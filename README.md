AIM: ** To simulate and synthesis multiplier using vivado

APPARATUS REQUIRED: vivado 2023.1

PROCEDURE:

Open Vivado: Launch Xilinx Vivado software on your computer.

Create a New Project: Click on "Create Project" from the welcome page or navigate through "File" > "Project" > "New".

Project Settings: Follow the prompts to set up your project. Specify the project name, location, and select RTL project type.

Add Design Files: Add your Verilog design files to the project. You can do this by right-clicking on "Design Sources" in the Sources window, then selecting "Add Sources". Choose your Verilog files from the file browser.

Specify Simulation Settings: Go to "Simulation" > "Simulation Settings". Choose your simulation language (Verilog in this case) and simulation tool (Vivado Simulator).

Run Simulation: Go to "Flow" > "Run Simulation" > "Run Behavioral Simulation". This will launch the Vivado Simulator and compile your design for simulation.

Set Simulation Time: In the Vivado Simulator window, set the simulation time if it's not set automatically. This determines how long the simulation will run.

Run Simulation: Start the simulation by clicking on the "Run" button in the simulation window.

View Results: After the simulation completes, you can view waveforms, debug signals, and analyze the behavior of your design. Logic Diagram 2 bit Multiplier
**Logic Diagram**
2 bit Multiplier

![image](https://github.com/navaneethans/VLSI-LAB-EXP-3/assets/6987778/7713750f-65e6-41c0-8082-5005eac4031c)

**4 Bit Multiplier**

![image](https://github.com/navaneethans/VLSI-LAB-EXP-3/assets/6987778/d95215dd-8cf1-4e08-93cc-96adfdd7fbdc)


**Verilog code**
~~~
2 bit Multilpier

module ha(a,b,sum,c);

input a,b;

output sum,c;

xor g1(sum,a,b);

and g2(c,a,b);

endmodule

module bitmultiplier(a,b,c);

input [1:0]a,b;

output[3:0]c;

wire w1;

and g1(c[0],b[0],a[0]);

ha ha1(a[0]&b[1],a[1]&b[0],c[1],w1);

ha ha2(a[1] &b[1],w1,c[2],c[3]);

endmodule
~~~
**Output Waveform**
![image](https://github.com/Desika11/VLSI-LAB-EXP-3/assets/165646570/b6b4778e-106f-4bf8-89b0-22ae71407cde)
![image](https://github.com/Desika11/VLSI-LAB-EXP-3/assets/165646570/6ea6982e-8051-43bb-b434-247edf7e537c)


4 bit multiplier:
~~~

module ha(a,b,c,s);

input a,b;

output s,c;

xor g1(s,a,b);

and g2(c,a,b);

endmodule

module fa(a,b,c,s,carry);

input a,b,c;

output s,carry;

wire w1,w2,w3;

xor g1(w1,a,b);

and g2(w2,a,b);

xor g3(s,w1,c);

and g4(w3,w1,c);

or g5(carry,w3,w2);

endmodule

module bitmultiplier(x,y,z);

input[3:0]x,y;

output[7:0]z;

wire [17:1]w;

and g1(z[0],x[0],y[0]);

ha ha1(x[1]&y[0],x[0]&y[1],z[1],w[1]);

fa fa1(x[2]&y[0],x[1]&y[1],w[1],w[5],w[2]);

fa fa2(x[3]&y[0],x[2]&y[1],w[2],w[6],w[3]);
ha ha2(x[3]&y[1],w[3],w[7],w[4]);

ha ha3(w[5],x[0]&y[2],z[2],w[8]);

fa fa3(w[6],x[1]&y[2],w[8],w[12],w[9]);

fa fa4(w[7],x[2]&y[2],w[9],w[13],w[10]);

fa fa5(w[4],x[3]&y[2],w[10],w[14],w[11]);

ha ha4(w[12],x[0]&y[3],z[3],w[15]);

fa fa6(w[13],x[1]&y[3],w[15],z[4],w[16]);

fa fa7(w[14],x[2]&y[3],w[16],z[5],w[17]);

fa fa8(w[11],x[3]&y[3],w[17],z[6],z[7]);

endmodule
~~~

OUTPUT:
![image](https://github.com/Desika11/VLSI-LAB-EXP-3/assets/165646570/c16ab83e-0c14-40e3-9cb4-696a11ef675f)
![image](https://github.com/Desika11/VLSI-LAB-EXP-3/assets/165646570/552f1e42-5003-4e62-91cb-3e7280c265e5)



**Result**
Hence the 2 bit multiplier and 4 bit multiplier are simulated and synthesised using Vivado 2023.1.


