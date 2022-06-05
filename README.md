# statusDisplay
Status display for home automation


## Power consumption
According to the manufacturer, each led could consume 0,3W (± 0,01%). For my first example statusDisplay with 3x10 LEDs that would mean up to 9W (so 1,8A @ 5V).
The first tests with the statusDisplay (LEDs behind a white paper that is used for labeling) showed that a brightness of 20% is more than enough and the Wemos D1 mini was able to drive all 30 LEDs without troubel or excesive heat. To be on the sure side I've connected a digital multimeter between the +5V pin of the Wemos D1 mini and the LED strips.
The following currencies were meassured:

| Brightness 	| White 	| Red   	| Green 	| Blue  	|
|------------	|-------	|-------	|-------	|-------	|
| 0-10% *    	| 23,6  	| 23,6  	| 23,6  	| 23,6  	|
| 15%        	| 26,9  	| 24,7  	| 24,7  	| 24,7  	|
| 20%        	| 35,3  	| 27,7  	| 27,7  	| 27,7  	|
| 30%        	| 59,7  	| 35,9  	| 35,8  	| 35,8  	|
| 40%        	| 103,8 	| 51,0  	| 50,7  	| 50,6  	|
| 50%        	| 170   	| 74,1  	| 73,5  	| 73,4  	|
| 60%        	| 270   	| 106,0 	| 105,3 	| 105,1 	|
| 70%        	| 390   	| 148,8 	| 146,8 	| 146,5 	|
| 80%        	| 540   	| 210   	| 210   	| 210   	|
| 90%        	| 670   	| 280   	| 280   	| 280   	|
| 100%       	| 830   	| 370   	| 360   	| 360   	|
|             |All values in mA   |        	|        	|     

*Notes about the values:*  
- *\*) There is no difference in power consumption for 0-10%, the same current is drawn if the LEDs are turned to "off"*  
- *All values >200mA were meassured with a resolution of 10mA*
- *Brightness for 80%-100% was set only for 1-2 seconds to prevent damage to the powersupply*
- *30 LEDs were powered at once*

I'm not sure why only 0,83A instead of the expected 1,8A were drawn when switching to 100%. But the brightness is definitifely too much, it's nearly impossible to read the labels near the leds due to the brightness (sunglasses?)

### Conclusion
Theoretically it's only possible to power 8,3 LEDs (2,5W/0,3W per LED) with a Wemos D1 mini (500mA fuse). But it's no problem to power 30 LEDs at once if you set your system to a relaistic brightness of 20%. Personally I feel that even 30% is too bright to easily read the text near the LEDs. Maybe in a bright environment a logic could be added (if needed) to set the brightness to 30% during daylight and 15% during night. I'll stay with 20% for now.

### Recommendation
To further reduce the risk of damaging/overheating your Wemos D1 mini you could directly use a Power supply with only 500mA and add an additional fuse with ~200mA into to +5V wire. That would then be still enough to enable all LEDs with white at 50% (don't forget sunglasses).
