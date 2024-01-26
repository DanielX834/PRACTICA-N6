# PRACTICA-NIVEL-DE-AGUA
Este repositorio muestra la sexta practica del diplomado de como podemos programar una ESP32 para lograr ver el nivel de agua con el sensor ultrasonico HC-SR04 y con ayuda de indicadores como los led´s.

## Introducción
### Descripción
La ```Esp32``` la utilizamos en un entorno de adquision de datos, lo cual en esta practica ocuparemos un sensor (```HC-SR04```) para adquirir el nivel del agua, tambien se utulizan ```LED's``` para avisar cuando el recipiente se encuentra vacio; Cabe aclarar que esta practica se usara un simulador llamado [WOKWI](https://https://wokwi.com/).

## Material Necesario
Para realizar esta practica necesitas lo siguiente
- [WOKWI](https://https://wokwi.com/)
- Tarjeta ESP 32
- Sensor HC-SR04
- Luces LED
- Resistor

## Instrucciones
### Requisitos previos
Para poder usar este repositorio necesitas entrar a la plataforma [WOKWI](https://https://wokwi.com/).

### Instrucciones de preparación de entorno 
1. Abrir la terminal de programación y colocar la siguente programación:

```
// defines pins numbers
const int trigPin = 4;
const int echoPin = 15;
const int led1 = 22;
const int led2 = 21;
const int led3 = 19;
const int led4 = 18;

// defines variables
long duration;
int distance;
int safetyDistance;


void setup() {
pinMode(trigPin, OUTPUT); // Sets the trigPin as an Output
pinMode(echoPin, INPUT); // Sets the echoPin as an Input
pinMode(led1, OUTPUT);
pinMode(led2, OUTPUT);
pinMode(led3, OUTPUT);
pinMode(led4, OUTPUT);
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
if (safetyDistance>=10 && safetyDistance<=100)
{
  digitalWrite(led1, HIGH);
  digitalWrite(led2, LOW);
  digitalWrite(led3, LOW);
  digitalWrite(led4, LOW);
}
else if(safetyDistance>=100 && safetyDistance<=200) 
{
  digitalWrite(led1, HIGH);
  digitalWrite(led2, HIGH);
  digitalWrite(led3, LOW);
  digitalWrite(led4, LOW);
}
else if(safetyDistance>=200 && safetyDistance<=300) 
{
  digitalWrite(led1, HIGH);
  digitalWrite(led2, HIGH);
  digitalWrite(led3, HIGH);
  digitalWrite(led4, LOW);
}
else if(safetyDistance>=300 && safetyDistance<=400) 
{
  digitalWrite(led1, HIGH);
  digitalWrite(led2, HIGH);
  digitalWrite(led3, HIGH);
  digitalWrite(led4, HIGH);
}
else
{
  digitalWrite(led1, LOW);
  digitalWrite(led2, LOW);
  digitalWrite(led3, LOW);
  digitalWrite(led4, LOW);
}

// Prints the distance on the Serial Monitor
Serial.print("Distance: ");
Serial.println(distance);
delay (2000);
}
```

2. Es importante mencionar que para esta practica en particular no se necesita instalar ninguna libreria.

![](https://github.com/DanielX834/PRACTICA-N6/blob/main/2Libreria.jpg?raw=true)

3. Hacer la conexion de **HC-SR04** con la **ESP32** como se muestra en la siguente imagen.

![](https://github.com/DanielX834/PRACTICA-N6/blob/main/3Conexion.jpg?raw=true)

4. Hacer la conexion del **LED** y el **Resistor** con la **ESP32** como se muestra en la siguente imagen.

![](https://github.com/DanielX834/PRACTICA-N6/blob/main/4ConexionLEDS.jpg?raw=true)
  **Conexión HC-SR04**
  -VCC --> 5V
  -TRIG --> esp:4
  -ECHO --> esp:15
  -GND  --> GND
  
  **Conexión Led´s**
  -Resistencia 1 --> esp:22
  -Resistencia 2 --> esp:21
  -Resistencia 3 --> esp:19
  -Resistencia 4 --> esp:18

### Instrucciónes de operación

1. Iniciar simulador.
2. Visualizar los datos en el monitor serial.
3. Colocar distancia *doble click* al sensor **HC-SR04**
4. En los led´s se puede observar el nivel dependiendo la distancia que nos marca el sensor ultrasonico.

  
## Resultados

Una vez terminado iniciamos simulacion y se observaran los valores como la distancia en y los led´s tendran que encender dependiendo del nivel de agua.

![](
