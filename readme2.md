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

here we have to do common mode 
here V1=Vicm1; V2=vicm2; V3=VDD; R1=R2=Rd; R3=Rss;
for the above task first we need to design the values of Rd, ​Rss and find current Iss flowing through the Rss.
from power equation P=V*I;
P=3mW; V=Vdd=3.3v.
therefore I=Iss=0.909mA.
we know Vp and Iss therefore Rss=550ohm.

applying load line equation for M1 we get 
Vocm1= VDD-Id*Rd
here, Id = half of Iss
therefore Id=0.455mA
substituting this we get Rd=3.516k ohm
from trial and error we found that aspect ratio is 7.8
from these parameter we got the desired output when we did DC analysis
![Screenshot 2025-03-03 205245](https://github.com/user-attachments/assets/dc518f47-8257-4a26-a098-19e2298d219d)

for transient analysis we need to find input and output maximum swing:
Vincm(max) = Vocm + Vtn 
fromthe library tsmc018 Vtn = 0.366v
therefore Vincm(max) = 1.7+0.366 = 2.066;
Vincm(min)=Vgs+Vp
