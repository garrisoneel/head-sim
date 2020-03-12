# head-sim

Attempting to recreate the effect of a guitar amp on the raw input signal.

Ideally it will replicate the sound of a valve amp faithfully from just the guitar input signal. [Vintage/Iconic amplifiers](https://www.guitarworld.com/gear/10-most-iconic-guitar-amps) are super expensive and/or rare. By recreating the sound using machine learning, I expect that a closer result can be achieved compared to parameterized models such as those used in modelling amplifiers (which are also prohibitively expensive). The question will be whether the resulting simulation can be run in real time and with minimal delay.

## Process 

### Standard

Guitar -> Valve Amp (Vacuum Tube) -> Speaker

### This

Guitar -> PC -> [DNN of some type] -> Solid State Amp (PC) -> Speaker

Guitar -> MicroController -> FPGA [DNN of some type] -> Solid State Amp -> Speaker

## Prototyping

### Sample Recording

Teensy with [audio shield][audioshield] used to record 2-channel 16-bit audio at 44k.1 kHz.
[1.4" taps][mono_tap] and a [stereo splitter][stereo_splitter] to record the input signal into the left channel (0), and the output signal to the right channel (1).
The 

## Iteration 1

After finding [this paper][RR2019], the aim of the first step of this project will be to train it using samples recorded here in order to evaulate the architecture.

### Architecture

![network architecture from Ramirez, Reiss 2019][architecture]

## Roadmap/Options

- [x] Make Github repo

- [ ] Gather Samples
  - 44.1 KHz, 16 bit
  - [x] Raw Guitar & Effect Pedal (fixed settings)
  - [x] Raw Guitar & Amp Head (fixed settings)
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

Relevant paper on NN modelling of audio effects: [Modeling of nonlinear audio effects with end-to-end deep neural networks][RR2019]  
[teensy 4 audio shield][audioshield]  
[teensy audio library][teensy_audio]  
[tensorflow on teensy][teensytf]  
Book on ML on microcontrollers [TinyML][tinyml]  

[teensy protopedal]: https://learn.sparkfun.com/tutorials/proto-pedal-example-programmable-digital-pedal/all

[teensy guitar shield ($$$)]: https://www.tindie.com/products/Blackaddr/arduino-teensy-guitar-audio-shield/

[teensytf]: https://forum.pjrc.com/threads/57441-Tensorflow-on-Teensy  

[tinyml]: https://tinymlbook.com/
  
[teensy_audio]: https://www.pjrc.com/teensy/td_libs_Audio.html

[architecture]: ./figures/NN_arch.png "Network Architecure"

[RR2019]: https://arxiv.org/pdf/1810.06603.pdf

[audioshield]: https://www.pjrc.com/store/teensy3_audio.html

[stereo_splitter]: https://www.amazon.com/gp/product/B005HGM1D6

[mono_tap]: https://www.amazon.com/gp/product/B000068O53/

