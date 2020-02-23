# head-sim
Attempting to recreate the effect of a guitar amp on the raw input signal.

Ideally it will replicate the sound of a valve amp faithfully from just the guitar input signal. [Vintage/Iconic amplifiers](https://www.guitarworld.com/gear/10-most-iconic-guitar-amps) are super expensive and/or rare. By recreating the sound using machine learning, I expect that a closer result can be achieved compared to parameterized models such as those used in modelling amplifiers (which are also prohibitively expensive). The question will be whether the resulting simulation can be run in real time and with minimal delay.

## Process:

### Standard: 
Guitar -> Valve Amp (Vacuum Tube) -> Speaker

### This: 
Guitar -> PC -> Python [RNN probably] -> Solid State Amp (PC) -> Speaker

Guitar -> MicroController -> FPGA [RNN probably] -> Solid State Amp -> Speaker

## Roadmap
1. Record time synchronized raw guitar output and amp head output (amp settings fixed).
2. Develop NN & evaluate effectiveness of simulation (python)
3. Record data from (1) and include amp knob values
4. Modify NN to evaluate ability to simulate full amp setting range (python)
5. Evaluate feasibility & cost of porting NN to FPGA
6. Port NN to FGPA, construct hardware for evaluation of realtime/delay.
7. Implement for use with real guitar & speaker (ADC, microcontroller, FGPA, DAC, power amp)
