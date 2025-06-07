# PRACTICA2-ESP32-CON-DHT22-CON-LCDI2C
En esta practica se hará la conexión de un ESP32 con un DHT22, mostrando la información en un LCD I2C

## INTRODUCCIÓN

### DESCRIPCIÓN
La Esp32 la utilizamos en un entorno de adquision de datos, lo cual en esta practica ocuparemos un sensor (DTH11) para adquirir temperatura y humedad del entorno; Cabe aclarar que esta practica se usara un simulador llamado WOKWI.

### MATERIAL NECESARIO

Para realizar esta practica necesitas lo siguiente
- [WOKWI](https://wokwi.com/)
- Tarjeta ESP 32
- Sensor DHT11
- LCD 16x2 (I2C)

### INSTRUCCIONES

**REQUISITOS PREVIOS**
Para poder usar este repositorio necesitas entrar a la plataforma [WOKWI](https://wokwi.com/)

### Instrucciones de preparación de entorno

1. Abrir la terminal de programación y colocar la siguente programación:
```
#include "DHTesp.h"
#include <LiquidCrystal_I2C.h>
#define I2C_ADDR    0x27
#define LCD_COLUMNS 20
#define LCD_LINES   4

const int DHT_PIN = 15;

DHTesp dhtSensor;

LiquidCrystal_I2C lcd(I2C_ADDR, LCD_COLUMNS, LCD_LINES);

void setup() {

  Serial.begin(115200);
  dhtSensor.setup(DHT_PIN, DHTesp::DHT22);
  lcd.init();
  lcd.backlight();

}

void loop() {

  TempAndHumidity  data = dhtSensor.getTempAndHumidity();
  Serial.println("Temp: " + String(data.temperature, 1) + "°C");
  Serial.println("Humidity: " + String(data.humidity, 1) + "%");
  Serial.println("---");


  lcd.setCursor(2, 0);
  lcd.print("Diplomado");
  lcd.setCursor(0, 1);
  lcd.print("Automatizacion");
  delay(2000);
  lcd.clear();
  lcd.setCursor(2, 0);
  lcd.print("Adrian Salas");
  lcd.setCursor(2, 1);
  lcd.print("Industrial");
  delay(2000);
  lcd.clear();
  lcd.setCursor(0, 0);
  lcd.print("07 junio 2025");
  delay(2000);
  lcd.clear();

  lcd.setCursor(0, 0);
  lcd.print("  Temp: " + String(data.temperature, 1) + "\xDF"+"C  ");
  lcd.setCursor(0, 1);
  lcd.print(" Humidity: " + String(data.humidity, 1) + "% ");
  delay(2000);
  lcd.clear();

}
```
2. Instalar las siguientes librerias
   - **DHT sensor library for ESPx**
   - **LiquidCrystal I2C**
   Como se muestra en las siguentes imagenes.

![](https://github.com/AdrianSalasCh/PRACTICA2-ESP32-CON-DHT22-CON-LCDI2C/blob/main/DHT%20sensor%20library%20for%20ESPx%20P2.PNG)

![](https://github.com/AdrianSalasCh/PRACTICA2-ESP32-CON-DHT22-CON-LCDI2C/blob/main/LiquidCrystal%20I2C.PNG)

3. Hacer la conexion de DHT11 con la ESP32 y el LCD 16x2 (I2C) como se muestra en la siguente imagen.

![](https://github.com/AdrianSalasCh/PRACTICA2-ESP32-CON-DHT22-CON-LCDI2C/blob/main/CONEXION%20P2.PNG)

### Instrucciónes de operación

1. Iniciar simulador.
2. Visualizar los datos en el monitor serial y en el LCD.
3. Colocar la temperatura y humedad dando *doble click* al sensor **DHT11**

## RESULTADOS

Cuando haya funcionado, verás los valores dentro del monitor serial y en el LCD como se muestra en la siguente imagen.

![]()

## CRÉDITOS

Desarrollado por Ing. Luis Adrián Salas Chávez
- [GitHub](https://github.com/)
