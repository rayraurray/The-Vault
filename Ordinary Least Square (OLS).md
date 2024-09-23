Given N number of data points (training set) =  
(𝑥1 , 𝑦1 ), (𝑥2 , 𝑦2 ),......, (𝑥𝑁 , 𝑦𝑁 )  
• Goal: To find a linear model (ℎ𝜃(𝑥) = 𝜃0 + 𝜃1𝑥) that best fit all the data.

![[SLR Example.png]]
# Cost Function
![[OLS Cost Function.png]]

Characteristic of least square cost function:  
- Least square is one of the convex optimization problems  
- The convex function have a single global minimum

![[Global Minimum.png]]

Method of least square directly computes the optimal choice of (𝜃0 , 𝜃1) at the global minimum, by taking the derivative.  
𝑎𝑟𝑔𝑚𝑖𝑛𝜃0 , 𝜃1 J(𝜃0 , 𝜃1)
# Normal Equation
[[Normal Equation]]