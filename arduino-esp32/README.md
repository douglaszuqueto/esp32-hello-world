# Blink com ESP32

## Código principal

```c
#define LED_GPIO 4

void setup() {
  pinMode(LED_GPIO, OUTPUT);
}

void loop() {
  digitalWrite(LED_GPIO, HIGH);
  delay(1000);
  digitalWrite(LED_GPIO, LOW);
  delay(1000);
}
```

## Referências

 * [Aduino ESP32](https://github.com/espressif/arduino-esp32)
