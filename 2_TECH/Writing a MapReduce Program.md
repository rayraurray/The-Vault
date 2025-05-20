[[MapReduce]]
[[Hadoop]]

---
# Components

**[[MapReduce]]** is a programming model used for processing large data sets across distributed clusters.

Hadoop's MapReduce programs are composed of three parts:
- **Driver**: Configures and submits the job to the cluster (runs on the client to configure and submit the job.).        
- **Mapper**: Processes input and emits intermediate key-value pairs (generates the word and count pairs).
- **Reducer**: Aggregates the intermediate pairs to produce the final output (accumulates the counts for every word).

---
# Execution Flow

![[Pasted image 20250519111307.png]]

The data passed to the Mapper is specified by an InputFormat (*specified in the driver code*). We then define the location of the input data (typically, *a file or a directory*) and determine how to split the input data into input splits (each mapper deals with a single input split). ***RecordReader object*** is then created for parsing the input data into key-value pairs to pass to the Mapper.

**Execution Flow:**
- Input files are split into chunks (InputSplits).
- Each InputSplit is processed by a **RecordReader**.
- Data is passed to **Mapper** instances.
- Output of Mappers is **shuffled and sorted** before reaching **Reducers**.
- **Combiners** can be optionally used for local aggregation to improve performance.

---
# Handling Input and Output
*The Key is **InputFormat***

Defines how data is split and passed to the Mapper.

Default is **TextInputFormat**, which:
- Uses `LineRecordReader`
- Emits key-value pairs: **key = byte offset**, **value = line content**
- It treats each \n –terminated line of a file as a value.

**Example:** 
![[Pasted image 20250519112811.png]]
*input*

```arduino
0  → "Tale as old as time..." 
39 → "Barely even friends..."
```
*output*

**Other Input Formats:**
- **FileInputFormat**: Abstract base class used for all file-based inputFormats.
- **KeyValueTextInputFormat**: Parses lines into key-value pairs using a *key **separator** value*. By default it's *Tab*.
- **SequenceFileInputFormat**: For binary key-value data with some additional metadata.
- **SequenceFileAsTextInputFormat**: Converts binary **key-value** pairs into **strings**.

**Key and Values are Objects:**
- **Keys and values** in Hadoop **are not primitive** but ***Java Objects***.
- *Keys* are objects which implement **WritableComparable**.
- *Values* are objects which implement **Writable**.

*that brings us to our next part*

---
# Writable and WritableComparable

Hadoop uses special wrapper classes for serialization.
**Must implement:**
- **Writable** (for values)
- **WritableComparable** (for keys – needed for sorting)

## 1. Writable
The writable interface makes serialization quick and easy for Hadoop. *Any value’s type **must implement*** the Writable interface. 

Hadoop defines its own *box classes* for strings, integers, and so on.
- IntWritable for integers
- LongWritable for longs
- FloatWritable for floats
- DoubleWritable for dobules
- Text for strings
- *etc.*

## 2. WritableComparable
A ***WritableComparable*** is a **Writable** which is also *Comparable*. Two WritableComarables can be *compared against each other* to determine their order.

**Keys** must be WritableComparables because they are **passed to the Reducer** in *sorted order*. Despite their names, **all Hadoop box classes implement both Writable and WritableComparable**.

For instance, **IntWritable** is actually a ***WritableComparable***.

---
# Writing the Code
Throughout the process we must ensure that *data types are consistent across **driver**, **mapper**, and **reducer**.*
## 1. Driver Code
Runs on the ***client side***.

**Configures:**
- InputFormat
- OutputFormat
- Mapper & Reducer classes
- Input/output paths        
Creates and submits a `Job` object to **the cluster**. 

**Execution options:**
- `job.waitForCompletion(true)` – blocks until job finishes.
- `job.submit()` – submits job without blocking.

**Example Code:**
```java
package stubs;

import org.apache.hadoop.fs.Path;
import org.apache.hadoop.io.IntWritable;
import org.apache.hadoop.io.Text;
import org.apache.hadoop.mapreduce.lib.input.FileInputFormat;
import org.apache.hadoop.mapreduce.lib.output.FileOutputFormat;
import org.apache.hadoop.mapreduce.Job;

public class WordCount {
    public static void main(String[] args) throws Exception {
        if (args.length != 2) {
            System.out.printf("Usage: WordCount <input dir> <output dir>\n");
            System.exit(-1);
        }

        Job job = new Job();
        job.setJarByClass(WordCount.class);
        job.setJobName("Word Count");

        FileInputFormat.setInputPaths(job, new Path(args[0]));
        FileOutputFormat.setOutputPath(job, new Path(args[1]));

        job.setMapperClass(WordMapper.class);
        job.setReducerClass(SumReducer.class);
        job.setOutputKeyClass(Text.class);
        job.setOutputValueClass(IntWritable.class);

        boolean success = job.waitForCompletion(true);
        System.exit(success ? 0 : 1);
    }
}

```

