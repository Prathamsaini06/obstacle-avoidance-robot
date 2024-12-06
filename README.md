# obstacle-avoidance-robot
// this code is for obstacle avoiding robot
//
#include<liquidcrystal.h>
liquidcrystal lcd(8, 9, 10, 11, 12, 13);

long cm, duration;
const int echopin = 7;
const int echopin = 6;

const int lm1 = 2;
const int lm1 = 3;
const int lm1 = 4;
const int lm1 = 5;

// Aabove is the motor driver pin connection.

void setup()
{
  pinMode(lm1, OUTPUT);
  pinMode(lm2, OUTPUT);
  pinMode(lm1, OUTPUT);
  pinMode(lm2, OUTPUT);
  
  pinMode(trigPin, OUTPUT);
  pinMode(echoPin, INPUT);
  
  Serial.begin(9600);
  lcd.begin(16,2);
}

void loop()
{ 
  
  // the distance ahead using an ultrasonic sensor
  digitalWrite(trigPin, LOW);
  delayMicroseconds(2);
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(5);
  digitalWrite(trigPin, LOW);
  duration = pulseIn(echoPin, HIGH);
// converting the time into a distance in centimeter
  
  cm = duration*0.34/2;
  
  if(cm<20)
  {
    stop_bot();
    delay(2000);
    
    go_back();
    delay(2000);
    
    stop again();
    delay(1000);
    
    go_left();
    delay(1000);
  }
  
  else
  {
    go_straight();
    delay(1000);
  }
  
// For serial monitor
  Serial.print("Distance: CM");
  Serial.println(cm);
  
}

// Here are the functions that are used in the program

void go_straight()
{
  lcd.setCursor(0,0);
  lcd.print("NOTHING AHEAD");
  lcd.setCursor(0,1);
  lcd.print("MOVING FORWORD");
  
    digitalWrite(lm1,HIGH);
    digitalWrite(lm2,lOW);                                                                          
    digitalWrite(rm1,HIGH);
    digitalWrite(rm2,lOW);
}
void go_back()
{
  lcd.clear();
  lcd.setCursor(0,0);
  lcd.print("TAKING REVERSE");
  lcd.setCursor(0,1);
  lcd.print(cm);
  
    digitalWrite(lm1,HIGH);
    digitalWrite(lm2,lOW);                                                                          
    digitalWrite(rm1,HIGH);
    digitalWrite(rm2,lOW);
}
void stop_bot()
{
  lcd.clear();
  lcd.setCursor(0,0);
  lcd.print("SOMTHING AHEAD");
  Lcd.print("STOP");
  
    digitalWrite(lm1,LOW);
    digitalWrite(lm2,lOW);                                                                          
    digitalWrite(rm1,LOW);
    digitalWrite(rm2,lOW);
}
void stop_again()
{
  lcd.clear();
  lcd.setCursor(0,0);
  lcd.print("BREAK FOR TURN");
  
    digitalWrite(lm1,LOW);
    digitalWrite(lm2,lOW);                                                                          
    digitalWrite(rm1,LOW);
    digitalWrite(rm2,lOW);
}

void go_left()
{
  lcd.clear();
  lcd.setCursor(0,0);
  lcd.print("TURNING LEFT");
  
    digitalWrite(lm1,LOW);
    digitalWrite(lm2,lOW);                                                                          
    digitalWrite(rm1,HIGH);
    digitalWrite(rm2,lOW);
}
  
void go_right()
{
  lcd.clear();
  lcd.setCursor(0,0);
  lcd.print("TURNING RIGHT");
  lcd.setCursor(0,1);
  lcd.print(cm);
  
    digitalWrite(lm1,HIGH);
    digitalWrite(lm2,lOW);                                                                          
    digitalWrite(rm1,LOW);
    digitalWrite(rm2,lOW);
}
  
