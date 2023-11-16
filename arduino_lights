# Arduino

## GIF work of proof



## Code for the program

```.py
#test arduino
import pyfirmata
from pyfirmata import Arduino
import time

board = Arduino('/dev/cu.usbserial-1420')
print('Success, Connected to Arduino')

data = pyfirmata.util.Iterator(board)
data.start()

LED_13 = board.digital[13]
LED_13.mode = pyfirmata.OUTPUT
LED_13.write(0)

LED_8 = board.digital[8]
LED_8.mode = pyfirmata.OUTPUT
LED_8.write(0)

LED_7 = board.digital[7]
LED_7.mode = pyfirmata.OUTPUT
LED_7.write(0)

n = 100
while n > 0:
    input = [0, 1]
    for x in input:
        for y in input:
            for z in input:
                LED_13.write(x)  # turn on
                LED_8.write(y)
                LED_7.write(z)
                time.sleep(1)

exit()

```
