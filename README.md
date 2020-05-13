# MS51_RGBLED_GPIO
 MS51_RGBLED_GPIO

update @ 2020/05/13

1. add define , ENABLE_BIT_900_300 and ENABLE_BIT_750_375

	- bit 1 : high level 0.9 us , low level 0.3 us

	- bit 0 : high level 0.3 us , low level 0.9 us

![image](https://github.com/released/MS51_RGBLED_GPIO/blob/master/bit1_900ns_300ns.jpg)

![image](https://github.com/released/MS51_RGBLED_GPIO/blob/master/bit0_300ns_900ns.jpg)

2. behavior about extra GPIO toggle to monitor bit 1 (ENABLE_BIT_900_300) 

	- scenario : in a for loop , toggle start with GPIO high (ch01) , end with GPIO low
	
	for (i = 0 ; i < 5 ; i++)
	
	{
	
		GPIO high
		
		bit 1 high level
		
		bit 1 low level
		
		GPIO low
		
	}
	
	* check below pic no.3, bit 1 low level base on GPIO low timing , will close to 0.3 us
![image](https://github.com/released/MS51_RGBLED_GPIO/blob/master/bit1_900ns_test_with_GPIO_forloop.jpg)

3. behavior about extra GPIO toggle to monitor bit 0 (ENABLE_BIT_900_300) 

	- scenario : in a for loop , toggle start with GPIO high (ch01) , end with GPIO low
	
	for (i = 0 ; i < 5 ; i++)
	
	{
	
		GPIO high
		
		bit 0 high level
		
		bit 0 low level
		
		GPIO low
		
	}
	
	* check below pic no.3, bit 0 low level base on GPIO low timing , will close to 0.9 us	
![image](https://github.com/released/MS51_RGBLED_GPIO/blob/master/bit0_900ns_test_with_GPIO_forloop.jpg)

4. behavior about extra GPIO toggle to monitor bit 1 (ENABLE_BIT_900_300) 

	- scenario : in a single loop , toggle start with GPIO high (ch01) , end with GPIO low
	
	GPIO high
	
	bit 1 high level
	
	bit 1 low level
	
	bit 1 high level
	
	bit 1 low level
	
	bit 1 high level
	
	bit 1 low level
	
	bit 1 high level
	
	bit 1 low level
	
	bit 1 high level
	
	bit 1 low level	
	
	GPIO low
	
	* check below pic , bit 1 high level close to 0.9 us , low level close to 0.3 us  
![image](https://github.com/released/MS51_RGBLED_GPIO/blob/master/bit1_900ns_test_with_GPIO_continuous.jpg)


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