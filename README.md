# Micropython MAX7219 8 digit chain

A micropython lib for MAX7219 8 digit chain, uses SPI interface.

This code has been passed the test of ESP32 board, if you use ESP8266 or pyb, please change the ss pin as your expected.

## ESP32 example

**Chain of 8 digit**

```python
from machine import SPI, Pin
from max7219_8digit_chain import *

spi = SPI(1, sck=Pin(14), mosi=Pin(13))
ss = Pin(4, Pin.OUT)
ss.value(1)

display = Display(spi, ss, 1, 2)
counter = 0
while True:
    counter += 1
    time.sleep(0.01)
    display.write_to_buffer(str(counter))
    display.write_to_chip()
```
