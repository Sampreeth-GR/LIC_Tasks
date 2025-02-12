# LIC_Tasks
Linear integrated circuit 


TASK1 : i) to find DC operating point
        ii) to do AC analysis
        iii) to do transient analysis and calculate gain.
![Screenshot 2025-02-12 194542](https://github.com/user-attachments/assets/98fd84ea-4e0f-40a0-a52f-e8323b9089a1)
 
circuit analysis:
* The above circuit is a common source amplifier using NMOS4
* Circuit consist of a resister (R) of 1K ohm with power rating of 100µ  watt
* Two DC voltage source [V1,V2]
* V1= gate voltage = 0.9volt
* V2= VDD = 1.8volt
* An NMOS4

for simulation we have used MOSFET with seperate specification, for this we have used net list known as spice netlist.
to add netlist first we need to go for spice directiove and type ".lib tsmc018.lib" where .lib  is keyword and tsmc018 is the PDf file name with all specification.

TASK1
i) to find DC operating point 
  we know that Resistor(R) has a power rating of 100 micro Watt 
  from Eq: P=VI
  where P=100u and V=1.8V we can find I 
  I=P/V=55.55µA = 5.5551 X 10-5
  where I is drain current, hence I=Id
  now if we know Id by trial and error we can find the width and length ot the MOSFET bu keeping anyone of the parameter constant
  lets keep length constant say 1µ meter. from trial and error we found ot that the width should be 6.86µ meter to get Id as 55.55µA.
  to find rest of the parameters we need to do simulation 
  to do simulation we need to go to simulation tab and select edit simulation and select DC op pnt and click ok 
  at last we need to run the simulation 
  ![Screenshot 2025-02-12 202352](https://github.com/user-attachments/assets/6229cd2c-ae6d-4e29-a4f8-a1738ff835fb)
  the above is the results of the simulation.

ii) to do AC analysis
  we need to change or generate sine waveform with specified amplitude and frequency 
  so we ned to right click on the V1 and select advanced and we need select sine we get option to type the specification.
  for DC offset = 0.9V
  for amplitude = 50mV
  for frequency = 1KHz
  at right side of the popup window there will me a box with tittle small signal AC analysis there we need to give AC amplitude as 1.
   to do simulation we need to go to simulation tab and select edit simulation and AC analysis and fill the following
type of sweep : decade
number of points per decade : 20
start frequency : 0.1Hz
stop frequency : 1THz
  click ok and run the simulation 
  ![Screenshot 2025-02-12 204331](https://github.com/user-attachments/assets/3613296c-bffc-4f41-b146-4acc5a1f342e)
  the above is the graph we get after simulation.
  here
  The green line represents the input voltage (V1).
  The blue line represents the output voltage (Vout) in dB.
  The x-axis represents frequency (log scale) from 100 mHz to 1 THz. 
  The y-axis represents gain (dB) and phase shift (degrees).It remains nearly constant at 0 dB, which is expected because the input signal has a fixed amplitude across frequencies.
   the bandwidth is only suitable for experimental purpose.     

