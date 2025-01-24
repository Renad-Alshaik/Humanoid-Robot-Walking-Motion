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

Step 4: Maintain Balance
- Real-Time Sensor Feedback:
Continuously monitor gyroscope and accelerometer data for stability.
Adjust joint angles dynamically to counteract any imbalance.
- Ground Reaction Forces:
Use foot pressure sensors to ensure equal weight distribution during stance.
- Adjust Trajectory:
If sensors detect instability, modify the swing leg trajectory or CoM shift

Step 5: Handle Turning and Stopping
- Turning:
Adjust the step direction by modifying the swing leg trajectory.
Ensure the CoM shift compensates for the change in direction.
- Stopping:
Gradually reduce the stride length and step height.
Bring both feet back to a balanced standing position.

Step 6: Error Handling
- Monitor Stability:
If the robot tilts beyond a threshold, stop the motion and reposition the legs for balance.
- Fall Detection:
Detect a fall using accelerometer data and initiate a recovery mechanism.

Step 7: Iteration
- Loop:
Continue the walking cycle until a stop command is issued.
Periodically update gait parameters based on terrain feedback (e.g., incline, uneven surface)
