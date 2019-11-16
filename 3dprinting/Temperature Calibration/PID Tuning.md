
# PID Tuning

based on https://reprap.org/wiki/PID_Tuning  

## Enable PID for both extruder and bed  

Note: This is required to use the PID autotune features  

1. Edit Marlin config
	  
 1.  Edit Configuration.h

         
  
 #define PIDTEMP
           
 #define PIDTEMPBED
  
  
1. Upload new marlin firmware  
  

## Tune your hotend  

1. Run the following gcode

    
   
 M303 E0 S200 C8
  
   
 This will heat the first nozzle (E0), and cycle around the target temperature 8 times (C8) at the given temperature (S200) ,200 C, and return values for P I and D
  
   
 Final output will be the lines you need to add to your marlin config
  
  
2. Update Marlin
	  
 1. Edit Configuration.h

  
         
 #define PIDTEMP
           
 #define DEFAULT_Kp <P>
           
 #define DEFAULT_Ki <I>
           
 #define DEFAULT_Kd <D>  

## Tune your heatbed  

1. Run the following gcode

     
  
 M303 E-1 S60 C8
  
   
 This will heat the first nozzle (E0), and cycle around the target temperature 8 times (C8) at the given temperature (S200) ,200 C, and return values for P I and D
  
   
 Final output will be the lines you need to add to your marlin config
  
  
2. Update Marlin
	  
 1. Edit Configuration.h

  
         
 #define PIDTEMPBED
           
 #define DEFAULT_bedKp <P>
           
 #define DEFAULT_bedKi <I>
           
 #define DEFAULT_bedKd <D>  

Markdown 1291  bytes 190  words 47  lines Ln 1, Col 0

HTML 904  characters 177  words 31  paragraphs
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTYwNDkyMDc2OCwtMTMwODI5NzAxNF19
-->