# PRACTICA NIVEL DE AGUA 

## Programación
```
// defines pins numbers
const int trigPin = 4;
const int echoPin = 15;
const int buzzer = 5;
const int ledPin = 2;

// defines variables
long duration;
int distance;
int safetyDistance;


void setup() {
pinMode(trigPin, OUTPUT); // Sets the trigPin as an Output
pinMode(echoPin, INPUT); // Sets the echoPin as an Input
pinMode(buzzer, OUTPUT);
pinMode(ledPin, OUTPUT);
Serial.begin(9600); // Starts the serial communication
}


void loop() {
// Clears the trigPin
digitalWrite(trigPin, LOW);
delayMicroseconds(2);

// Sets the trigPin on HIGH state for 10 micro seconds
digitalWrite(trigPin, HIGH);
delayMicroseconds(10);
digitalWrite(trigPin, LOW);

// Reads the echoPin, returns the sound wave travel time in microseconds
duration = pulseIn(echoPin, HIGH);

// Calculating the distance
distance= duration*0.034/2;

safetyDistance = distance;
if (safetyDistance>5 && safetyDistance<9)
{
  digitalWrite(buzzer, LOW);
  digitalWrite(ledPin, HIGH);
}
else if(safetyDistance>10 ) 
{
  digitalWrite(buzzer, HIGH);
  digitalWrite(ledPin, HIGH);
}
else
{
  digitalWrite(buzzer, LOW);
  digitalWrite(ledPin, LOW);
}

// Prints the distance on the Serial Monitor
Serial.print("Distance: ");
Serial.println(distance);
}
```

## Conexión

![](https://github.com/DiegoJm10/PRACTICA-NIVEL-DE-AGUA/blob/main/ESP32%20ULTRASONICO%20con%20parametros%20-%20Wokwi%20ESP32,%20STM32,%20Arduino%20Simulator%20-%20Google%20Chrome%2010_06_2023%2010_45_36%20a.%20m..png?raw=true)
