### SYNCHRONOUS-UP-COUNTER

**AIM:**

To implement 4 bit synchronous up counter and validate functionality.

**SOFTWARE REQUIRED:**

Quartus prime

**THEORY**
##
An Up Counter is a sequential digital circuit that counts numbers in increasing order on every clock pulse.

It uses flip-flops to store binary data.
On each positive clock edge, the count increases by 1 (000 → 001 → 010 → 011 …).

The counter works in a synchronous manner, meaning all flip-flops are triggered by the same clock.

Up counters are mainly used in timers, digital clocks, and event counters.
##
##
A Down Counter is a sequential digital circuit that counts numbers in decreasing order on every clock pulse.

It also uses flip-flops connected together.
On each clock pulse, the count decreases by 1 (111 → 110 → 101 → 100 …).

Like the up counter, it operates as a synchronous circuit when a common clock is used.

Down counters are used in countdown timers and control applications.
##



**4 bit synchronous UP Counter**

If we enable each J-K flip-flop to toggle based on whether or not all preceding flip-flop outputs (Q) are “high,” we can obtain the same counting sequence as the asynchronous circuit without the ripple effect, since each flip-flop in this circuit will be clocked at exactly the same time:

![image](https://github.com/naavaneetha/SYNCHRONOUS-UP-COUNTER/assets/154305477/d5db3fa0-e413-404c-b80e-b2f39d82e7e8)


![image](https://github.com/naavaneetha/SYNCHRONOUS-UP-COUNTER/assets/154305477/52cb61eb-d04b-442d-810c-31185a68410b)

Each flip-flop in this circuit will be clocked at exactly the same time.
The result is a four-bit synchronous “up” counter. Each of the higher-order flip-flops are made ready to toggle (both J and K inputs “high”) if the Q outputs of all previous flip-flops are “high.”
Otherwise, the J and K inputs for that flip-flop will both be “low,” placing it into the “latch” mode where it will maintain its present output state at the next clock pulse.
Since the first (LSB) flip-flop needs to toggle at every clock pulse, its J and K inputs are connected to Vcc or Vdd, where they will be “high” all the time.
The next flip-flop need only “recognize” that the first flip-flop’s Q output is high to be made ready to toggle, so no AND gate is needed.
However, the remaining flip-flops should be made ready to toggle only when all lower-order output bits are “high,” thus the need for AND gates.

**Procedure**
##
PROCEDURE – UP COUNTER (Quartus II 13.0)

Open Quartus II 13.0 software.

Create a New Project Wizard and give project name as Up_Counter.

Select Verilog HDL as the design entry method.

Write Verilog code for synchronous up counter using flip-flops.

Save the file and compile the project.

Open Simulation Tool (ModelSim) and apply clock input.

Observe the output counting in ascending order.

##
##
Open Quartus II 13.0.

Create a new project named Down_Counter.

Choose Verilog HDL as design method.

Write Verilog code for synchronous down counter.

Save and compile the design.

Simulate using ModelSim with clock input.

Observe the output counting in descending order.
##

**PROGRAM**
~~~
UP COUNTER
module ex11(out,clk,rst);
input clk,rst;
output reg [3:0]out;
always @ (posedge clk)
begin
   if(rst)
     out<=0;
   else 
     out <= out+1;
end
endmodule
~~~
~~~
DOWN COUNTER
module ex12(out,clk,rst);
input clk,rst;
output reg [3:0]out;
always @ (posedge clk)
begin
   if(rst)
     out<=0;
   else 
     out <= out-1;
end
endmodule
~~~
**RTL LOGIC UP COUNTER**
<img width="2560" height="1347" alt="ex11(1)" src="https://github.com/user-attachments/assets/ab178681-884e-4557-bc2e-b2abcc79379a" />
<img width="2560" height="1333" alt="ex12(1)" src="https://github.com/user-attachments/assets/1b98b468-7354-480a-b62b-4a8c18528fb9" />


**TIMING DIAGRAM FOR IP COUNTER**
<img width="2553" height="1303" alt="ex11(2)" src="https://github.com/user-attachments/assets/7fad55a9-8f05-4aeb-bd65-f39a1f77bf62" />
<img width="2550" height="1343" alt="ex12(2)" src="https://github.com/user-attachments/assets/2ca315bc-cd0f-4b24-a5ab-2e793e465edb" />


**TRUTH TABLE**

![truth](https://github.com/user-attachments/assets/24067ede-dc00-48be-bc96-e3133c833331)


**RESULTS**
The synchronous up counter was successfully designed and implemented in Quartus 13.0, and the counting operation was correctly verified with all flip-flops toggling simultaneously on each clock pulse.
