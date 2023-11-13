# Experiment-08- Encoders-and-decoders 
### AIM: 
To implement 8 to 3 Encoder and  3to8 Decoder using verilog and validate its outputs
### HARDWARE REQUIRED:  
PC, Cyclone II , USB flasher
### SOFTWARE REQUIRED:   
Quartus prime
### THEORY 
## Encoders
Binary code of N digits can be used to store 2N distinct elements of coded information. This is what encoders and decoders are used for. Encoders convert 2N lines of input into a code of N bits and Decoders decode the N bits into 2N lines.

1. Encoders –
An encoder is a combinational circuit that converts binary information in the form of a 2N input lines into N output lines, which represent N bit code for the input. For simple encoders, it is assumed that only one input line is active at a time.

As an example, let’s consider Octal to Binary encoder. As shown in the following figure, an octal-to-binary encoder takes 8 input lines and generates 3 output lines.

![image](https://user-images.githubusercontent.com/36288975/171543588-bc0746df-a173-4b35-989e-5fb7d385fe8a.png)
## Figure -01 3 to 8 Encoder 
Implementation –

X = D4 + D5 + D6 + D7
Y = D2 +D3 + D6 + D7
Z = D1 + D3 + D5 + D7 
Hence, the encoder can be realised with OR gates as follows:
![image](https://user-images.githubusercontent.com/36288975/171543740-68403b82-aa93-4c98-9343-f32b14885a2e.png)
## Figure -02 3 to 8 Encoder implenentation 
### Decoders 
A decoder does the opposite job of an encoder. It is a combinational circuit that converts n lines of input into 2n lines of output.

Let’s take an example of 3-to-8 line decoder.
Implementation –
D0 is high when X = 0, Y = 0 and Z = 0. Hence,

D0 = X’ Y’ Z’ 
Similarly,

D1 = X’ Y’ Z
D2 = X’ Y Z’
D3 = X’ Y Z
D4 = X Y’ Z’
D5 = X Y’ Z
D6 = X Y Z’
D7 = X Y Z 
![image](https://user-images.githubusercontent.com/36288975/171543978-ee2d0671-2846-40a1-8705-507fd6287a49.png)
## Figure -03 8 to 3 Decoder 
![image](https://user-images.githubusercontent.com/36288975/171543866-5a6eace6-8683-49d7-9c4f-a7cb30ec3035.png)
## Figure -04 8 to 3 Decoder implementation 
### Procedure

1.Start the module using module projname().

2.Declare the inputs and outputs along with the select lines according to the multiplexer and demultiplexer.

3.Use wire to assign intermediate outputs.

4.Use and, or and not gates to get the desired output.

5.End the module.

6.Generate RTL realization and timing diagrams.

### PROGRAM 
/*
Program for Endocers and Decoders  and verify its truth table in quartus using Verilog programming.
Developed by: KOWSALYA M
RegisterNumber:  212222230069
*/
```
# MULTIPLEXER

module multiplexer(I0,I1,I2,I3,S0,S1,Y);
input I0,I1,I2,I3,S0,S1;
output Y;
wire P,Q,R,S,S0c,S1c;
not(S0c,S0);
nor(S1c,S1);
and(P,S0c,S1c,I0);
and(Q,S0c,S1,I1);
and(R,S0,S1c,I2);
and(S,S0,S1,I3);
or(Y,P,Q,R,S);
endmodule

# DEMULTIPLEXER

module demux(Y0,Y1,Y2,Y3,S0,S1,I);
input S0,S1,I;
output Y0,Y1,Y2,Y3;
wire S0C,S1C;
nor (S0C,S0);
nor (S1C,S1);
and (Y0,I,S0C,S1C);
and (Y1,I,S0C,S1);
and (Y2,I,S0,S1C);
and (Y3,I,S0,S1);
endmodule
```
### RTL LOGIC :
### MULTIPLEXER :
![281362249-3acd724f-778b-4273-8d52-473ef8da773e](https://github.com/Kowsalyasathya/Experiment-08-Encoders-and-decoders-/assets/118671457/f6f23780-acd0-4623-8321-b8306c26195c)
### DEMULTIPLEXER:
![281366644-7616466e-a3ee-4fbe-9666-fba4a22f09ad](https://github.com/Kowsalyasathya/Experiment-08-Encoders-and-decoders-/assets/118671457/5a3b51d2-02a6-42a9-b942-c5a1feb050a1)
### TIMING DIGRAMS:
### MULTIPLEXER :
![281367344-68f79e23-ba07-40f2-b7de-7af918ebba85](https://github.com/Kowsalyasathya/Experiment-08-Encoders-and-decoders-/assets/118671457/b619d53e-3ba7-4f75-bca3-558fde61c68b)
###  DEMULTIPLEXER:
![281367624-0b87433e-8d25-44d3-9301-6a59cf1d94f2](https://github.com/Kowsalyasathya/Experiment-08-Encoders-and-decoders-/assets/118671457/af56803f-901d-4a75-9f3b-701042e57eaa)
### TRUTH TABLE 
### MULTIPLEXER :
![281367824-e97adc77-e0d4-41b1-bcf1-b2e8cf30a065](https://github.com/Kowsalyasathya/Experiment-08-Encoders-and-decoders-/assets/118671457/953baa58-0da3-4433-a8a2-df3eee976e86)
### DEMULTIPLEXER:
![281367880-4172b3ca-6cc8-4009-b572-4e13c6e61351](https://github.com/Kowsalyasathya/Experiment-08-Encoders-and-decoders-/assets/118671457/fabb034d-3cf3-4d21-8955-cd395744b28e)
### RESULTS :
Hence, 4x1 Multiplexer and 1x4 Demultiplexer is been implemented and verified using verilog programming and its output are validated.
