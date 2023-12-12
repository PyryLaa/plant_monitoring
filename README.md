# plant_monitoring
Plant monitoring system with Arduino Nano

This project was made as a part of our MCU course at TAMK. This is my copy of the main source file, the whole project
repo can be found at https://github.com/CaptMikachu/NANO_plant-monitor-system

The idea of this project was to build a plant monitoring system using Arduino Nano board with analog sensors, DC waterpump and I2C display to show monitored data to user.
My own contribution to this project's code was both ADC related functions (ADC_init and ADC_read) and the EEPROM related functions. Both were implemented with controlling 
the registers of ATMega328p directly.

There is a total of 6 sensors in the project. 
2 moisture sensors for the top and bottom moistures of the plant container. 
2 temperature sensors for air and watering water temperature.
1 ultrasonic sensor to monitor water level
1 light sensor to monitor ambient light level (this was left mostly unused, since there was no clear information what the data produced by this sensor meant)
Interfacing with the device is done with 4 pushbuttons, de-bouncing done with hardware.

The basic functionality of the device is as follows:
When powered up, the device asks the user whether to use default values for the sensors thresholds or user defined. If user defined values chosen, they are loaded from EEPROM.
After the values have been loaded, the device starts its monitoring. The default view shows air temperature, top moisture and light levels. User can scroll through different
views with the push buttons. 

User can also modfiy the alarm thresholds for air and water temperatures, both moisture levels and the water level. User can also set their desired water container height.
These values are save to EEPROM so they are preserved in the case of power loss or board reset. 

Automatic watering with the DC pump starts if the top moisture sensor reading goes below the set low threshold, goes on for 3 seconds and stops. This happens until the 
bottom moisture sensor reads as if it is in water. This means that the water has started to come through the bottom soil and the plant is watered. There is also a manual
watering option if the user wants.

There are 3 different alarm sounds/songs for air temperature low, water temperature low and water level low. These thresholds can also be modified by the user and are also
saved to EEPROM memory.


Sensors used in this project are mostly DFRobot's sensors, with the exception of the water temperature sensor which is a Carel NTC thermistor.
