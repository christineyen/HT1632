## Adafruit's HT1632 library + SureElectronics Matrix

Parts:

* [P7.62 24X16 Green LED Dot Matrix Unit Board](http://www.sureelectronics.net/goods.php?id=1123)
* Arduino Uno R3

While [Adafruit's 16x24 LED Matrix tutorial](http://ladyada.net/products/16x24LEDmatrix/) was awesome, the HT1632 library in order to interface with the matrix didn't quite match up with the coordinates / mapping of the LEDs in the SureElectronics board off eBay.

The matrixdemo Example, which is supposed to traverse the matrix from (0, 0) to (WIDTH, 0), and all the way to (WIDTH, HEIGHT), was traversing my LED panel like this:

	|----------------|----------------|----------------|
	|                                                  |
	|              ^ |              ^ |              ^ |
	|             [5]|             [4]|             [3]|
	|----------------|----------------|----------------|
	|                                                  |
	|              ^ |           ^  ^ |           ^  ^ |
	|             [2]|          [7][1]|          [6][0]|
	|----------------|----------------|----------------|
	
... and so on. I made a few tweaks to ```HT1632.cpp``` that got the coordinate system set up the way I want:

	|----------------|----------------|
	|[0]----->       |                |
	|                |                |
	|----------------|----------------|
	|                |                |
	|                |                |
	|----------------|----------------|
	|                |                |
	|                |            END |
	|----------------|----------------|
