#include "Arduino.h"
#include "WiFi.h"
#include "HTTPClient.h"
#include "DHT.h"

char ssid[] = "iPhone de Guilherme";
char pass[] = "abcdefgh";
char serverAddress[] = "https://api.tago.io/data";  // TagoIO address
char contentHeader[] = "application/json";
char tokenHeader[]   = "1544d37b-b88f-4304-9735-e1db8539edec"; // TagoIO Token

const int sensorLDR = 5; // define o pino do sensor de luz

int luz_atual = 0;

float dhtTemperatura = 0; // variável para armazenar a temperatura lida
float dhtUmidade = 0; // variável para armazenar a umidade lida

DHT dht (13, DHT11); // define o pino para o sensor DHT11

HTTPClient client;

void setup() {
  // put your setup code here, to run once:
  Serial.begin(9600);
  init_wifi();
  dht.begin();
}
void init_wifi() {
  Serial.println("Conectando WiFi");
  WiFi.begin(ssid, pass);
  while (WiFi.status() != WL_CONNECTED) {
    Serial.print(".");
    delay(1000);
  }
  Serial.println("Conectado");
  Serial.print("Meu IP eh: ");
  Serial.println(WiFi.localIP());
}
float temperatura = 0;
void loop() {
  lerUmid();
  lerTemp();
  lerLumi();
  
  // put your main code here, to run repeatedly
  char anyData[30];
  char postData[300];
  char anyData1[30];
  char bAny[30];
  int statusCode = 0;
  
  strcpy(postData, "{\n\t\"variable\": \"umidade\",\n\t\"value\": ");
  dtostrf(dhtUmidade, 6, 2, anyData);
  strncat(postData, anyData, 100);
  strcpy(anyData1, ",\n\t\"unit\": \"%\"\n\t}\n");
  strncat (postData, anyData1, 100);
  Serial.println(postData);
  client.begin(serverAddress);
  client.addHeader("Content-Type", contentHeader);
  client.addHeader("Device-Token", tokenHeader);
  statusCode = client.POST(postData);

  strcpy(postData, "{\n\t\"variable\": \"temperatura\",\n\t\"value\": ");
  dtostrf(dhtTemperatura, 6, 2, anyData);
  strncat(postData, anyData, 100);
  strcpy(anyData1, ",\n\t\"unit\": \"C\"\n\t}\n");
  strncat (postData, anyData1, 100);
  Serial.println(postData);
  client.begin(serverAddress);
  client.addHeader("Content-Type", contentHeader);
  client.addHeader("Device-Token", tokenHeader);
  statusCode = client.POST(postData);

   strcpy(postData, "{\n\t\"variable\": \"luminosidade\",\n\t\"value\": ");
  dtostrf(luz_atual, 6, 2, anyData);
  strncat(postData, anyData, 100);
  strcpy(anyData1, ",\n\t\"unit\": \"%\"\n\t}\n");
  strncat (postData, anyData1, 100);
  Serial.println(postData);
  client.begin(serverAddress);
  client.addHeader("Content-Type", contentHeader);
  client.addHeader("Device-Token", tokenHeader);
  statusCode = client.POST(postData);
  
  delay (2000);
  Serial.print("Status code: ");
  Serial.println(statusCode);
  Serial.println("End of POST to TagoIO");
  Serial.println();

  
  delay(5000);
}

void lerUmid() {
  dhtUmidade = dht.readHumidity();
}

void lerTemp() {
  dhtTemperatura =  dht.readTemperature();
}

void lerLumi(){
  // verifica a luminosidade
 luz_atual = analogRead(sensorLDR);
}

