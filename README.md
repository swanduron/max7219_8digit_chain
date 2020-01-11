# Micropython MAX7219 8 digit chain

A micropython lib for MAX7219 8 digit chain, uses SPI interface.

This code has been passed the test of ESP32 board, if you use ESP8266 or pyb, please change the ss pin as your expected.

This lib is modified from other max7219 8digit as below link, thanks for the original contributer.

https://github.com/pdwerryhouse/max7219_8digit.git

## ESP32 example

**Display a increasing number in 2 digit module**

```python
from machine import SPI, Pin
from max7219_8digit_chain import *
import time

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
**Change intensity of module**

```python

display.brightness(3)

```

**Demo image**
![image](https://github.com/swanduron/max7219_8digit_chain/blob/master/image/demo.jpg)


**Update schedule**

In current code, if the string is '1.2345', the dot will use one digit instead of following above digit, this is not expected behavior.