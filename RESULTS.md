
Even after putting the circuit together carefully, the expected outputs and waveforms aren’t showing 
up. This is usually due to a mix of common simulation and design issues: 
1. Missing or incorrect ground connections 
Every current path needs to return to ground. If a source, load, or switch doesn’t have a clear ground 
reference, current won’t flow. In practice, this shows up as flat-lined or zero waveforms. 
2. Switching or control problems 
MOSFETs and analog switches rely on proper gate drive signals. If the square wave sources aren’t 
connected correctly—or if the gate/control voltage never reaches the required threshold—the 
devices stay off. That means no current will pass through the loads (e.g., TT&C or Payload branches). 
3. Parameter settings 
The timing, duty cycle, or frequency of the control signals might not match the simulation window. If 
the drive signals are out of range, the switches won’t turn on at the right time (or at all). An incorrect 
amplitude can also keep a MOSFET permanently off, leaving the branch open. 
4. Component values or wiring mistakes 
Resistors with unrealistic values, missing ground connections, or accidental open circuits can stop 
current entirely or make the results look odd. The OBC load (55 Ω) in particular needs a solid 
connection to ground—if it floats, it won’t conduct or show any measurable voltage/current. 
5. Scope or probe placement 
Sometimes the circuit is actually working, but the measurement setup hides it. If probes or scopes 
aren’t placed on the correct nodes, or if a meter is missing, the waveforms won’t appear even 
though current is flowing. 
