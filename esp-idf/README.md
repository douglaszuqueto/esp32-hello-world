# Blink com ESP32

## Código principal

```c
/* Importação das bibliotecas */
#include "freertos/FreeRTOS.h"
#include "freertos/task.h"
#include "driver/gpio.h"
#include "sdkconfig.h"

/* Define o Pino do Led Conectado */
#define LED_GPIO 4

/* Configura as GPIO */
void setup()
{
  gpio_pad_select_gpio(LED_GPIO);
  gpio_set_direction(LED_GPIO, GPIO_MODE_OUTPUT);
}

/* Blink */
void blink()
{
  while (true)
  {
    gpio_set_level(LED_GPIO, 0);
    vTaskDelay(1000 / portTICK_PERIOD_MS);

    gpio_set_level(LED_GPIO, 1);
    vTaskDelay(1000 / portTICK_PERIOD_MS);
  }
}

/* Metodo principal */
void app_main()
{

  /* Chamada da função setup */
  setup();

  /* Criação de uma tarefa para executar o blink */
  xTaskCreate(&blink, "blink", configMINIMAL_STACK_SIZE, NULL, 5, NULL);
}
```

## Referências
 
 * [ESP-IDF - Documentation](http://esp-idf.readthedocs.io/)
 * [ESP-IDF](https://github.com/espressif/esp-idf)
 * [ESP-IDF - Get Started(blink)](https://github.com/espressif/esp-idf/blob/master/examples/get-started/blink)
