Multitask learning is a slightly different flavor of the world of transfer learning.
By giving a set of learning tasks, $\large t_1 , t_2 , …, t_n$, the learner co-learn all tasks simultaneously.

In other words, the learner optimizes the learning/performance across all of the $\large n$ tasks through some shared knowledge.

In this case, the learner receives information on multiple tasks at once without distinguishing between the source and targets.

![[Multi-task Learning.png]]

# Generic Multi-task Learning
Case study: Plant disease identification

The generic multitask learning consists of two components: the shared layers and the specific layers. 
![[Generic MTl.png]]

# When it makes sense
Training on a set of tasks that could benefit from sharing lower-level features

For example: The features of the host species can help identify plant diseases. These features are the ones that pathologists use to infer associated diseases and to establish lists of diseases associated with host species.

Usually: Amount of data you have for each task is quite similar

Can train a large network of neurons to do all tasks well. The size of the neural network must be taken into consideration if one wants to train it to adapt to many tasks.

