# MPU6050_angle_readings
# Pitch and roll angles from a MPU6050 sensor and CF filter

### Diego Chavez - diegochav3z
### New Mexico State University
### email: saidcha@nmsu.edu - saidcharana@gmail.com 
### website: diegochav3z.com  
Jupyter notebook code to obtain pitch and roll angles using a MPU6050 intertial motion unit. The MPU6050 used for this code is a 6-DOF with 3 degrees dedicated to an accelerometer and the other 3 dedicated to a gyroscope. The output of the accelerometer is normalized to +/- 2 LSB/g, therefore its output is in (g). For the gyroscope its sensitivity 131LSB/degrees/second, therefore its output is in (degrees/s). The communication protocol used was I2C. 

All sensors come with noise this means that a filter is necessary to process the information and have clear data coming out of it. The forces actuating in the object is mainly provided by the accelerometer, however the accelerometer is very sensitive to small forces. This means that a 'low pass' filter needs to be used to counteract the disturbances. 
On the other hand the gyroscope provides the angular velocity, this one integrated gives a good measurement of the angular position. However due the nature of the integration, the data tends to drift away from the zero.

Here a complementary filter is implemented as follows:  
    >> The gyroscope values are integrated everytimestep to obtain an angle value. The accelerometer values are normalized vector values of the        gravitational force, this is why the atan2 function was used to obtain an angle value. 
    >> Gyroscope angle and accelerometer values are combined, where the accelerometer values complement the gyroscope values with a 0.02 to 0.98 distribution. So that the roll and pitch angles are given by: 
        >>> pitch/roll = Gyroscope_Angle*0.98 + Accelerometer_Angle*0.02
  
   

