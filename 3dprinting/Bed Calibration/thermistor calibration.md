

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

B
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTg2Mjc2NDg2MSwtMTMzMzExNjI3NV19
-->