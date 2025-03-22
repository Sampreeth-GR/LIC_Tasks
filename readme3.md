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



