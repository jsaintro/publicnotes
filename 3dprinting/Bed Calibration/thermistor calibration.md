

## Physical Placement

1. Place thermocouple on bed (Should be as close to thermistor location as possible/accept on top of bed)
2. secure with capton tape.  Just to keep in place.  don't have to cover head
3. Place fiberglass pipe insulation over thermocouple
4. Place pieced of card board on top of insulation (To evenly compress when we lower hotend)
5. Manually lower hot end over cardboard insulation to secure and insulate thermocouple to bed not super squshed but secure enough so air isn't making it to the thermocouple

## Setup Firmware
1. edit configuration_adv.h
    `#define SHOW_TEMP_ADC_VALUES`
2. Edit configuration_prusa.h
   `#define BED_MAXTEMP 140` from 125
   **NOTE SET THIS BACK WHEN DONE WITH THESE TESTS!!**
3. Install the new firmware
4. REset the eeprom (This is important)
    ```
    M502
    M500
    ```
6. Use M105 to get values
    ```
    ADC B:24.2C->978.31250
    ```
    Record termocouple value
    
7. Go in 5 deg C increments up to 120 (on the termocouple
   Wait 3min between to allow temp to stabilize
   Don't exceed a reading of 139C on the thermocuple

| adc temp | adc value | measured temp |
Recv:  T:18.57 /0.00 (988.00) B:25.00 /25.00 (977.00) @:0 B@:0 | 26
Recv:  T:18.57 /0.00 (988.00) B:30.00 /30.00 (966.00) @:0 B@:12 | 31
Recv:  T:18.57 /0.00 (988.00) B:35.00 /35.00 (954.00) @:0 B@:17 | 36
Recv:  T:18.93 /0.00 (987.50) B:40.00 /40.00 (939.00) @:0 B@:22 | 41
Recv:  T:19.29 /0.00 (987.00) B:45.00 /45.00 (922.00) @:0 B@:26 | 46
Recv:  T:20.00 /0.00 (986.00) B:50.00 /50.00 (903.00) @:0 B@:31 | 50
Recv:  T:20.50 /0.00 (985.00) B:55.00 /55.00 (881.00) @:0 B@:36 | 55
Recv:  T:21.12 /0.00 (983.75) B:60.00 /60.00 (857.00) @:0 B@:42 | 60
Recv:  T:22.00 /0.00 (982.00) B:65.00 /65.00 (830.00) @:0 B@:47 | 65
Recv:  T:23.00 /0.00 (980.00) B:70.00 /70.00 (801.00) @:0 B@:52 | 70
Recv:  T:24.00 /0.00 (978.00) B:75.00 /75.00 (770.00) @:0 B@:60 | 75




 ADC B:25.6C->975.75000 26C
ADC B:30.8C->964.18750 32C 31.2C R
ADC B:35.1C->953.81250 36C 35.7C R
ADC B:40.2C->938.56250 42C 41.4C R
ADC B:45.1C->927.43750 45C 44.9C R
ADC B:50.2C->915.25000 49C 48.6C R
ADC B:54.9C->903.25000 52C 52.0C R
ADC B:60.1C->882.50000 57C 57.3C R
ADC B:65.1C->860.93750 62C 62.3C R
ADC B:70.0C->837.43750 67C 67.3C R
ADC B:75.0C->811.43750 72C 72.5C R
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
ADC B:125.0C->479.87500 125C 125.5 R2
ADC B:129.9C->445.62500 128C 129.5C R
ADC B:130.2C->443.87500 129C 130.5C R2


2. Edit configuration_prusa.h
   `#define BED_MAXTEMP 125`
    **NOTE REALLY IMPORTANT!!**
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTUxOTE4MzUwNiwxOTMzMTIyNDc4LC0xMD
I0NDExNTE3LC0xMTU1MzE1MjE0LC0xMjYxOTA0NDcyLDM4MTM2
NzEzLC01MjUzNjIxNSwtMTc5NDI0NTE3MCw0NDIxMjU4NjYsMj
k3MDcyODExLDQ4NTY5Mzk5MywtOTIxNzg5MjU3LDExNTYzNTUz
NzcsMjA1MTA4MTU4MCwtNDAwNjk2MTIyLDEzOTAwODE1OSwtND
I4ODk0NzExLC0xODQwMzAwNTk1LC0xMjE2NjYzNjQ2LC0xMjcy
MDEyNzA3XX0=
-->