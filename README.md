# esp32_blink
My first program involving an esp32 microcontroller.

Tools used:

ESP32, ESP-IDF

```C
#include <stdio.h>
#include "driver/gpio.h"
#include "freertos/FreeRTOS.h"
#include "freertos/task.h"
#define LED_BLUE GPIO_NUM_2

void app_main(void)
{
  gpio_reset_pin(LED_BLUE);
  gpio_set_direction(LED_BLUE, GPIO_MODE_OUTPUT);

  while(1)
  {
    gpio_set_level(LED_BLUE, 1);
    printf("LED on\n");
    vTaskDelay(1000 / portTICK_PERIOD_MS);

    gpio_set_level(LED_BLUE, 0);
    printf("LED off\n");
    vTaskDelay(1000 / portTICK_PERIOD_MS);
  }
}
```

# Code explanation:
```C
#include <stdio.h>
#include "driver/gpio.h"
#include "freertos/FreeRTOS.h"
#include "freertos/task.h"
```

Including libraries from esp-idf sdk. gpio.h enables u to make use of the general input/output pins onboard the esp32 board. task.h enables u to manage tasks.


```C
#define LED_BLUE GPIO_NUM_2
```
It simply gives the GPIO pin (2) a readable name (LED_BLUE) so you can use that name instead of the raw pin number in your code.

```C
gpio_reset_pin(LED_BLUE);
```
This resets the gpio pin 2 to its default hardware state and removes any previous configuration before setting the pin to output mode.

```C
gpio_set_direction(LED_BLUE, GPIO_MODE_OUTPUT);
```
It configures that GPIO pin to act as an output, meaning the ESP32 will drive the voltage on the pin (HIGH or LOW) instead of reading it.
