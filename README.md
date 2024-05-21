# VLSI-LAB-EXP-4

SIMULATION AND IMPLEMENTATION OF SEQUENTIAL LOGIC CIRCUITS



**AIM:**
 
 
   To simulate and synthesis SR, JK, T, D - FLIPFLOP, COUNTER DESIGN using Xilinx ISE.




**APPARATUS REQUIRED:**


vivado 2023.2



**LOGIC DIAGRAM**



SR FLIPFLOP



![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/77fb7f38-5649-4778-a987-8468df9ea3c3)



JK FLIPFLOP



![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/1510e030-4ddc-42b1-88ce-d00f6f0dc7e6)



T FLIPFLOP



![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/7a020379-efb1-4104-85ee-439d660baa08)



D FLIPFLOP



![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/dda843c5-f0a0-4b51-93a2-eaa4b7fa8aa0)




COUNTER



![image](https://github.com/navaneethans/VLSI-LAB-EXP-4/assets/6987778/a1fc5f68-aafb-49a1-93d2-779529f525fa)


  


**PROCEDURE:**



STEP:1  Start  the Xilinx navigator, Select and Name the New project.



STEP:2  Select the device family, device, package and speed.       



STEP:3  Select new source in the New Project and select Verilog Module as the Source type.                       



STEP:4  Type the File Name and Click Next and then finish button. Type the code and save it.



STEP:5  Select the Behavioral Simulation in the Source Window and click the check syntax.                       



STEP:6  Click the simulation to simulate the program and  give the inputs and verify the outputs as per the truth table.               



STEP:7  Select the Implementation in the Sources Window and select the required file in the Processes Window.



STEP:8  Select Check Syntax from the Synthesize  XST Process. Double Click in the  FloorplanArea/IO/Logic-Post Synthesis process in the User Constraints process group. UCF(User constraint File) is obtained. 



STEP:9  In the Design Object List Window, enter the pin location for each pin in the Loc column Select save from the File menu.



STEP:10 Double click on the Implement Design and double click on the Generate Programming File to create a bitstream of the design.(.v) file is converted into .bit file here.



STEP:11  On the board, by giving required input, the LEDs starts to glow light, indicating the output.




**VERILOG CODE : **

 

DEVELOPED BY : THRISHA G

REGISTER NUMBER : 212221060286



SR FLIPFLOP :



~~~
module srff(s,r,clk,rst,q);
input s,r,clk,rst;
output reg q;
always@(posedge clk)
begin
if(rst==1)
q=0;
else
begin
case({s,r})
2'b00:q=q;
2'b01:q=0;
2'b10:q=1;
2'b11:q=1'bX;
endcase
end
end
endmodule
~~~



JK FLIPFLOP :



~~~
module jkff(j,k,clk,rst,q);
input j,k,clk,rst;
output reg q;
always@(posedge clk)
begin
if(rst==1)
q=0;
else
begin
case({j,k})
2'b00:q=q;
2'b01:q=0;
2'b10:q=1;
2'b11:q=~q;
endcase
end
end
endmodule
~~~



T FLIPFLOP :



~~~
module tff(clk,rst,t,q);
input clk,rst,t;
output reg q;
always @(posedge clk)
begin
if (rst==1)
q=1'b0;
else if (t==0)
q=q;
else
q=~q;
end
endmodule
~~~



D FLIPFLOP :



~~~
module dff(d,clk,rst,q);
input d,clk,rst;
output reg q;
always @(posedge clk)
begin
if (rst==1)
q=1'b0;
else
q=d;
end
endmodule
~~~



UP DOWN FLIPFLOP :



~~~
module updown(clk,rst,updown,out);
input clk,rst,updown;
output reg [3:0]out;
always@(posedge clk)
begin
if (rst==1)
out=4'b0000;
else if(updown==1)
out=out+1;
else
out=out-1;
end
endmodule
~~~



MOD 10 COUNTER :

~~~
module mod(clk,rst,count);
input clk,rst;
output reg[3:0]count;
always @(posedge clk)
begin
if(rst==1 | count==4'b1001)
count <= 4'b0000;
else
count <= count +1;
end
endmodule

~~~




RIPPLE COUNTER :

~~~
module ripplecounter(clk,rst,q);
input clk,rst;
output [3:0]q;
tff tff1(q[0],clk,rst);
tff tff2(q[1],q[0],rst);
tff tff3(q[2],q[1],rst);
tff tff4(q[3],q[2],rst);
endmodule
module tff(q,clk,rst);
input clk,rst;
output q;
wire d;
dff df1(q,d,clk,rst);
not n1(d,q);
endmodule
module dff(q,d,clk,rst);
input d,clk,rst;
output q;
reg q;
always@(posedge clk or posedge rst)
begin
if(rst)
q=1'b10;
else
q=d;
end
endmodule

~~~


OUTPUT WAVEFORM :



 SR FLIPFLOP :



 ![image](https://github.com/thrishag/VLSI-LAB-EXP-4/assets/98105360/ee2c4de7-4c49-4538-ade8-6a20945486bc)




JK FLIPFLOP :



![image](https://github.com/thrishag/VLSI-LAB-EXP-4/assets/98105360/7087e432-c7e1-48db-8dce-99e250f33a96)



T FLIPFLOP :



![image](https://github.com/thrishag/VLSI-LAB-EXP-4/assets/98105360/071946c0-32e4-419c-a1ed-fcd7cfe48e75)



D FLIPFLOP :



![image](https://github.com/thrishag/VLSI-LAB-EXP-4/assets/98105360/f7ff8302-ad09-4958-8988-4d911cd4692c)



UP DOWN COUTER:



![image](https://github.com/thrishag/VLSI-LAB-EXP-4/assets/98105360/80773513-308d-493f-b57c-5992cc565691)



MOD 10 COUNTER :



![image](https://github.com/thrishag/VLSI-LAB-EXP-4/assets/98105360/864e1408-f220-42af-9d58-f0bde065f6ce)



RIPPLE COUNTER :



![image](https://github.com/thrishag/VLSI-LAB-EXP-4/assets/98105360/28ba5c9d-5cf5-4189-8811-afde94e1ef21)









**RESULT :**



Hence SR, JK, T, D - FLIPFLOP, COUNTER DESIGNS are simulated and synthesised using Xilinx ISE.
