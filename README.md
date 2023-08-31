# MPC 

This is a Readme file for the Project under Professor Amit Setia. 
The title for the project is Model Predictive Control in Robotics.

By using Model Predictive Control one can accurately predict the next most optimised step to take in order to reach your destination faster. 
This is done by predicting from a large number of predictions based on our control horizon and choosing the first most optimised prediction and following the same
for the other predictions. 

This concept is currently being used in chemical plants , with a large number of applications in autonomous vehicals , obstacle avoidance etc.

# Results

![image](https://user-images.githubusercontent.com/94890363/204078094-972ae6ae-9683-4c65-b6b0-8c51960628e3.png)
 

This is a graphical illustration of the model that the most basic MPC controller gave us 

We had two start states , x0 = 10 and X1= 5 and our goal was to bring them to the origin as fast and in the most optimised way as possible.
We had our own set of control inputs which were predefined and our model worked past them by optimising the result till the end which can be seen in the figure.
More about this can be read in the Uploaded PDF. 

# Multivariable Linear MPC

![image](https://user-images.githubusercontent.com/94890363/204093927-9c9df760-823d-4871-b293-52371e5130e4.png)

This is a graphical illustration of the 3 state model of the same Linear MPC controller. 
Here we have 3 state variables namely , x0=10 , x1=5 , x2=2 . 
These all start at the given initial points and try to converge towards the origin( which is our target destination) following the control parameters defined by u.

# Reducing Online Computation 

* The online computation for the above problem takes a lot of time.
* Firstly, the model has to calcuate the k+1 predictions of the n state variables , and the k predictions of the m control variables. 
* This brings the trivial computation time to **n(N+1) + m(N)**. 
* To execute this properly CPU with large computation power and higher clock speed are required. 
* This in turn makes the entire MPC controller costly.  
* Therefore there is a need to reduce the online computation of the MPC controller.

## We can do that in 2 ways :- 

### 1. By reducing the number of variables in the final equation by removing Xk. 
  * This will reduce the computation and will bring the overall computation time to **mN** as we got rid of the state variable Xk
  * The reduction is given below :-
  
   ![image](https://user-images.githubusercontent.com/94890363/205126679-a1f3429c-87db-40df-a86e-ef47405c8031.png)
   
### 2. By optimising the number of control variables by using a horizon which is lesser than the control horizon.
  * Now the total cost of computation will reduce to m*(NC) , NC being our new control horizon ( smaller than N) 
  * This is method is added to the previous method which in turn give us the most time efficient solution.
  * Nc is usually chosen as 2. 


 

# APPLICATIONS OF LINEAR MPC 

![8f436a6807c1824dfbd8ef954e1a4005](https://user-images.githubusercontent.com/94890363/204094907-5eafb1c0-9e88-4ad0-8577-8af0c207693f.gif)



* Let us image a case of a mars rover and consider a nominal 2d direction of motion. 
* Let us imagine that the motion of the rover is in 2d and the rover is falling with some initial velocity 
* This meand that the MPC controller has to put a great amount of thrust in the start and then the amount of thrust should reduce with time.
* This could be done with the above two given models.
* The origin would be the y=0 point and our initial point would be defined by the state parameters.
* The rover would have a velocity which would be defined as vcosΘ and vsinΘ. The MPC controller will try to optimise the thrust by providing the most optimal thrust to our problem.

# Learning- Based MPC 

* This is a different section of MPC, where the model learns based on the repetitive execution of the code. 
* The constraints are pre-feeded to the model. The model then performs MPC optimisations on the datasets once , then it optimises the datasets even more as the laps go on. 
* There is an entire team dedicated to make this possible in racing. 
* Their video can be found here - https://youtu.be/aCDPwZZm9C4

# Final Simulation on Turlebot3:-


https://user-images.githubusercontent.com/94890363/219039530-28044044-cdd4-4127-977a-ec8852df5f7b.mp4



