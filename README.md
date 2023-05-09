# MicroPLC-Learning
The MicroPLC-Learning repo is a collection of resources, code, and documentation that has been accumulated during the process of learning and programming microcontrollers. This repository serves as a personal knowledge hub, gathering valuable materials to support the understanding and development of microcontroller programming skills. It contains a wide range of resources, starting from very simple examples suitable for beginners and gradually progressing to more complex projects
``` c
#include "TM1637.h"
#define CLK 16//pins definitions for TM1637 and can be changed to other ports
#define DIO 17
TM1637 tm1637(CLK,DIO);
int count=0;
const int SW0 = 32;
const int SW1 = 33;
int SW0_state=0;
int SW1_state=0;

void setup()
{
  pinMode(SW0,INPUT);
  pinMode(SW1,INPUT);
  tm1637.init();
  tm1637.set(BRIGHT_TYPICAL);//BRIGHT_TYPICAL = 2,BRIGHT_DARKEST = 0,BRIGHTEST = 7;
  tm1637.display(3,count);
}

void loop() {
  SW0_state = digitalRead(SW0);
  SW1_state = digitalRead(SW1);
  delay(200);
  
  if (SW0_state==HIGH) {
      count=0;
      tm1637.clearDisplay();
  }

  if (SW1_state==HIGH) {
      count = count + 1;    
  }
  if (count==0){
    tm1637.display(3,count);
  }else{
    tm1637.displayNum(count);
  }
    // put your main code here, to run repeatedly:

}
```
