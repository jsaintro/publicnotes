# PID Tuning
## Tune your hotend  
2. Run the following gcode
`M303 E0 S215 C8`
Note: Where 215 is the temp in C that you are going to use for your filament (Change accordingly).   
Note: This will heat the first nozzle (E0), and cycle around the target temperature 8 times (C8) at the given temperature (S200) ,200 C, and return values for P I and D
  
3. Add the results to your slicer config
Edit the start gcode for the printer profile
`M301  [C<value>] [D<value>] [E<index>] [I<value>] [L<value>] [P<value>]`
 
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
eyJoaXN0b3J5IjpbLTM1MTgzNzQwLDYzNjcxNDAxOSwtMTMwOD
I5NzAxNF19
-->