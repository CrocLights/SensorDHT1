# SensorDHT
## Sobre o sensor:
![IMG_20250827_132032976~2](https://github.com/user-attachments/assets/ae09b763-afbe-49df-89ff-93e54af98e5e)

## Fios
![Dht](https://github.com/user-attachments/assets/876ac786-8cf6-48db-8eb0-1993aa542555)
Você conecta o VCC do DHT com 3V, e SDA com o 34 e o GND na parte GND do ESP32

## Código:
#include <Bonezegei_DHT11.h>


#define DHTPIN 4   // Use outro pino, NÃO 34
Bonezegei_DHT11 dht(DHTPIN);


void setup() {
  Serial.begin(9600);
  dht.begin();
}


void loop() {
  delay(2000); // 2s já é suficiente


  if (dht.getData()) {
    float umidade = dht.getHumidity();
    float temperatura = dht.getTemperature();


    Serial.print("Umidade: ");
    Serial.print(umidade);
    Serial.print("% Temperatura: ");
    Serial.print(temperatura);
    Serial.println(" °C");
  } else {
    Serial.println("Falha ao ler do sensor DHT!");
  }
}
