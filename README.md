### SYNCHRONOUS-UP-COUNTER

**AIM:**

To implement 4 bit synchronous up counter and validate functionality.

**SOFTWARE REQUIRED:**

Quartus prime

**THEORY**
~~~
A synchronous up counter is a sequential circuit that counts upward (0,1,2,3…) on every clock pulse.

In this counter, all flip-flops receive the clock signal simultaneously, so they change state at the same time.

The output of one flip-flop acts as a control signal for the next flip-flop in the counting sequence.

The first flip-flop toggles with every clock pulse, while the higher flip-flops toggle only when all lower bits are HIGH.

Because all flip-flops are clocked together, the counter operates faster and avoids propagation delay problems seen in asynchronous counters.

The number of flip-flops determines the maximum count range (n flip-flops → 2ⁿ states).

Synchronous up counters are used in digital clocks, timers, frequency dividers, and many counting applications.
~~~
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
~~~
1.Open New Project Wizard and create a new Quartus project with project name and working directory.

2.Create a new Verilog/VHDL file and write the synchronous up-counter code (n-bit counter).

3.Save the file and set the module/entity name (e.g., up_counter) as the top-level design.

4.Add any required clock/reset constraints and compile the project using Start Compilation.

5.Use Pin Planner to assign FPGA pins to clk, reset, and output bits if you will test on hardware.

6.Run RTL or functional simulation (ModelSim/Quartus Simulator) to verify counting sequence and timing.

7.If hardware testing needed, open Programmer, generate SOF file and program the FPGA to observe the counter.
~~~
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

**RTL LOGIC UP COUNTER**
<img width="2560" height="1347" alt="ex11(1)" src="https://github.com/user-attachments/assets/ab178681-884e-4557-bc2e-b2abcc79379a" />

**TIMING DIAGRAM FOR IP COUNTER**
<img width="2553" height="1303" alt="ex11(2)" src="https://github.com/user-attachments/assets/7fad55a9-8f05-4aeb-bd65-f39a1f77bf62" />

**TRUTH TABLE**

![truth](https://github.com/user-attachments/assets/24067ede-dc00-48be-bc96-e3133c833331)


**RESULTS**
The synchronous up counter was successfully designed and implemented in Quartus 13.0, and the counting operation was correctly verified with all flip-flops toggling simultaneously on each clock pulse.
