# sensor-characterization-with-arduino-uno-
Using Ultrasonic and IR to calculate the distance and characterize 
## Led Test with Arduino 
Code for ledtest, I tested three led lights with the Arduino  
```
const int LED1 = 13;
const int LED2 = 12;
const int LED3 = 8;

void setup() {
pinMode(LED1, OUTPUT);
pinMode(LED2, OUTPUT);
pinMode(LED3, OUTPUT);
Serial.begin(9600);
}

void loop() {
digitalWrite(LED1, HIGH);
delay(1000);
digitalWrite(LED1, LOW);
delay(100);
digitalWrite(LED2, HIGH);
delay(1000);
digitalWrite(LED2, LOW);
delay(100);
digitalWrite(LED3, HIGH);
delay(1000);
digitalWrite(LED3, LOW);
delay(100);
}
```
