Experiment 6:

design and analyze current mirror circuit as active load in amplifier circuit 

circuit diagram:

![Screenshot 2025-03-22 225118](https://github.com/user-attachments/assets/912cd5a5-e79a-44b0-8d74-bd22a79c1511)

_**FOR DESIGN**_

we need to design current mirroring for Av>10, VDD=1.8 and P<3mV.

total current in the circuit should be ratio of power and Vdd, and total current is sum of reference current and current through M2

that is I(total)=p/VDD

which is equal to 0.555mA

I(total)= Ireff + Ix

for current mirror ratio 1:1

I(total)=2*Iref

therefore Ireff=0.277mA



_**FOR SIMULATION**_

as per the circuit diagram M1 is NMOS and M2 and M3 is PMOS.

for maintaining the stability i am using Vin as half of VDD. for perfect current mirroring the length of the osfet should be large more than 180nm,

so Vdd=1.8V, Vin=0.9V, L(M1,M2,M3)=180nm, Ireff=0.277mA.

now for this values we need to find the value of width(W) of the channel so that we will get exactly Ireff = Ix.

from trial and error it was found to be 2.3717um. for current mirror 1:1.

after simulation we get the below DC operating points 

![Screenshot 2025-03-22 231948](https://github.com/user-attachments/assets/8768a756-53d3-4879-9cd2-fd81a95025ca)

for confirming the results we need to clarify that all the transisters are in saturation region(Vds>=Vov) so i foud the respective values,

![Screenshot 2025-03-22 232234](https://github.com/user-attachments/assets/e3303b1a-4881-4d0a-bf47-5808421894d5)

upon calculations all the transister are in saturation regions. 



for 1:2 current mirror ratio 

the Ireff should be one third of I(total) that is Ireff = 0.185mA.

we need to just double the W of M2 and M3 transister so I(total) will be 0.555mA, Ireff = 0.185mA and due to curret mirror we get Ix double of 0.185mA that is 0.37mA therefore I(total)=0.555mA

so after making the following changes in the circuit we get below results:

![Screenshot 2025-03-22 233613](https://github.com/user-attachments/assets/db38932f-889e-4413-abb7-ac6551cdfd0f)


Now we need to varry L value keeping the aspect ratio constant and analyse the current mirroring 

for L=180nm as we have already deigned Ix = Ireff

for L=500nm we need to calculate the value of W, as we know the aspect ratio(W/L)  that is 13.17 for L=180nm and W=2.3717um.

now for L=500nm, W/L=13.17 

W=6.585um

now we need substitue these value in the simulation for 1:1 current mirroring ratio and see the difference in the current flow 

![Screenshot 2025-03-23 112856](https://github.com/user-attachments/assets/55065a96-4934-4db3-83e6-0825be5305b2)

we can see that there is a slight increase in current which is around 2nA


for L=1um and W/L=13.17 

W=13.17um 

by substituting the values in the simulation for 1:1 current mirroring ratio we get 

![Screenshot 2025-03-23 114222](https://github.com/user-attachments/assets/53a92167-6103-40f9-8ce5-10472853aad1)


now we need to do transient and AC analysis for the circuit with 1:1 current mirroring ratio and find maximum outputswing and Bandwidth.

the below is the results of Transient anlysis

![Screenshot 2025-03-23 120041](https://github.com/user-attachments/assets/f5197d91-08de-42fc-b16b-3a15a693fd6c)

the expected gain was 10V/V, but as per simulation i got 9.3V/V.

9.3V/V = 19.36dB

the below is the result of Ac analysis 

![Screenshot 2025-03-23 120713](https://github.com/user-attachments/assets/05830702-c33b-4d7f-a761-100df7a76661)

as per AC analysis i got 19.5dB 

to find band width we need to find -3dB which is 16.5dB. hence bandwidth is 100nHz to 3.14GHz.

_**RESULT**_

1) Successful Current Mirror Design
2) Impact of Channel Length Modulation:
     For L = 500nm and W = 6.585µm, the mirrored current (Ix) increased by approximately 2nA compared to the reference current.
     For L = 1µm and W = 13.17µm, the mirrored current (Ix) showed a minimal increase compared to the reference current.
3) Transient analysis of the amplifier with the 1:1 current mirror configuration (L=180nm) yielded a voltage gain (Av) of 9.3 V/V (19.36dB), which is slightly below the design Av > 10. 
4) AC analysis showed  a gain of 19.5dB, similat to transient analysis results. The amplifier's bandwidth was determined to be from 100nHz to 3.14GHz, as measured from the -3dB point on the frequency response curve.
   
_**INFERENCE **_

1) **Current Mirror Accuracy and Channel Length:**

The experiment confirms that channel length modulation significantly impacts current mirror accuracy. Longer channel lengths are preferable for better current matching.  
we can se that due channel length modulation and the  difference of Gate voltage (M2 and M3) and output voltage there is small increase when we vary the channel length 

2) we can see when we did 1:2 analysis we saw that there was a slight increase in current Ix which is because we had set Q point for 1:1 by W/L but when we just simply doubled the W for 1:2 the Q point got effected.


_**BONAS PART:**_

Vary the current mirror ratio and analyze current mirroring 

according to the concept if the ratio is 1:1 then Iref = IX. If the ratio is 1:2 then Ix = 2*Ireff which we have already seen throungh simulation 

now lets see what happens if ratio is 2:1. expected relust is Iref = 2*Ix

![Screenshot 2025-03-23 145728](https://github.com/user-attachments/assets/c8a47084-ff9e-451f-80a7-1d1763be5179)

i have kept W=2.3717u(M3) and W=1.18585u(M2 and M1), which shows that Iref is almost double that of Ix

now for ratio 1:3. expected Ix = 3*Iref

![Screenshot 2025-03-23 150153](https://github.com/user-attachments/assets/693aa5ca-2c39-49c5-bcb4-db1c90154830)

i have not changed the W(M3), W=701151(M2 and M3), which shows that Ix is almost three times of Iref

now for 3:1 ratio. expected Iref = 3*Ix

![Screenshot 2025-03-23 150538](https://github.com/user-attachments/assets/5be320d2-551c-48b1-bdc9-fa28d668ee7d)

i have kept W=2.3717u(M3) and W=0.790u(M2 and M1), which shows that Iref is almost three times of Ix

_**RESULT**_
| current mirror ratio | length(M1,M2,M3) | width(M3) | width(M2) | width(M1) | Iref | Ix(calculated) | Ix(simulated) |
|----------------------|------------------|-----------|-----------|-----------|------|----------------|---------------|
| 1:1 | 180nm | 2.3717um | 2.3717um | 2.3717um | 0.277mA | 0.277mA |
| 1:2 | 180nm | 2.3717um | 4.7434um | 4.7434um | 0.277mA | 0.277mA |
