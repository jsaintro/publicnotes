

## Physical Placement

1. Place thermocouple on bed (Should be as close to thermistor location as possible/accept on top of bed)
2. Place fiberglass pipe insulation over thermocouple
3. Place pieced of card board on top of insulation (To evenly compress when we lower hotend)
4. Manually lower hot end over cardboard insulation to secure and insulate thermocouple to bed

## Setup Firmware
1. edit configuration_adv.h
    `#define SHOW_TEMP_ADC_VALUES`
2. Edit configuration_prusa.h
   `#define BED_MAXTEMP 140` from 125
   **NOTE SET THIS BACK WHEN DONE WITH THESE TESTS!!**
4. Use M115 to get values
    ```
    ADC B:24.2C->978.31250
    ```
    Record termocouple value
    
5. Go in 5 deg C increments up to 120 (on the termocouple
   Wait 3min between to allow temp to stabilize
   Don't exceed a reading of 139C on the thermocuple

ADC B:25.6C->975.75000 26C
ADC B:30.7C->964.43750 30C
ADC B:35.0C->954.00000 34C 34.2C
ADC B:40.3C->938.37500 39C 39.2C
ADC B:45.2C->927.12500 43C 42.5C (Remeasure
ADC B:50.0C->915.68750 46C 45.9C
ADC B:55.3C->901.62500 50C 49.3C
ADC B:60.0C->882.93750 54C 53.7C (Remeasure)
ADC B:65.0C->861.43750 59C 58.3C
ADC B:70.0C->837.50000 63C 63.0C
ADC B:75.0C->811.56250 68C 67.5C
ADC B:79.9C->784.75000 77C 77.5C R
ADC B:85.1C->754.18750 82C 82.6C R
ADC B:90.0C->724.18750 87C 87.7C R
ADC B:94.9C->692.43750 86C 86.3C
ADC B:100.3C->656.43750 91C 91.3C
ADC B:105.2C->623.00000 95C 96.0C
ADC B:110.0C->590.81250 106C 107.0C R
ADC B:114.9C->553.62500 112C 113.0C R
ADC B:120.0C->515.75000 118C 118.5C R
ADC B:125.0C->479.81250 123C 124C R
ADC B:129.9C->445.62500 128C 129.5C R


2. Edit configuration_prusa.h
   `#define BED_MAXTEMP 125`
    **NOTE REALLY IMPORTANT!!**
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTc2MjYzMzQ5LC03NzQ3Njc4NDIsNjQ4OD
QxNDI3LDE3NzU4NTU5ODcsLTY3ODkxNTU0MCwtODI4MDgzMjU3
LC04MjAxMTUzNTEsMTcwMDY2MDU2Niw1MzQ0MzYzMDUsLTQ4ND
cxNTE4MiwxNzM2NjkwMjI5LDEwMDAwMzA3OTgsLTE3Mzk5NjQ3
NTMsMTIzOTI2OTUxOCwtNjk0Mjg1NDYwLDgxNzk2MjQyNywxOT
UxOTgwMDQzLDI1MTU3MDQ3MCwtNDU5MTAzMjA1LDgzMDY4NjAw
MF19
-->