**The Job Object:**
- The job class allows you to set configuration options for your MapReduce job.
- Any options not explicitly set in your driver code or specified in your configuration will be read from your Hadoop configuration files.
- Usually located in */etc/hadoop/conf*.
- You can also use the Job object to submit the job, control its execution, and query its state.

**Specifying the InputFormat:**
- The default InputFormat (TextInputFormat) will be used unless you specify otherwise.
- To use an InputFormat other than the default, use the following command: `job.setInputFormatClass(KeyValueTextInputFormat.class)`

**InputFormat:**
- By default, `FileInputFormat.setInputPaths()` will read all files from a specified directory and send them to Mappers.
- Exceptions: items with the name beginning with **a period** or **underscore**.  
- Alternatively, `FileInputFormat.addInputPath()` can be used multiple times, specifying a single file/directory each time

**OutputFormat:**
- `FileOutputFormat.setOutputPath()` specifies the directory to which the Reducers will write their final output.
- The driver can also specify the format of the output data.
- Default is a plain text file.
- Could be explicitly written as: `job.setOutputFormatClass(TextOutputFormat.class)`

**`waitForCompletion()` vs `Submit()`:**
- There are two ways to run your MapReduce job: `job.waitForCompletetion()` or `job.submit()`
- The client determines the proper division of input data into InputSplits, and then sends the job information to the JobTracker daemon on the cluster.

- ## 2. Mapper

- `map(key, value, context)`
- Processes input key-value pairs.
- Emits intermediate key-value pairs using `context.write()`.

**Example Code:**
```java
package stubs;

import java.io.IOException;

import org.apache.hadoop.io.IntWritable;
import org.apache.hadoop.io.LongWritable;
import org.apache.hadoop.io.Text;
import org.apache.hadoop.mapreduce.Mapper;

public class WordMapper extends Mapper<LongWritable, Text, Text, IntWritable> {
    @Override
    public void map(LongWritable key, Text value, Context context)
            throws IOException, InterruptedException {

        String line = value.toString();

        for (String word : line.split("\\W+")) {
            if (word.length() > 0) {
                context.write(new Text(word), new IntWritable(1));
            }
        }
    }
}
```
## 3. Reducer

- `reduce(key, values, context)`
- Accepts each key and an iterable of all associated values.
- Aggregates and emits final results via `context.write()`.

```java
public class SumReducer extends Reducer<Text, IntWritable, Text, IntWritable> {
    @Override
    public void reduce(Text key, Iterable<IntWritable> values, Context context)
            throws IOException, InterruptedException {

        int wordCount = 0;

        for (IntWritable value : values) {
            wordCount += value.get();
        }

        context.write(key, new IntWritable(wordCount));
    }
}
```

---
# Streaming API
Many organizations have developers skilled in languages other than Java. (ex: C++, C#, Ruby, Python, Perl, etc.)

The streaming API allows developers **to use any language they wish to write Mappers and Reducers**. As long as *the language can read from standard input and write to standard output*.

Although **Mappers and Reducers** *can be written using the Streaming API*, **Partitioners**, **InputFormats**, etc. ***must still be written in Java***.

| Advantages                             | Disadvantages                                                                           |
| -------------------------------------- | --------------------------------------------------------------------------------------- |
| No need to learn Java                  | Performance                                                                             |
| Faster Development Time                | Suited for handling text data                                                           |
| Ability to use existing code libraries | Streaming jobs can use excessive amounts of RAM or fork excessive numbers of processes. |

**To implement Streaming:**
- Write separate Mapper and Reducer programs in the language(s) of your choice.
- They will receive input via **stdin**.
- They should write their output to **stdout**. If TextInputFormat (the default) is used, the streaming Mapper just receives each line from the file on **stdin**.
- No key is passed. Mapper and Reducer output should be sent to stdout as:  Key `tab` value `newline`
- Separators other than tab can be specified.

