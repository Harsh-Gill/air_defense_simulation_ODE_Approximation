# air_defense_simulation_ODE_Approximation

**Project Intro.**
This project is for designing and simulating an air-defense system capable of accurately targeting incoming planes. This will be done in 4 phases, building up from a simple system that needs guided input to a final one which is automatically capable of detecting the target plans motion parameters and sending out an appropriate response.  The simulation assumes a simplified model of air-resistance, and uses the runge-kutta method to estimate trajectories. It uses newtons iterative method to find optimal trajectories. The main limitation of this method is the simplification of air-resistance, neglecting plane-motion variability and missile

**Runge-Kutta Method**
More specifically , the methods used to obtain the trajectory shape was by using the Runge-Kutta method of the 4th Order , which can evaluate the differential equation of motion integral effectively. The Runge-Kutta method can take in a derivative of x and solve its integral by iterating over small steps and returning a value of the step multiplied by the derivative function to essentially solve the integral. We chose the 4th Order for this simulation as it is a relatively simple option (as higher order ones become increasingly complex ) but still gives accurate results up to the fifth power of the step.
![image](https://user-images.githubusercontent.com/70016426/130725776-f099295d-0140-4f15-900d-fecf661e2133.png)

**Newtons Method**
Then to find the optimum trajectory to strike the plane , we transformed the trajectory into a root-finding problem by expressing it as a difference between the position of the plane at time t and position of the missle at time t. Then we expressed a vector function F as the difference between these values and set the difference to 0. Following that, we taylor expand the values and disregard the higher order terms.  After , we invert the terms to express the velocity in terms of the partial derivatives. Then we use the newtons method to iteratively find the roots answers and thus the optimal speed to hit the plane in a specific time t. 

![image](https://user-images.githubusercontent.com/70016426/130726478-20a99e2a-c6af-41ff-9b4b-fc1bde603266.png)


# System Simulation 

![alt-text](https://github.com/Harsh-Gill/air_defense_simulation_ODE_Approximation/blob/main/animations/animation.gif)


**The system is now detecting the planes position every 0.1 second , starting for t=0

**Plane first seen at t=0 at [5000, -5000, 7000]
**Plane then seen at t=0.1 at [4995.02, -4994.98, 7000.02]
**Plane then seen at t=0.2 at [4990.08, -4989.92, 7000.08]

**Using the 3 detected positions stated above The planes paramters of motions are
**At the intial t = 0 With pos. x: 5000 y: -5000 z: 7000
**The intial speed was x: -49.999999999990905 y: 50.000000000009095 z: 9.094974773304898e-12
**The acceleration is x: 3.9999999999054117 y: 3.9999999999054117 z: 3.9999999999054117

**For the missile to strike the plane at: 32 sec
**It must be fired at Speed in X-direc. : 17.801502639133254 Speed in Y-direc. : -4.4177003614652826 Speed in Z-direc. : 82.53753639900316
**position of plane at: 32 sec
**5447.999999951862 -1352.0000000481382 9047.999999951862

**position of missile at 32 sec
**5448.000000064015 -1352.0000000807424 9047.999999895728 32 sec

