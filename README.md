# Brushless-motor-
How Brushless motor works?
Controlling brushless motor with Arduino;

التحكم بموتور برشليس بالاردوينو:
القطع التي نحتاجها:
١- أردوينو و بريد بورد
٢- مفرق الجهد potentiometer
٣- أسلاك (جنابر) jumbers
٤- موتور برشليس  brushless
٥- متحكم سرعة الكتروني : electronic speed controller : ESC
٦- بطارية 

إنشاء دائرة الكترونية: 
١- نقوم بإيصال مفرق الجهد ( potentiometer ) بـ 5V and  Ground 
٢- إيصال مخرجات مفرق الجهد  ( potentiometer ) بـ A0
٣- ايصال سلك الاشارة ( signal wire ) الخاص بمتحكم السرعة الإلكتروني ESC بالمنفذ ٣ ( pin 3 )
٤- إيصال السلك الأسود الخاص بمتحكم السرعة ESC بالأرضي (ground ) في الاردوينو
٥- أخيراً إيصال الدائرة بالبطارية.







كود برمجة الاردوينو:
The sketch of brushless motor works as same as servo motor! 


/*
Controlling a Brushless Motor with Arduino
 Brandon Tsuge

 This is an example that demonstrates how to read values from a potentiometer, or sensor and map them to a servo output to control
https://www.theboredrobot.com/post/controlling-a-brushless-motor-with-arduino
 
 */


//include the servo library
#include <Servo.h>

//define the pins for the sensor input.
#define SensorPin A0
#define MotorPin 3

Servo Motor1;

//initialize variables
int Speed = 0;
int SensorVal = 0;


void setup() {
  Motor1.attach(MotorPin); //attach the servo to the pin
  Serial.begin(9600);
}

void loop() {
  //read the potentiometer, map to 0-180, write it to the motor using the servo commands
  SensorVal = analogRead(SensorPin);
  Speed = map(SensorVal, 0, 1023, 0, 180);
  Motor1.write(Speed);

  Serial.println(Speed);

  
}

 
