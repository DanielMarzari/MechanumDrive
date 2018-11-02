# MechanumDrive
Controller input to motor group output

Java


@author Daniel Marzari 
 
 getMechanumCoordinate(Coordinate point) - takes in a coordinate on the unit circle and converts it into the  
                                           motor group powers(two groups) in coordinate form on the unit circle.
 
        1/        \M
       G/          \G
      M/            \2
        
 
 
      M\            /1
       G\          /G
        2\        /M
 
  
      The parallel diagonal wheels allow the robot/car to strife. The following table shows 
      the input values and their desired corresponding output for the motor powers.

      INPUT              (DESIRED) OUTPUT
      (0, 1)               (PI/4, PI/4)
      (1, 0)               (-PI/4, PI/4)
      (0, -1)              (-PI/4, -PI/4)
      (-1 ,0)              (PI/4, -PI/4)

      If you plot these output coordinates compared to the input coordinates you see that each point is flipped over 
      the Y-axis and then is shifted counterclockwise 45 degrees (PI/4 radians). Therefore we get the following equation: 
 
      newTheta = (90 - oldTheta) + 90         OR          newTheta = (PI/2 - oldTheta) + PI/2
      
      This maps 60 degrees to 120 degrees                 This maps PI/3 radians to 2PI/3 radians
      This maps 210 degrees to -30 degrees                This maps 4PI/3 radians to -PI/3 radians
 
      finalTheta = newTheta - 45
 
      We can combine these equations and get the following:
 
      finalTheta = 90 - oldTheta + 90 - 45    OR          finalTheta = PI/2 - oldTheta + PI/2 - PI/4
      finalTheta = 135 - oldTheta                         finalTheta = 3PI/4 - oldTheta
 
     
      Now that we have the angle finalTheta, we can find the x and y coordinates (of the output unit circle) 
      by using the sin and cos functions. 
 
      y = sin(135 - theta)                OR              y = sin(3PI/4 - theta) 
      x = cos(135 - theta)                                x = cos(3PI/4 - theta) 
      

