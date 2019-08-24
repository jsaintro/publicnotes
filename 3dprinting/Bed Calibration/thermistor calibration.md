

## Physical Placement

1. Place thermocouple on bed
2. Place fiberglass pipe insulation over thermocouple
3. Manually lower hot end over insulation and thermocouple to secure

## Setup Firmware
1. edit configuration_adv.h
    `#define SHOW_TEMP_ADC_VALUES`
2. Use M115 to get values
    ```
    ADC B:24.2C->978.31250
    ```
    Record termocouple value
    
3. Go in 5 deg C increments up to 120 (on the termocouple
   Wait 3min between to allow temp to stabilize

ADC B:25.6C->975.75000 26C
ADC B:30.7C->964.43750 30C
ADC B:35.0C->954.00000 34.2C
ADC B:40.3C->938.37500 39.2C
ADC B:45.2C->927.12500 43C 42.5C
ADC B:50.0C->915.68750 46C 45.9C
ADC B:55.3C->901.62500 50C 49.3C

<!--stackedit_data:
eyJoaXN0b3J5IjpbNzg2OTI2MzgxLDEzMjU3MDY0NzgsLTIwMj
g0MjAxNjgsMTc3OTc1NjU2OSwtMTQxMTM3MzMzNCwxMzE3Mzc1
MDM2LC0xMTIzNTk5NDMwLC0xNjY4MjE1MCwtMTMzMzExNjI3NV
19
-->