I gave a read to the document around 2-3 times and tried to understand what the project I about and mainly what do I have to build .
The initial steps was understanding the electrical power needs of the CubeSat .  Basically calculating the values of the solar input , battery behaviour and the value of other loads .
Below are the points of what I understood in brief and what would be my further approach
•	A CubeSat orbit Earth with repeated sunlight(60 min) and eclipse (30 min) phases.
•	In sunlight , solar panels onboard electronics and charge the battery 
•	In eclipse , no solar power is available , so the battery discharges to keep the system alive.
•	The simulation should show how the battery voltage , current and charge change over these cycles
Since I am not well versed with the software CircuitJs , I needed to do some research over this problem statement as well as the software . To also calculate the desired values of different components as well as understanding the components I have used the help of AI and Google search . Many things sre new to me in this project and I am open , happy and willing to learn new things
So what I did it I put my approach on Ai platforms and asked it if it was correct and told it to correct if things are wrong and add if things have been missed

Resources – Below are the links of the research I have done over this topic and the problem statement in oreder to implement the circuit on circuitjs

Perplexity - https://www.perplexity.ai/search/1-create-the-power-bus-battery-3ibTwQCeSNWhAU1CQkboBg
Chatgpt -1) https://chatgpt.com/share/68baead2-6dcc-8011-a4df-5c1401fee842
2) https://chatgpt.com/share/68baebf5-8a54-8011-be25-c734e30d009a
Youtube - https://youtu.be/cKx952NsPjc?si=RzU6_CjePzXv0DqZ

CIRCUIT – 
Below is a description of the circuit that has been made 
Input Source: The circuit starts with a voltage source in the top left, which delivers the required DC or AC signal for the experiment.
Current Measurement: An ammeter is placed right after the source to measure the total current entering the system.
Series Resistors: Right after the ammeter, there are two very low value resistors (0.1 ohm  and 0.01 ohm), 
Signal Generator: Below the main line, a waveform generator at 11.1mHz inputs a very slow signal into the circuit,.

Current Source Branches (Piecewise-Linear Emulation)
Branch 1:
It consists of a 27 ohm resistor in series with in series with and ac voltage source of max voltage 10V , frequency of and Dual cycle of 
Branch 2:
It consists of a 18 ohm resistor connected in series with and ac voltage source of max voltage of 10V  , frequency of and Dual cycle of 

Extra Time
Troubleshooting Note-
The simulator indicates 2 bad connections, suggesting incomplete wiring or missing ground/reference points, which must be fixed for accurate simulation results
Outline of Improved Approach With Additional Time -
•	With extra time, I would isolate and test each circuit sub-section (battery, solar input, each load branch) individually in CircuitJS. This approach could identify exactly where issues arise,whether in timing logic, switch control, or load configuration.
•	I would document expected waveforms and values for each node ahead of time and compare simulation results step-by-step, making it easier to spot deviations early.
•	If CircuitJS limitations were suspected, I would experiment with alternative components 
•	Additional time would allow consultation of datasheets, simulation manuals, or online support forums for CircuitJS to clarify uncertainties, especially around waveform timing or switch configuration.

Problems Faced during the Project and Solutions 
1)
Problem- Some advanced features (PWL current source) are not directly available or intuitive in CircuitJS.
Solution: Seek workarounds such as using a pulse voltage source with a series resistor. Research and test more detailed settings or custom elements in CircuitJS documentation.
2)
Problem -Ensuring that square wave control signals properly turn on/off the correct branches, especially with variable timing requirements.
Solution - With time, implement manual step-by-step simulation, observe node waveforms with scopes, and iteratively adjust frequency and duty cycle settings for each control signal. Use labeled nodes for clarity.

Failures & Fixes
1)
Problem -  The default current source in CircuitJS lacked the ability to input Piecewise Linear PWL waveforms, confirmed when only a fixed DC current box appeared upon editing.
Fix: Switched to using a pulse voltage source combined with a series resistor to approximate the PWL solar input current profile. Configured the pulse source with correct frequency, duty cycle, and amplitude to simulate sun/eclipse cycles accurately.
2)
Problem -Initially, the resistors representing battery ESR and EPS loss were incorrectly placed in series, leading to impractical circuit paths and simulation errors.
Fix: Repositioned the 0.1 ohm resistors strictly in the battery path and the 0.01 ohm resistor in the solar input branch. This separation better represented the physical ESP architecture and allowed proper current flow and voltage behavior.
3)
Problem - Early simulations showed too high resistance (e.g., 1 kΩ) for EPS loss or ESR resistors, causing unrealistic current readings.
Fix: Updated resistor values to match realistic system parameters (0.1 ohm for battery ESR, 10 ohm for EPS loss in solar path with pulse voltage source), restoring credible current and voltage values.




