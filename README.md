# WRO-Sewage-Cleaner-robot
# Report
- [PROJECT REPORT](https://docs.google.com/document/d/1S0MSvquXofWw6It9QTXSThzVdBmhXdr8IRROb4kRJek/edit#heading=h.uwtpzkmp9874)
# Video
- [Video](https://youtu.be/He5vBDilmNc?si=IJNBha5A0QitPSHe)
# Robot
- [Robot](https://github.com/user-attachments/assets/f9f58a4c-317c-496e-b789-b8ddb21c3b52)
- [code] (#define CUSTOM_SETTINGS
#define INCLUDE_GAMEPAD_MODULE
#include <Dabble.h>

//Right motor
int enableRightMotor=5; 
int rightMotorPin1=7;
int rightMotorPin2=8;

//Left motor
int enableLeftMotor=6;
int leftMotorPin1=9;
int leftMotorPin2=10;

void setup()
{
  // put your setup code here, to run once:
  pinMode(enableRightMotor,OUTPUT);
  pinMode(rightMotorPin1,OUTPUT);
  pinMode(rightMotorPin2,OUTPUT);
  
  pinMode(enableLeftMotor,OUTPUT);
  pinMode(leftMotorPin1,OUTPUT);
  pinMode(leftMotorPin2,OUTPUT);

  rotateMotor(0,0);   
    
  Dabble.begin(9600, 2, 3);
}



void loop()
{
  int rightMotorSpeed=0;
  int leftMotorSpeed=0;
  Dabble.processInput();
  if (GamePad.isUpPressed())
  {
    rightMotorSpeed = 255;
    leftMotorSpeed = 255;
  }

  if (GamePad.isDownPressed())
  {
    rightMotorSpeed = -255;
    leftMotorSpeed = -255;
  }

  if (GamePad.isLeftPressed())
  {
    rightMotorSpeed = 255;
    leftMotorSpeed = 0;
  }

  if (GamePad.isRightPressed())
  {
    rightMotorSpeed = 0;
    leftMotorSpeed = 255;
  }

  rotateMotor(rightMotorSpeed, leftMotorSpeed);
}

void rotateMotor(int rightMotorSpeed, int leftMotorSpeed)
{
  if (rightMotorSpeed < 0)
  {
    digitalWrite(rightMotorPin1,LOW);
    digitalWrite(rightMotorPin2,HIGH);    
  }
  else if (rightMotorSpeed >= 0)
  {
    digitalWrite(rightMotorPin1,HIGH);
    digitalWrite(rightMotorPin2,LOW);      
  }

  if (leftMotorSpeed < 0)
  {
    digitalWrite(leftMotorPin1,LOW);
    digitalWrite(leftMotorPin2,HIGH);    
  }
  else if (leftMotorSpeed >= 0)
  {
    digitalWrite(leftMotorPin1,HIGH);
    digitalWrite(leftMotorPin2,LOW);      
  }

  analogWrite(enableRightMotor, abs(rightMotorSpeed));
  analogWrite(enableLeftMotor, abs(leftMotorSpeed));    
})
