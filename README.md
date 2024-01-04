# ModularUltrasonicArrays
Modular hardware and software for generating and amplifiying ultrasonic signals in phased-arrays applications

## General architecture
SignalGenBoard --> AmpBoards --> Array of emitters

## Design choices

### Multiplexing the logic signals
8 logic signals are multiplexed into 1 wire (and a singl  clock+latch for all the signals). This reduces the amount of pins needed in the generator of the SignalGen board and reduces drastically the number of connectors an wires between the SignalGenBoard and the AmpBoards. The disadvantage is the the AmpBoards need shift-registers to demultiplex the signals. Also, the maximum speed of the demux signals has to be lower thus limiting the phase resolution. Generally, with 8 multiplexed signals the frequencies used are 40 kHZ * 32 phase divisions * 8 muxed signals = 10.24 Mhz for the clock signal.

### Arrays have common ground
From the amplification boards, there is only 1 wire per transducer comming out. All the grounds of the transducers are connected with a common ground that connects to a single GND connector (in the Amp board for example). This reduces to half the number of wires going from the AmpBoard to the emitters and simplifies the wiring of the arrays. However, it does not enable push-pull configurations and makes harder to reuse the emitters of the arrays for making other arrays.


### Modular design 
Signal generation, amplification and arrays are separated. This is less compact but more modular and easy to repair. Most researchers do not mind a bulky system.
