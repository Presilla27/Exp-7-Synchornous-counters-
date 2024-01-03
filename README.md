# Exp-6-Synchornous-counters - up counter and down counter 
### AIM: To implement 4 bit up and down counters and validate  functionality.
### HARDWARE REQUIRED:  – PC, Cyclone II , USB flasher
### SOFTWARE REQUIRED:   Quartus prime
### THEORY 

## UP COUNTER 
The counter is a digital sequential circuit and here it is a 4 bit counter, which simply means it can count from 0 to 15 and vice versa based upon the direction of counting (up/down). 

The counter (“count“) value will be evaluated at every positive (rising) edge of the clock (“clk“) cycle.
The Counter will be set to Zero when “reset” input is at logic high.
The counter will be loaded with “data” input when the “load” signal is at logic high. Otherwise, it will count up or down.
The counter will count up when the “up_down” signal is logic high, otherwise count down

Since we know that binary count sequences follow a pattern of octave (factor of 2) frequency division, and that J-K flip-flop multivibrators set up for the “toggle” mode are capable of performing this type of frequency division, we can envision a circuit made up of several J-K flip-flops, cascaded to produce four bits of output.
The main problem facing us is to determine how to connect these flip-flops together so that they toggle at the right times to produce the proper binary sequence.
Examine the following binary count sequence, paying attention to patterns preceding the “toggling” of a bit between 0 and 1:
Binary count sequence, paying attention to patterns preceding the “toggling” of a bit between 0 and 1.

Note that each bit in this four-bit sequence toggles when the bit before it (the bit having a lesser significance, or place-weight), toggles in a particular direction: from 1 to 0.



Starting with four J-K flip-flops connected in such a way to always be in the “toggle” mode, we need to determine how to connect the clock inputs in such a way so that each succeeding bit toggles when the bit before it transitions from 1 to 0.

The Q outputs of each flip-flop will serve as the respective binary bits of the final, three-bit count:

 ![image](https://github.com/Presilla27/Exp-7-Synchornous-counters-/assets/155127632/c843c46b-8aa8-4101-add4-c33015d6f494)



## DOWN COUNTER 

As well as counting “up” from zero and increasing or incrementing to some preset value, it is sometimes necessary to count “down” from a predetermined value to zero allowing us to produce an output that activates when the zero count or some other pre-set value is reached.

This type of counter is normally referred to as a Down Counter, (CTD). In a binary or BCD down counter, the count decreases by one for each external clock pulse from some preset value. Special dual purpose IC’s such as the TTL 74LS193 or CMOS CD4510 are 4-bit binary Up or Down counters which have an additional input pin to select either the up or down count mode.


![image](https://github.com/Presilla27/Exp-7-Synchornous-counters-/assets/155127632/ae774787-a4ea-4661-8f06-b058ab842837)



3-bit Count Down Counter
### Procedure
1.Create a new project in Quartus II software.
2.Name the project as uc for upcounter and dc for downcounter.
3.Create a new Verilog HDL file in the project file.
4.Name the module as dc and uc for downcounter and upcounter.
5.Within the module declare input and output variables.
6.Complete the program.
7.End the module.



### PROGRAM 

UP COUNTER :
module uc(clk, A);
input clk;
output reg [2:0]A;
always @(posedge clk)
begin
A[2]=(((A[0])&(A[1]))^A[2]);
A[1]=(A[0])^A[1];
A[0]=A[0]^1;
end
endmodule

DOWN COUNTER :
module dc(clk,A);
input clk;
output reg [2:0]A;
always @(posedge clk)
begin
A[2]=(((~A[0])&(~A[1]))^A[2]);
A[1]=(~A[0])^A[1];
A[0]=1^A[0];
end
endmodule


### RTL REALIZATION;
UP COUNTER DOWN COUNTER  

![image](https://github.com/Presilla27/Exp-7-Synchornous-counters-/assets/155127632/f8f3f453-dfce-48ea-817c-1b4bd7a6bdfc)


DOWN COUNTER 

![image](https://github.com/Presilla27/Exp-7-Synchornous-counters-/assets/155127632/d1cfa42f-d786-4872-bb2f-dddf52143538)


### TIMING DIGRAMS FOR COUNTER  

UP COUNTER :
![image](https://github.com/Presilla27/Exp-7-Synchornous-counters-/assets/155127632/a903618e-dbf3-4b48-9290-eeb46fb56764)

DOWN COUNTER :

![image](https://github.com/Presilla27/Exp-7-Synchornous-counters-/assets/155127632/5dbb531c-14fe-4bb2-af00-2df6ec98c035)


### TRUTH TABLE 

UP COUNTER :

![image](https://github.com/Presilla27/Exp-7-Synchornous-counters-/assets/155127632/2f701859-0462-4ca9-b884-30a37d6d3ace)

DOWN COUNTER :

![image](https://github.com/Presilla27/Exp-7-Synchornous-counters-/assets/155127632/a2f7c48e-aa6e-4338-a434-9ece1f17cc69)


### RESULTS 
By this we have verified the truth table of 3-bit up-counter using verilog.

