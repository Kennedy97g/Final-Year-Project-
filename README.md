# Final-Year-Project-
Basic Experiments  Week 10
// Single Position Servo 6
#include <Servo.h>

Servo servo6;  // create servo object to control a servo


int pos = 0;    // variable to store the servo position

void setup() {
  servo6.attach(9);  // attaches the servo on pin 9 to the servo object
}

void loop() {
if (pos > 180){                      // If variable 'pos' is greater than 180 degrees then it is 
                                     // made equal to 180 becasue servo cant rotate more than 180 degrees
    servo6.write(180);              
   delay(15);                       // waits 15ms for the servo to reach the position
 } 
    servo6.write(pos);              // tell servo to go to position in variable 'pos' if it is less than 
                                    //180 degrees
   delay(15);  
 }
////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
// Flex Sensor Servo 6
#include <Servo.h> 
Servo servo6;

const int flexPin = A0; //pin A0 to read analog input

int flexposition6;      //set variable for positionof flex sensor posit
int servoposition6;     //set variable for positionof servo position

//Variables:
int value;               //save analog value

void setup() {
servo6.attach(9);        // attaches the servo on pin 9 to the servo object
Serial.begin(9600);      // set Baud rate to 9600 where it can be monitored using serial plotter/monitor
}

void loop() {

flexposition6=analogRead(flexPin);                   // read the analog value of flex pin input and make it equal to the flex position
servoposition6=map(flexposition6, 800,960,38,180);  // limiting the sensitivity of the flex sensor to only read values above 800 and below 960
servoposition6=constrain(servoposition6,38,180);    // limit the postion values so that they dont exceed the motor capabilities
servo6.write(servoposition6);                       // set servo 6 position to the value of servopositon6
 delay(100);                                        // 15ms time delay to smoothen running of robot
}
////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////
