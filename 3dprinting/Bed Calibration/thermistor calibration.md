

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
ADC B:60.0C->882.93750 54C 53.7C
ADC B:65.0C->861.43750 59C 58.3C
ADC B:70.0C->837.50000 63C 63.0C
ADC B:75.0C->811.56250 68C 67.5C
ADC B:79.9C->784.62500 73C 73.2C
ADC B:84.9C->755.37500 77C 77.1C

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTk1MTk4MDA0MywyNTE1NzA0NzAsLTQ1OT
EwMzIwNSw4MzA2ODYwMDAsLTIxMzA4NDQxMDQsMTExOTE2ODU3
NCwxNjUyMjEzMjQ3LDc4NjkyNjM4MSwxMzI1NzA2NDc4LC0yMD
I4NDIwMTY4LDE3Nzk3NTY1NjksLTE0MTEzNzMzMzQsMTMxNzM3
NTAzNiwtMTEyMzU5OTQzMCwtMTY2ODIxNTAsLTEzMzMxMTYyNz
VdfQ==
-->