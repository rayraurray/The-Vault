Data normalization is **the process of reorganizing data within a database so that users can utilize it for further queries and analysis**. Simply put, it is the process of developing clean data.

# Min-max Scaling
Data is scaled to a fixed range, usually 0 to 1.  
$$\Large
x_{\text{norm}}=\frac{x-x_{\text{min}}}{x_{\text{max}}-x_{\text{min}}}
$$
# Standardization
Data is rescaled to having properties of $\large \mu = 0$,  $\large \sigma = 1$  
$$\Large
x_{\text{norm}}=\frac{x-\mu}{\sigma}
$$