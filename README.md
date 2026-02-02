#include <SoftwareSerial.h>

SoftwareSerial BT(2, 3); // RX, TX
int led = 13;

void setup() {
  pinMode(led, OUTPUT);
  digitalWrite(led, LOW);

  Serial.begin(9600);
  BT.begin(9600);

  Serial.println("Bluetooth LED Control Ready");


void loop() {
  if (BT.available()) {
    char data = BT.read();
    Serial.println(data);

    if (data == '1') {
      digitalWrite(led, HIGH); // LED ON
    }
    if (data == '0') {
      digitalWrite(led, LOW);  // LED OFF
    }
  }
}