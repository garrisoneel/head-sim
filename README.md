# head-sim

Attempting to recreate the effect of a guitar amp on the raw input signal.

Ideally it will replicate the sound of a valve amp faithfully from just the guitar input signal. [Vintage/Iconic amplifiers](https://www.guitarworld.com/gear/10-most-iconic-guitar-amps) are super expensive and/or rare. By recreating the sound using machine learning, I expect that a closer result can be achieved compared to parameterized models such as those used in modelling amplifiers (which are also prohibitively expensive). The question will be whether the resulting simulation can be run in real time and with minimal delay.

## Process

### Standard

Guitar -> Valve Amp (Vacuum Tube) -> Speaker

### This

Guitar -> PC -> Python [RNN probably] -> Solid State Amp (PC) -> Speaker

Guitar -> MicroController -> FPGA [RNN probably] -> Solid State Amp -> Speaker

## Roadmap

- [x] Make Github repo
  
We are here
***

- [ ] Gather Samples
  - 44.1 KHz, 16 bit
  - [ ] Raw Guitar & Effect Pedal (fixed settings)
  - [ ] Raw Guitar & Amp Head (fixed settings)
  - [ ] Raw Guitar & Effect Pedal (variable settings)
  - [ ] Raw Guitar & Amp Head (variable settings)

- [ ] Develop & Evaluate Processing Techniques (Python)
  - [ ] Float vs entirely 16bit int processing?
  - [ ] ML?
  - [ ] Straight NN
  - [ ] RNN
  - [ ] LSTM
  
- [ ] Implement in Hardware
  - [ ] ADC
    - Teensy ADC?
    - Teensy Audio board? would add record to SD card
      - use stereo input to record two channels at once
    - dedicated ADC?
    - need to retrain with custom ADC
  - [ ] FGPA
    - [Could use Teensy??](https://community.arm.com/developer/ip-products/processors/b/processors-ip-blog/posts/new-neural-network-kernels-boost-efficiency-in-microcontrollers-by-5x)
    - What about rPi or jetson nano?? - delay?
    - [ ] Evaluate Capability/Cost of FPGA
    - [ ] Generate FGPA Code
    - [ ] Evaluate FPGA with software
  - [ ] DAC
    - Teensy Audio Board? test delay.
  - [ ] Interface ADC & FPGA
  - [ ] Interface FPGA & DAC
  - [ ] Power Amp to speaker output

## Links

[teensy protopedal](https://learn.sparkfun.com/tutorials/proto-pedal-example-programmable-digital-pedal/all)  
[teensy guitar shield ($$$)](https://www.tindie.com/products/Blackaddr/arduino-teensy-guitar-audio-shield/)  
[tensorflow on teensy](https://forum.pjrc.com/threads/57441-Tensorflow-on-Teensy)  
[tinyml book](https://tinymlbook.com/)  
[teensy 4 audio shield](https://www.pjrc.com/store/teensy3_audio.html)  
[teensy audio library](https://www.pjrc.com/teensy/td_libs_Audio.html)
