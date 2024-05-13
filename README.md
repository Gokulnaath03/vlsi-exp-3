# vlsi-exp-3

#SIMULATION AND IMPLEMENTATION OF MULTIPLIER:

#AIM:

 To simulate and synthesis multiplier using VIVADO.

 #APPARATUS REQUIRED:

 VIVADO 2023.2

#PROCEDURE:

STEP:1 Start the Vivado, Select and Name the New project.
STEP:2 Select the device family, device, package and speed.
STEP:3 Select new source in the New Project and select Verilog Module as the
Source type.
STEP:4 Type the File Name and Click Next and then finish button. Type the code
and save it.
STEP:5 Select the Behavioural Simulation in the Source Window and click the check
syntax.
STEP:6 Click the simulation to simulate the program and give the inputs and verify
the outputs as per the truth table.



#2-BIT MULTIPLIER:

![image](https://github.com/Gokulnaath03/vlsi-exp-3/assets/167178811/ed593f34-809d-4ffa-962b-f035f52820ea)

#PROGRAM:

module ha(a,b,s,carry);
input a,b;
output s,carry;
assign carry=a&b;
endmodule
module multiplier_2(a,b,c);
input [1:0]a,b;
output [3:0]c;
wire w;
assign c[0]=a[0]&b[0];
ha h1(a[0]&b[1],a[1]&b[0],c[1],w);
ha h2(a[1]&b[1],w,c[2],c[3]);
endmodule

#OUTPUT:

![image](https://github.com/Gokulnaath03/vlsi-exp-3/assets/167178811/7c98dbcc-98fa-4f12-8569-cf1aea46406d)

#4-BIT MULTIPLIER:

![image](https://github.com/Gokulnaath03/vlsi-exp-3/assets/167178811/a5a2d057-c3d6-475b-8c81-3e5fe30fa67c)


#PROGRAM:

module ha(a,b,sum,carry);
input a,b;
output sum,carry;
assign sum=a^b;
assign carry=a&b;
endmodule
module fa(a,b,c,sum,carry);
input a,b,c;
output sum,carry;
assign sum=a^b^c;
assign carry=(a&b)|(b&c)|(a&c);
endmodule
module multi_4(a,b,p);
input[3:0]a,b;
output [7:0]p;
wire [17:1]w;
assign p[0]=a[0]&b[0];
ha h1(a[1]&b[0],a[0]&b[1],p[1],w[1]);
fa f1(w[1],a[2]&b[0],a[1]&b[1],w[2],w[3]);
fa f2(w[3],a[3]&b[0],a[2]&b[1],w[4],w[5]);
ha h2(a[3]&b[1],w[5],w[6],w[7]);
ha h3(a[0]&b[2],w[2],p[2],w[8]);
fa f3(w[8],a[1]&b[2],w[4],w[9],w[10]);
fa f4(w[10],a[2]&b[2],w[6],w[11],w[12]);
fa f5(w[12],w[7],a[3]&b[2],w[13],w[14]);
ha h4(a[0]&b[3],w[9],p[3],w[15]);
fa f6(w[15],a[1]&b[3],w[11],p[4],w[16]);
fa f7(w[16],a[2]&b[3],w[13],p[5],w[17]);
fa f8(w[17],w[14],a[3]&b[3],p[6],p[7]);
endmodule


#OUTPUT:

![image](https://github.com/Gokulnaath03/vlsi-exp-3/assets/167178811/29696d5d-e8b8-4214-8c03-4930f9437233)

#RESULT:

The simulate and synthesis multiplier using VIVADO is successfully verified.
