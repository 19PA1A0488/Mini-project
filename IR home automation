#include <LiquidCrystal.h>

#include <IRremote.h>

LiquidCrystal lcd(8,9,10,11,12,13);
#define bulb1 3
#define bulb2 4
#define bulb3 5

int RECV_PIN = 7;


int itsON[] = {1,1,1,1};

#define code1 16724175 
#define code2 16718055 
#define code3 16743045 

IRrecv irrecv(RECV_PIN); 
decode_results results;
void setup() 
{
irrecv.enableIRIn();
lcd.begin(16, 2);
Serial.begin(9600);
pinMode(bulb1, OUTPUT);
pinMode(bulb2, OUTPUT);
pinMode(bulb3, OUTPUT);
digitalWrite(bulb1, HIGH);
digitalWrite(bulb2, HIGH);
digitalWrite(bulb3, HIGH);
lcd.print("IR Controlled");
lcd.setCursor(0,1);
lcd.print("Home Automation");
delay(2000);
lcd.clear();
lcd.print("Batch 8");
lcd.setCursor(0,1);
delay(1000);
lcd.print("System Ready...");
delay(1000);
lcd.clear();
lcd.setCursor(0,0);
lcd.print("Fan   Light  TV ");
lcd.setCursor(0,1);
lcd.print("OFF    OFF   OFF");
}
void loop() {
lcd.setCursor(0,0);
lcd.print("Fan   Light  TV"); 
if (irrecv.decode(&results)) {
unsigned int value = results.value;
switch(value) {
case code1:
if(itsON[1] == 1) { 
digitalWrite(bulb1, LOW); 
itsON[1] = 0;
lcd.setCursor(0,1);
lcd.print("ON  ");
}
else { 
digitalWrite(bulb1, HIGH);
itsON[1] = 1;
lcd.setCursor(0,1); 
lcd.print("OFF ");
}
break; 
case code2:
if(itsON[2] == 1) {
digitalWrite(bulb2, LOW);
itsON[2] = 0;
lcd.setCursor(6,1); 
lcd.print("ON   "); 
} else {
digitalWrite(bulb2, HIGH);
itsON[2] = 1;
lcd.setCursor(6,1); 
lcd.print("OFF  ");
}
break;
case code3:
if(itsON[3] == 1) {
digitalWrite(bulb3, LOW);
itsON[3] = 0;
lcd.setCursor(13,1); 
lcd.print("ON ");
} else {
digitalWrite(bulb3, HIGH);
itsON[3] = 1;
lcd.setCursor(13,1); 
lcd.print("OFF");
}
break; 
}
Serial.println(value); // you can comment this line
irrecv.resume(); // Receive the next value
}
}
