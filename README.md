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
## Ultrasonic sensor with arduino 
Testing the distance with the ultrasonic sensor to calculate the distance.
datasheet for the ultrasonic sensor
[HC-SR04.pdf](https://github.com/barbart/sensor-characterization-with-arduino-uno-/files/8833388/HC-SR04.pdf)
 

code for the ultrasonic sensor 
```
const int trigPin = 13;
const int echoPin = 8;
const int led = 12;    // I will use one of the 2 LEDs only
//const int led1 = 7;

float duration; // variable for the duration of sound wave travel
int distance; // variable for the distance measurement
int oldistance = 0;
int count = 0;
int sum = 0;

void setup() {
  pinMode(trigPin, OUTPUT); // Sets the trigPin as an OUTPUT
  pinMode(echoPin, INPUT); // Sets the echoPin as an INPUT
  pinMode(led, OUTPUT); // Sets the led as OUTPUT
//  pinMode(led1, OUTPUT); // Sets the led as OUTPUT
  Serial.begin(9600);
  Serial.println("Ultrasonic Sensor HC-SR04 Test"); // print some text in Serial Monitor
}
void loop() {
  digitalWrite(led, HIGH);
  digitalWrite(trigPin, LOW);
  delayMicroseconds(5);
  digitalWrite(trigPin, HIGH);
  delayMicroseconds(10);
  digitalWrite(trigPin, LOW);

  //  digitalWrite(led, HIGH);
  //  delay(10);
  //  digitalWrite(led, LOW);
  //  delay(100);
  //  digitalWrite(led1, HIGH);
  //  delay(15);
  //  digitalWrite(led1, LOW);
  //  delay(100);

  duration = pulseIn(echoPin, HIGH);
  distance = duration * 0.034 / 2; // Calculating the distance and Speed of sound wave divided by 2
  if (oldistance != distance) {
    oldistance = distance;
    // Displays the distance on the Serial Monitor
    Serial.print("Distance: ");
    Serial.print(distance);
    Serial.println("cm");
  }
  if (count < 100) {
    sum += distance;
    count ++;
  } else {
    Serial.println(sum / 100);
    digitalWrite(led, LOW);
    // wait for 2 seconds
    delay(4000);
    count = 0;
    sum = 0;
  }
}
```

