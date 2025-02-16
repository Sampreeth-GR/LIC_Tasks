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
  so we need to right click on the V1 and select advanced and we need select sine we get option to type the specification.
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

iii) to do transient analysis and calculating gain
   to do transient analysis we need to click on simulation tab and select edit simulation in the popup window we need to select transient and give the specifications 
   for stop time : 5ms
   for time to start saving data : 0s
   and click ok and run the simulation 
   ![Screenshot 2025-02-16 111942](https://github.com/user-attachments/assets/c618dfb2-b0b3-43bd-aa3b-b331f8e4217d)
   the above is the graph we get after simulation.
   here
   The green line represents the input voltage (V1).
   the blue line represents the output voltage (V2).
   the output volatage graph looks like inverted sine wave because it is one of the charecteristics of CS amplifier

   to calculate gain we need to find ratio of V2/V1
   by looking in to graph V2 is Vp-p which is (1.644V-1.573V) 0.071.
   similarly V1 is Vp-p which is (950mV-850mV) 100mV.
   therefore gain (Av)= 0.071V / 100mV.
   Av=0.71


   RESULT:
   Simulated DC operating point results: 
   during DC analysis we found that for 
   Given power rating: 100 µW
   Given VDD = 1.8V
   Drain current (Id):55.55𝜇𝐴
   By setting L = 1µm, the required width W = 6.86µm was determined using trial and error.


   Simulated AC analysis results:
   during AC analysis we found that for 
   DC Offset = 0.9V
   Amplitude = 50mV
   Frequency = 1 kHz    
   Bandwidth limited for experimental use
   Gain remains nearly constant (0 dB) for most frequencies


   simulated trasient analysis results:
   during transient analysis we found that for 
   Input Signal: Sine Wave (1 kHz, 50mV amplitude)
   Output is an inverted sine wave 
   Av = 0.71


   INFERENCE:
   During Transient analysis we found that gain is less than 1, which is a weak amplification. 
   therefore in order to increase amplification there are some ways 
   
   a) we know that for the above circuit Av= (-gm*R)
      hence by increasing the value of R we can increase Av

   b) we can also increase Av by increasing gm
      https://youtu.be/LvE0curDf_Q?si=Df1Tb1B7ZXhyWp-y   
      the above link is a video for varying gm keeping various parameters constant 
      ![WhatsApp Image 2025-02-16 at 12 09 19_7c292e4a](https://github.com/user-attachments/assets/06245cdd-c62b-47d8-bd91-e7768a670407)

 
 for simulation purpose i have varied R value to 10Kohm 
 by varying R even Id gets changed so we need to again wind correct W/L value to get desierd Id
 by trial and error we foud that new W/L value is 1.9125 (W=3.825𝜇m,L=2𝜇m). so we get Id=55.5𝜇A
 after varying the below is the result of DC analysis
 ![Screenshot 2025-02-16 121518](https://github.com/user-attachments/assets/83c6f8ae-c9a2-4ecb-b537-d7c47f0572f6)

 for AC and Transient analysis by following the same procedure as mentioned above we get the results as below.
 ![Screenshot 2025-02-16 121852](https://github.com/user-attachments/assets/ecb9f0aa-baa9-4138-bc9f-fbec58b8989c)



 ![Screenshot 2025-02-16 122003](https://github.com/user-attachments/assets/2da770cf-f147-4d5c-aeff-b8a053958edb)


  from th above transient analysis we can see that gain (Av) = (1.34-1.14)V/100mV.
  therefore gain (Av) = 2
  which is greater than 1



 


    



