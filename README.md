# MS51_RGBLED_GPIO
 MS51_RGBLED_GPIO

update @ 2020/05/07

1. Optimize GPIO toggle timing 

2. upload picture for reference

	- bit 1 : high level 0.375x2 us , low level 0.375x1 us

	- bit 0 : high level 0.375x1 us , low level 0.375x2 us

![image](https://github.com/released/MS51_RGBLED_GPIO/blob/master/RGB_1LED_0x00_0x01.jpg)

![image](https://github.com/released/MS51_RGBLED_GPIO/blob/master/RGB_1LED_0xFF_0x00_0x00.jpg)

3. Scenario : 

	- collect data by setLED_Color to fill DataBuffer array

	- display data by setLED_Display , also include reset pulse in front and back

4. Enable DemoStateChange will record pattern index in flash