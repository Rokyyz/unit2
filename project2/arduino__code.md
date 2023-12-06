```.py
#include <DHT.h>

#define DHTTYPE DHT11
#define DHTPIN1 13
#define DHTPIN2 11
#define DHTPIN3 9

DHT dht1(DHTPIN1, DHTTYPE);
DHT dht2(DHTPIN2, DHTTYPE);
DHT dht3(DHTPIN3, DHTTYPE);

void setup() {
  pinMode(12, OUTPUT);  // PIN 12 used as a 5V port
  digitalWrite(12, HIGH);
  Serial.begin(9600);
  dht1.begin();
  dht2.begin();
  dht3.begin();
}

void loop() {
  delay(5000);
  float h1 = dht1.readHumidity();
  float t1 = dht1.readTemperature();
  float h2 = dht2.readHumidity();
  float t2 = dht2.readTemperature();
  float h3 = dht3.readHumidity();
  float t3 = dht3.readTemperature();

 
  // Check if any reads failed and exit early (to try again).
  // if (isnan(h1) || isnan(h2) || isnan(h3) || isnan(t1) || isnan(t2) || isnan(t3)) {
  //   if ((t1)){
  //   Serial.println(F("Failed"));
  //   return;
  // }

  Serial.print(h1);
  Serial.print(F(","));
  Serial.print(t1);
  Serial.println(F(",1"));
  Serial.print(h2);
  Serial.print(F(","));
  Serial.print(t2);
  Serial.println(F(",2"));
  Serial.print(h3);
  Serial.print(F(","));
  Serial.print(t3);
  Serial.println(F(",3"));
}

```
