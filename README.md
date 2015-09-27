# procReadSerialDrawVector
Reads serial input and displays on 3D proscene graph

Simple tool for taking a CSV serial input and turning the input into 3D graphical vectors drawn in the Processing Java applet.  The app currently takes three (3) x three (3) terms in the line.  

The input must look like this: 
-0.35,-0.35,10.79,21.55,26.64,-54.59,-0.12,0.31,0.10

In the future, I'll make it so that it's agnostic to serial input and will simply draw vectors based on what is fed in.  This output is the output from a 10DOF Adafruit IMU breakout (minus the barometric pressure).
