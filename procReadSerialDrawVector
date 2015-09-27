import processing.serial.*;

Serial myPort;  // Create object from Serial class
int lf = 10;    //Line feed
String myString = null;
String[] list;
int errors = 0;

import remixlab.proscene.*;
Scene scene;
//Choose one of P3D for a 3D scene, or P2D or JAVA2D for a 2D scene
String renderer = P3D;


void setup() 
{
	size(1200, 800, renderer); 
	scene = new Scene(this);
	// when damping friction = 0 -> spin
	scene.eye().frame().setDampingFriction(0);
  
	String portName = Serial.list()[0];
	myPort = new Serial(this, portName, 115200);
	frameRate(5);
	background(0);
	delay(3000);
}

void draw()
{
  background(0);
  while (myPort.available() > 0) {
    myString = myPort.readStringUntil(lf);
    if (myString != null) {
      myString = trim(myString);
      list = split(myString, ',');
      if ((list.length != 9) || Float.isNaN(float(list[0])) || Float.isNaN(float(list[1])) || Float.isNaN(float(list[2])) || Float.isNaN(float(list[3])) || Float.isNaN(float(list[4])) || Float.isNaN(float(list[5])) || Float.isNaN(float(list[6])) || Float.isNaN(float(list[7])) || Float.isNaN(float(list[8]))) {
        println(millis() + ": Input are not floats");
        //println(float(list[0]), float(list[1]), float(list[2]), float(list[3]), float(list[4]), float(list[5]), float(list[6]), float(list[7]), float(list[8]));
        errors++;
      }
      else {
        println(list[0], list[1], list[2], list[3], list[4], list[5], list[6], list[7], list[8]);
        
        // ***** Draw Acceleration Vector *****
        strokeWeight(5);
        stroke(color(0, 0, 255));
        line(0, 0, 0, float(list[0]), float(list[1]), float(list[2]));
        
        // ***** Draw Heading Vector *****
        strokeWeight(1);
        stroke(color(255, 0, 0));
        line(0, 0, 0, float(list[3]), float(list[4]), float(list[5]));
        strokeWeight(5);
        line(0, 0, float(list[3]), float(list[4]));
        
        // ***** Draw Rate Gyro Vector *****
        strokeWeight(5);
        stroke(color(0, 255, 0));
        line(0, 0, 0, float(list[6]), float(list[7]), float(list[8]));
        /*
        print(list[0]);
        print(",");
        print(list[1]);
        print(",");
        print(list[2]);
        print(",");
        print(list[3]);
        print(",");
        print(list[4]);
        print(",");
        print(list[5]);
        print(",");
        print(list[6]);
        print(",");
        print(list[7]);
        print(",");
        println(list[8]);*/
      }
    }
  }
  

}
