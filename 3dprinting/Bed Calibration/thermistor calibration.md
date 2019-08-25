

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
ADC B:30.8C->964.18750 32C 31.2C R
ADC B:35.1C->953.81250 36C 35.7C R
ADC B:40.2C->938.56250 42C 41.4C R
ADC B:45.1C->927.43750 45C 44.9C R
ADC B:50.2C->915.25000 49C 48.6C R
ADC B:54.9C->903.25000 52C 52.0C R
ADC B:60.1C->882.50000 57C 57.3C R
ADC B:65.0C->861.43750 59C 58.3C
ADC B:70.0C->837.50000 63C 63.0C
ADC B:75.0C->811.56250 68C 67.5C
ADC B:79.9C->784.75000 77C 77.5C R
ADC B:85.1C->754.18750 82C 82.6C R
ADC B:90.0C->724.18750 87C 87.7C R
ADC B:95.0C->692.12500 92C 92.8C R
ADC B:100.1C->657.75000 98C 98.2C R
ADC B:105.0C->624.50000 102C 103.0C R
ADC B:110.0C->591.06250 108C 108.0C R
ADC B:114.9C->553.62500 112C 113.0C R
ADC B:120.0C->515.75000 118C 118.5C R
ADC B:125.0C->479.81250 123C 124C R
ADC B:129.9C->445.62500 128C 129.5C R


2. Edit configuration_prusa.h
   `#define BED_MAXTEMP 125`
    **NOTE REALLY IMPORTANT!!**
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTQwMDY5NjEyMiwxMzkwMDgxNTksLTQyOD
g5NDcxMSwtMTg0MDMwMDU5NSwtMTIxNjY2MzY0NiwtMTI3MjAx
MjcwNywtMTM1MzQ5MTg5LC0xNjY2MDg4NjE5LC0xNjg4MzE0OD
E0LDE3MDY5MjI5NDksMTc2MjYzMzQ5LC03NzQ3Njc4NDIsNjQ4
ODQxNDI3LDE3NzU4NTU5ODcsLTY3ODkxNTU0MCwtODI4MDgzMj
U3LC04MjAxMTUzNTEsMTcwMDY2MDU2Niw1MzQ0MzYzMDUsLTQ4
NDcxNTE4Ml19
-->