# Humanoid-Robot-Walking-Motion
algorithm for how the walking motion will be executed in the humanoid robot.
# Steps :

Step 1: Initialization
Configure the parameters:
Specify the walking speed, step height, stride length, and step size.
Establish the starting joint angles for a standing position that is balanced.
Sensor calibration:
Set the gyroscope, accelerometer, and other sensors to zero.
Make sure the robot is standing up straight.
Turn on the Balancing System: To keep your balance when walking, turn on PID controllers.

Step 2: Plan Walking Gait 
- Define Gait Cycle .. A full gait cycle consists of two phases:
   Swing Phase: The leg moves forward.
   Stance Phase: The leg supports the body.
- Precompute Trajectories:
  Determine the joint angles for every phase using inverse kinematics.
  Create smooth transitions for the swing leg, using a trajectory generator (e.g., cubic or quintic polynomials).

Step 3: Execute Walking Cycle
- initialize Stance:
Start with the robot’s weight evenly distributed between both feet.
- Shift Center of Mass (CoM):
Slightly shift the robot’s CoM towards the stance leg to prevent falling.
Use the gyroscope and accelerometer to adjust the shift dynamically.
- Lift Swing Leg:
Gradually increase the joint angles to lift the swing leg off the ground.
Raise the swing foot to the pre-defined step height.
- Move Swing Leg Forward:
Move the swing leg forward using the planned trajectory.
- Place Swing Leg Down:
Lower the swing foot to the ground, ensuring contact is made with the sole sensors.
- Repeat for the Other Leg:
Shift the CoM to the newly planted foot and repeat the cycle.
