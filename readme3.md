# Experiment 6:
# PART-A
design and analyze current mirror circuit as active load in amplifier circuit 

## circuit diagram:

![Screenshot 2025-03-22 225118](https://github.com/user-attachments/assets/912cd5a5-e79a-44b0-8d74-bd22a79c1511)

## _**FOR DESIGN**_

we need to design current mirroring for Av>10, VDD=1.8 and P<3mV.

total current in the circuit should be ratio of power and Vdd, and total current is sum of reference current and current through M2

that is I(total)=p/VDD

which is equal to 0.555mA

I(total)= Ireff + Ix

for current mirror ratio 1:1

I(total)=2*Iref

therefore Ireff=0.277mA



## _**FOR SIMULATION**_

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

# _**RESULT**_

1) Successful Current Mirror Design
2) Impact of Channel Length Modulation:
     For L = 500nm and W = 6.585µm, the mirrored current (Ix) increased by approximately 2nA compared to the reference current.
     For L = 1µm and W = 13.17µm, the mirrored current (Ix) showed a minimal increase compared to the reference current.
3) Transient analysis of the amplifier with the 1:1 current mirror configuration (L=180nm) yielded a voltage gain (Av) of 9.3 V/V (19.36dB), which is slightly below the design Av > 10. 
4) AC analysis showed  a gain of 19.5dB, similat to transient analysis results. The amplifier's bandwidth was determined to be from 100nHz to 3.14GHz, as measured from the -3dB point on the frequency response curve.
   
# _**INFERENCE **_

1) **Current Mirror Accuracy and Channel Length:**

The experiment confirms that channel length modulation significantly impacts current mirror accuracy. Longer channel lengths are preferable for better current matching.  
we can se that due channel length modulation and the  difference of Gate voltage (M2 and M3) and output voltage there is small increase when we vary the channel length 

2) we can see when we did 1:2 analysis we saw that there was a slight increase in current Ix which is because we had set Q point for 1:1 by W/L but when we just simply doubled the W for 1:2 the Q point got effected.


# _**BONUS PART:**_

Vary the current mirror ratio and analyze current mirroring 

according to the concept if the ratio is 1:1 then Iref = IX. If the ratio is 1:2 then Ix = 2*Ireff which we have already seen throungh simulation 

now lets see what happens if ratio is 2:1. expected relust is Iref = 2*Ix

![Screenshot 2025-03-23 145728](https://github.com/user-attachments/assets/c8a47084-ff9e-451f-80a7-1d1763be5179)

i have kept W=2.3717u(M3) and W=1.18585u(M2 and M1), which shows that Iref is almost double that of Ix

now for ratio 1:3. expected Ix = 3*Iref

![Screenshot 2025-03-23 150153](https://github.com/user-attachments/assets/693aa5ca-2c39-49c5-bcb4-db1c90154830)

i have not changed the W(M3), W=7.1151u(M2 and M3), which shows that Ix is almost three times of Iref

now for 3:1 ratio. expected Iref = 3*Ix

![Screenshot 2025-03-23 150538](https://github.com/user-attachments/assets/5be320d2-551c-48b1-bdc9-fa28d668ee7d)

i have kept W=2.3717u(M3) and W=0.790u(M2 and M1), which shows that Iref is almost three times of Ix

# _**RESULT**_
| current mirror ratio | length(M1,M2,M3) | width(M3) | width(M2) | width(M1) | Iref | Ix(calculated) | Ix(simulated) |
|----------------------|------------------|-----------|-----------|-----------|------|----------------|---------------|
| 1:1 | 180nm | 2.3717um | 2.3717um | 2.3717um | 0.277mA | 0.277mA | 0.277002mA |
| 1:2 | 180nm | 2.3717um | 4.7434um | 4.7434um | 0.185mA | 0.37mA | 0.3825mA |
| 2:1 | 180nm | 2.3717um | 1.18585um | 1.18585um | 0.277mA | 0.1385mA | 0.144484mA |
| 1:3 | 180nm | 2.3717um | 7.1151um | 7.1151um | 0.277mA | 0.831mA | 0.806682mA |
| 3:1 | 180nm | 2.3717um | 0.790um | 0.790um | 0.277mA | 0.0923mA | 0.100205mA |






-----------------------------------------------------------------------------------------------------------------------------------------------------------------


# PART-B
DESIGN THE DIFFERENTIAL AMPLIFIER WITH THE SAME DESIGN SPECIFICATION AS EXPERIMENT 3 AND PERFORM DC TRANSIENT AND AC ANALYSIS.

# CIRCUIT DIAGRAM:

![Screenshot 2025-03-23 175624](https://github.com/user-attachments/assets/6ad54d0b-8884-4b6b-bf93-b29714905c44)

## DC analysis

![Screenshot 2025-03-23 175813](https://github.com/user-attachments/assets/8dd1a9d0-7acc-4aa3-8e24-0c95fdc6a551)

as per the parameters of the differential amplifier Vdd = 1.8V, Id(M1 and M2)=0.499mA, Vout = 1.7V and as per the circuit question current mirror ratio of M3 amd M4 1:2.

to get current Id(M3) = 0.899 we need to give Iref =0.499mA
keeping L=180nm constant for all the mosfet for perfect current mirroring, by trial and error width was found to be W(4) = 3.5um, W(3) = 7um. W3 is double the W4 because we need to double increase the Id(M3).

after designing the M3 and M4 we need to design the value of M1 and M2 keeping the value of L=180nm, W(M1 and M2) was found to be 90um.

afer designing the M1 and M2 now we need to design the value of M11 and M22 in such a way that we need to mach the out put parameter 1.7V and it was found to 2.205um. 
## Transient anlysis 

![Screenshot 2025-03-23 175956](https://github.com/user-attachments/assets/666b3d5a-e295-4224-9495-87fec7144493)

gain = 57 V/V =35.11dB
## AC anlysis 

![Screenshot 2025-03-23 180205](https://github.com/user-attachments/assets/4d682983-b02a-4de7-a52e-e0a2e9492b8b)

The higher-than-expected gain suggests the circuit might have additional gain contributions from parasitic effects or device mismatches.

The high bandwidth (100mHz to 504MHz) confirms that the amplifier can operate in high-frequency applications.

The gain deviation could also be due to underestimation of drain resistance or transconductance variations.

