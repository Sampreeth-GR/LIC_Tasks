DIFFRENTIAL AMPLIFIERS

A differential amplifier is a special type of electronic circuit that makes weak signals stronger. What makes it special is that it only amplifies the difference between two input signals and ignores any noise that is common to both.
Because of this, differential amplifiers are very useful in many devices, especially when we need clear and accurate signals without interference.

A differential amplifier is built using two identical transistors that are arranged as shown below. 
![Screenshot 2025-03-03 192444](https://github.com/user-attachments/assets/493fe3c1-bd20-4a8c-a488-88389fe65fd1)

To work properly.
R1=R2=Rd;  M1=M2;  R3=Rss;

Differential Input: It looks at the difference between the two input voltages.
Common-Mode Input: If both inputs have the same voltage, the amplifier ignores it.
Differential Output: The output shows a signal based on the difference between the two inputs.
This design helps remove unwanted noise and focus only on the useful signal.

Differential amplifiers using MOSFETs are found in many electronic devices, including:
Operational Amplifiers (Op-Amps)
High-Frequency Applications
Analog Circuits in Chips



THE TWO MAIN TYPES OF ANALYSIS IN DIFFERENTIAL AMPLIFIER ARE:
1. Differential Mode Analysis
In this mode, the amplifier processes the difference between the two input signals.
The output is proportional to the voltage difference between the inputs.
It Rejects common noise and only amplifies the signal difference.
(Vincm1 - Vincm2)

2. Common Mode Analysis
both inputs receive the same signal (common-mode input).
the output should be zero, meaning the amplifier ignores common signals.
It Helps remove unwanted interference (like electrical noise).
(Vincm1 - Vincm2)/2.

CHARECTERISTICS OF MOSFET DIFFERENTIAL AMPLIFIER:
Differential Gain (Ad):                 The gain of the amplifier for differential input signals.

Common-Mode Gain (Acm):                 The gain of the amplifier for common-mode input signals.

Common-Mode Rejection Ratio (CMRR):     The ratio of differential gain to common-mode gain (CMRR = Ad/Acm).

Transconductance (gm):                  A key parameter affecting the gain of the MOSFET amplifier.

Output Resistance (ro):                 The output resistance of the MOSFETs.

Power Dissipation:                      The amount of power consumed by the amplifier.
​


Task: design and analyze differential amplifier circuit for the following conditions
VDD=3.3v, power<=3mW, Vincm=1.65v, Vocm=1.7v, Vp=0.5v. perform DC, AC analysis, frequency responce and extract the parameters?

NOW FOR DC ANALYSIS:
here we have to do common mode 
here V1=Vicm1; V2=vicm2; V3=VDD; R1=R2=Rd; R3=Rss;
for the above task first we need to design the values of Rd, ​Rss and find current Iss flowing through the Rss.
from power equation P=V*I;
P<=3mW; V=Vdd=3.3v.
therefore I=Iss=0.909mA.
we know Vp and Iss therefore Rss=550ohm.

applying load line equation for M1 we get 
Vocm1= VDD-Id*Rd
here, Id = half of Iss
therefore Id=0.455mA
for power less than 3mW we need to design aspect ratio such a way that Id is less than 0.455mA
substituting this we get Rd=3.516k ohm
to get Vout exactly 1.7V and Id less than 0.455mA we need to adjust the value of the Rd greater than the claculated value because current is inversly proportional to resistance [ohm law].
from trial and error we found that aspect ratio is 7.6 but,  to get Id less than calculated Value we need to put Rd value as 3.563058k ohm.
from these parameter we got the desired output when we did DC analysis
![WhatsApp Image 2025-03-06 at 18 28 00_70e3aa78](https://github.com/user-attachments/assets/982e1469-c5bb-41af-a1eb-b12b6d28cf6e)

In a differential amplifier, MOSFETs must operate in the saturation region to ensure proper amplification 

Linear and High Gain Operation​ is primarily controlled by the gate-source voltage rather than the drain-source voltage 
This allows the differential amplifier to achieve a high voltage gain, which is crucial for amplification.

Avoiding Signal Distortion
In triode region, the MOSFET acts more like a resistor, making the amplifier behave non-linearly.
This distorts the differential input signal and reduces gain stability.
Maintaining a Stable Common-Mode Rejection Ratio (CMRR)

A differential amplifier is designed to reject common-mode signals.
Proper saturation operation ensures that the current mirror or active load functions correctly, maintaining a high CMRR.

to find Vgs and Vds values we need to go to view option and select spice error log. below is the result
![WhatsApp Image 2025-03-06 at 18 38 55_0794c39d](https://github.com/user-attachments/assets/afef4dbb-385e-4783-9581-6b8eed4ce22b)
here for MOSFET to operate in saturation region Vds should be greater than Vov. [Vds>Vov]
as per the simulation Vgs=1.16V, Vtn=0.404V and Vds=1.21V.
Vov=0.756V which is less than Vds hence design is in saturation region 

if we notice according to our spice library Vtn is 0.366V but is the simulation we can see that Vtn=0.404 there is a difference of 0.038V.
it may be due to body effect, Variability in the Model Parameters.

now, if we slightly increase or decrease the Vincm,
there will be a slight variation in Id, as Vincm effects the channel, because of change in Id there will be change in Vo1 
ID is directly proportional to Vincm 
Vout is inversly proportional to Id. {[Vo=Vdd-Id*Rd] where Vdd,Rd-constant}.
it can be seen using simulation:

![WhatsApp Image 2025-03-06 at 19 04 35_ba5cbdbc](https://github.com/user-attachments/assets/373b76df-a763-4b36-8289-67443e5ecc13)
so when Vicm=1.8V, Id=0.5mA and Vo=1.44V

![WhatsApp Image 2025-03-06 at 19 04 35_cd4f1dfa](https://github.com/user-attachments/assets/2aa1bd25-d2d0-4696-8aa1-abea87ae876d)
when  Vicm=1.5V, Id=0.3mA and Vo=1.955V


so from DC analysis we can conclude that: Q-point when VGS=1.65 is {(1.21V,0.449mA)}
![WhatsApp Image 2025-03-06 at 19 25 18_149711ab](https://github.com/user-attachments/assets/7d2a1819-a978-4aeb-9e05-08ddaabfbfc3)









NOW FOR TRANCIENT ANALYSIS:
first we need to find vincm(min), Vincm(max).
Vincm(min)= Vth + Vp = 0.366 + 0.5 = 0.866V.
Vincm(max) = Vdd - (Id*Rd) + Vth = 2.066V.

for trancient analysis 
Replace DC input with an AC signal.
Use SINE(dc_offset, Amplitude, Frequency).
Set Stop Time: 5ms.
Run the simulation.

with two amplitude of 50mV and a phase difference of 180 degree we can check whether circuit act as a linear amplifier or not with calculated range.

for Vincm < 0.866V  and Vincm > 2.066 there should be distortion 
![Screenshot 2025-03-06 201006](https://github.com/user-attachments/assets/ebd35625-b5fc-48e1-b615-1346ba9d39b1)

