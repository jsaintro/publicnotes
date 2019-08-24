

## Physical Placement

1. Place thermocouple on bed
2. Place fiberglass pipe insulation over thermocouple
3. Manually lower hot end over insulation and thermocouple to secure

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
ADC B:79.9C->784.62500 73C 73.2C
ADC B:84.9C->755.37500 77C 77.1C
ADC B:90.3C->722.12500 82C 82.0C
ADC B:94.9C->692.43750 86C 86.3C
ADC B:100.3C->656.43750 91C 91.3C
ADC B:105.2C->623.00000 95C 96.0C
ADC B:110.5C->587.43750 101C 101.0C
ADC B:115.2C->551.43750 106C 106.0C
ADC B:120.2C->514.31250 110C 111.0C
ADC B:125.1C->479.62500 116C 115.0C

2. Edit configuration_prusa.h
   `#define BED_MAXTEMP 125`
    **NOTE REALLY IMPORTANT!!**
<!--stackedit_data:
eyJoaXN0b3J5IjpbNjc4MjU0Mzc0LDE3MzY2OTAyMjksMTAwMD
AzMDc5OCwtMTczOTk2NDc1MywxMjM5MjY5NTE4LC02OTQyODU0
NjAsODE3OTYyNDI3LDE5NTE5ODAwNDMsMjUxNTcwNDcwLC00NT
kxMDMyMDUsODMwNjg2MDAwLC0yMTMwODQ0MTA0LDExMTkxNjg1
NzQsMTY1MjIxMzI0Nyw3ODY5MjYzODEsMTMyNTcwNjQ3OCwtMj
AyODQyMDE2OCwxNzc5NzU2NTY5LC0xNDExMzczMzM0LDEzMTcz
NzUwMzZdfQ==
-->