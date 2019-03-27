---
title: Lab 6 report
author: Cassidy Siegrist
partner: Ian, Drew
date:
---


Objective
	- The objective of this lab was to understand the different types of Finite State Machines (FSM) and to apply this knowledge into designing a relevant model. 
	
1-1
	- Our task for this part of the lab was to design a sequence detector by implementing the model of a Mealy Finite State Machine using specifically 3 always blocks. While we were able to compile and upload our files to our assigned board, we were unable to create the proper testbench to produce the proper behavioral simulation. The switches 0 (SW0) and 15 (SW15) work as intended but the LED switches still fail to work as intended.   
	
	
Conclusion
	- In conclusion, we were only able to complete a small percentage of the tasks given. While using searching for helpful references online did help marginally and the extension on our due date was in fact helpful, we were unable to find sufficient information to properly implement this finite state machine. For future labs and lectures, more attention should be given to proper understanding and application of verilog syntax.   


module mealy_3processes(
    input clk,
    input reset,
    input ain,
    output reg yout
    );
reg state, nextstate;
 parameter S0=0, S1=1;
reg count[3:0];
always @(posedge clk or posedge reset) // always block to update state
if (reset)
 state <= S0;
else
 state <= nextstate;
 always @(state or ain) // always block to compute output
begin
 yout = 1'b0;
 case(state)
 S0: if(ain)
 yout = 1;
 S1: if(!ain)
 yout = 1;
 endcase
end
always @(state or ain) // always block to compute nextstate
begin
 nextstate = S0;
 case(state)
 S0: if(ain)
 nextstate = S1;
 S1: if(!ain)
 nextstate = S1;
 endcase
end  
endmodule


module mealy_3processestb(
    input clk,
    input reset,
    input ain,
    output yout
    );
endmodule


