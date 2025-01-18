# IOT-project
IOT SMART ROBOT CAR USING BLUETOOTH 
#include <SoftwareSerial.h>
SoftwareSerial serial(8, 9); // 8=Rx, 9=Tx

#define m1  2 // Left motor
#define m2  3 // Left motor
#define m3  4 // Right motor
#define m4  5 // Right motor

void setup() {
  serial.begin(9600);
  serial.println("SERVING ROBOT");
  serial.println("1 - FORWARD");
  serial.println("2 - BACKWARD");
  serial.println("3 - LEFT");
  serial.println("4 - RIGHT");
  serial.println("5 - STOP");
  serial.println();
  
  pinMode(m1, OUTPUT);
  pinMode(m2, OUTPUT);
  pinMode(m3, OUTPUT);
  pinMode(m4, OUTPUT);
}

void loop() {
  if (serial.available() > 0) {
    char data = serial.read();
    delay(10); // Debouncing delay
    
    if (data == '1') {
      forward();
    } else if (data == '2') {
      backward();
    } else if (data == '3') {
      left();
    } else if (data == '4') {
      right();
    } else if (data == '5') {
      stop();
    }
  }
}

void forward() {
  digitalWrite(m1, HIGH);
  digitalWrite(m2, LOW);
  digitalWrite(m3, HIGH);
  digitalWrite(m4, LOW);
}

void backward() {
  digitalWrite(m1, LOW);
  digitalWrite(m2, HIGH);
  digitalWrite(m3, LOW);
  digitalWrite(m4, HIGH);
}

void left() {
  digitalWrite(m1, LOW);
  digitalWrite(m2, HIGH);
  digitalWrite(m3, HIGH);
  digitalWrite(m4, LOW);
}

void right() {
  digitalWrite(m1, HIGH);
  digitalWrite(m2, LOW);
  digitalWrite(m3, LOW);
  digitalWrite(m4, HIGH);
}

void stop() {
  digitalWrite(m1, LOW);
  digitalWrite(m2, LOW);
  digitalWrite(m3, LOW);
  digitalWrite(m4, LOW);
}
