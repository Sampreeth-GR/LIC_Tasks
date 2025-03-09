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
for Vincm=0.5V
as Vgs<=Vth
The transitor is in off state , therefore distortion in the output circuit .
![Screenshot 2025-03-06 201006](https://github.com/user-attachments/assets/ebd35625-b5fc-48e1-b615-1346ba9d39b1)
for Vincm=1.65V
![Screenshot 2025-03-06 202414](https://github.com/user-attachments/assets/a031627a-c147-4afd-b460-24a8c989ac44)
for Vincm=3V
![Screenshot 2025-03-06 202356](https://github.com/user-attachments/assets/296009f2-bb1e-414c-b6c0-16d168498503)
for differential gain 
we need subtract the Vo1-Vo2 and do simulation 
![Screenshot 2025-03-09 113728](https://github.com/user-attachments/assets/f59057ff-c244-4e48-b5f5-0f84eeba689f)
here Vincm(p-p)=0.1v and (Vo1-Vo2)p-p=0.728v
therefore differential gain is 7.28

NOW FOR AC ANALYSIS:

for this we have  to calculate gain with theoretical values .
gain = Av= -gm*Rd where gm= (2Id)/Vov = 1.202mS
Av= -1.202m *3.563058k = -4.2841V/V
as we know Av in dB = 20Log AV
gain is 12.63dB
![Screenshot 2025-03-07 110914](https://github.com/user-attachments/assets/8f897e03-5eda-468c-9650-f1330cce8690)
by simulation we can see that gain is 11.42, because we have adjusted the RD and Id is less than 0.45mA.
the graph of gain has not decreased in the above ckt, this is because of the parasetic capacitors in mosfet 
now if we connect a capaciors accross the Vout terminals we can slightly overcome the problem
![Screenshot 2025-03-09 113004](https://github.com/user-attachments/assets/4faa52ca-d9a9-4faa-8210-6675dbcb79fc)
for the above ckt design now we can find out the bandwidth
for BW we need to subtract gain with 3dB which is 0-46Hz 














CIRCUIT 2:


replacing R3 with a current source of less than 0.909mA for power less than 3mW so we take Iss as 0.899mA.
as we replace R3 by a current source there is a slight dicrease in Vout so to get currect Vout i have replaced RD value.
when i theoreticall calculated the value of Rd it was 3.52K ohm but in previous ckt i increased the value of rd to get Vo=1.7v,
but now that calculated value almost correctly matched for the design, and got Vout=1.7V
 by following the same procedure we do DC,trancient and AC analysis:
 DC ANALYSIS:
 ![Screenshot 2025-03-06 214014](https://github.com/user-attachments/assets/1614a63f-78d7-4f37-96ff-86b6aaa76b70)
TRANCIENT ANALYSIS:
![Screenshot 2025-03-06 215451](https://github.com/user-attachments/assets/e3713a3d-9795-4efd-8b44-5aa9344aed54)
differential gain analysis:
![Screenshot 2025-03-09 114121](https://github.com/user-attachments/assets/04d608db-7714-4bec-ba87-21faa1103522)
gain =7.19
AC ANALYSIS:
![Screenshot 2025-03-07 111708](https://github.com/user-attachments/assets/c4b2fd89-6e47-43cf-b981-55db15400d7e)
to avoid parasetic capacitance
![Screenshot 2025-03-09 114524](https://github.com/user-attachments/assets/51e3e600-9ec5-4605-bae6-2e4c396ecd01)
BW= (11.26-3db)=47.59Hz
   



CIRCUIT 3:

for circuit 3 we need to replace current source by a mosfet (M3) and design its Vgs in such a way that its drain current matches the Iss value 
for designing the mosfet we need to find the right value of Vgs first 
we have theory Vgs=Vp+Vtn
here Vtn is the threshold voltage of M3
from calculation Vgs of M3 is 0.866V from traial and error method we fount the aspect as 39.1 and we set the Id(M3) as 0.899mA.
DC ANALYSIS:
![Screenshot 2025-03-07 162943](https://github.com/user-attachments/assets/61065de5-1715-4a71-a9b5-41468b328ee2)
here there is a slight increase in Vout this is beacuse:
When replacing an ideal current source with a MOSFET current source, the finite output resistance (r0) of the MOSFET causes a slight increase in the source voltage of the differential pair. Since the gate voltage remains fixed, this reduces the effective VGS of the input transistors. To compensate and stay in saturation, the drain voltage (output voltage) increases. This results in a higher output voltage compared to the ideal current source case. 
to compensate it i have changes the value of Rd. Rd=3.5571k
![Screenshot 2025-03-07 164916](https://github.com/user-attachments/assets/f865ab2c-743c-4cf3-a5ae-972dbd04d8ee)
![Screenshot 2025-03-07 165008](https://github.com/user-attachments/assets/9a720873-dbcf-420a-9b32-42ca49a943dd)
TRANSIENT ANALYSIS:
![Screenshot 2025-03-07 165146](https://github.com/user-attachments/assets/296a4405-77d3-4a8e-9cc0-883f68e9d41e)
differential gain
![Screenshot 2025-03-09 114737](https://github.com/user-attachments/assets/0190e13e-8d02-4314-a7c6-cf017bd4aa0a)
gain=7.27
AC ANALYSIS
![Screenshot 2025-03-07 165252](https://github.com/user-attachments/assets/c144688f-efac-4e7f-acde-f0241142f051)
avoiding parasetic capacitance
![Screenshot 2025-03-09 115023](https://github.com/user-attachments/assets/8c3ceedd-a939-45b5-859f-af4402421a70)
11.34-3dB
BW=46.79Hz

CIRCUIT 4:

now we have to replace Rd with MOSFET which acts as a resister for this we have replaced the RD by PMOS
with an aspect ratio of 14.0155 which act as resistor of value 3.5577K ohm.
DC ANALYSIS:

![Screenshot 2025-03-07 221402](https://github.com/user-attachments/assets/fc94e473-af35-4936-aa0d-59ad2d8257b1)
TRANSIENT ANALYSIS:
![Screenshot 2025-03-07 221711](https://github.com/user-attachments/assets/e4a9b63d-fc84-4896-bc6d-ae033ad110c9)
the below is the graph of the differential gain of two outputs
![Screenshot 2025-03-09 103956](https://github.com/user-attachments/assets/63e72ed7-2d62-494e-8835-46b80525bb28)
here Vincm(p-p)=0.1v and differential output voltage is 306.18mv
therefore gain = 3.03
AC ANALYSIS:
here as we have replaced the resistance by MOSFET the GM of each mosfet leads to decrease in gain.
![Screenshot 2025-03-09 103730](https://github.com/user-attachments/assets/19fec686-be6c-4365-88d7-db29cd65e0a8)
avoiding paracetic capacitace
![image](https://github.com/user-attachments/assets/489ce913-4fa4-4862-adcf-5e724cf90386)
3.79-3dB
BW=112.58Hz


RESULT:
![WhatsApp Image 2025-03-09 at 11 09 44_36068f1f](https://github.com/user-attachments/assets/79e1a1cc-7822-4148-b018-55557786348a)


INFERRENCE :
1) varying RD:
   First Circuit (Resistor as Tail Current Source): Since the tail current is not well-regulated, R1 and R2 may need to be increased to compensate for the lower effective current and 
   maintain 𝑉out.
   Second Circuit (Ideal Current Source): The tail current is constant, so no major change in R1 and 𝑅2 is required.
   Third Circuit (MOSFET as Tail Current Source): The MOSFET has some output resistance, which slightly affects the tail current. If the output voltage increases, 𝑅1 and 𝑅2
   should be decreased to bring it back to the desired level. Conversely, if the output voltage drops, increase 𝑅1  and 𝑅2 to maintain balance.
2) varying Vincm:
   there will be a slight variation in Id, as Vincm effects the channel, because of change in Id there will be change in Vo1 
    ID is directly proportional to Vincm Vout is inversly proportional to Id. {[Vo=Vdd-Id*Rd] where Vdd,Rd-constant}.
3) replacing Rss by MOSFET
   by replacing we can get higher gain and better stability as compared to ckt1

