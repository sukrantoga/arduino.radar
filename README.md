#include <Servo.h>
Servo servo1;
#define trig 9
#define echo 10
int mesafe;
int sure;
int yesil = 6;
int kirmizi = 7;



void setup() {
  Serial.begin(9600);
  servo1.attach(3);
  pinMode(trig,OUTPUT);
  pinMode(echo,INPUT);
  pinMode(yesil,OUTPUT);
  pinMode(kirmizi,OUTPUT);

}

void loop() {
  for (int i=0; i<180;i++){
    servo1.write(i);
    if (mes  () < 10){
      digitalWrite (kirmizi,HIGH);
       digitalWrite (yesil,LOW);
    } else { 
      digitalWrite (yesil,HIGH);
       digitalWrite (kirmizi,LOW);
    }
    delay(20);

  }
  for (int i=180; i>-1;i--){
    servo1.write(i);
    if (mes () < 10){
      digitalWrite (kirmizi,HIGH);
       digitalWrite (yesil,LOW);
    } else { 
      digitalWrite (yesil,HIGH);
       digitalWrite (kirmizi,LOW);
    }
    delay(20);

  }

}

int mes(){
  digitalWrite(trig,LOW);
  delayMicroseconds(2);
  digitalWrite(trig,HIGH);
  delayMicroseconds(10);
  digitalWrite(trig,LOW);
  sure = pulseIn(echo,HIGH);
  mesafe = (sure/2)/29.1;
  return mesafe;
}





