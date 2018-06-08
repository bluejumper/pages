# Embedded computers

**Embedded computers** can be found in solutions where logic is required as part
of a larger system, involving a microprocessor to conduct this logic.
These larger systems needn't be a computer one. In a car for example, an
*embedded computer* may receive an input as a signal from a peripheral (eg.
handbrake detection, gear in reverse, indicator signal), or from a larger
computer system (ie. a computer that operates a self-driving vehicle), and
implement the logic that is required when that signal is received. After
processing an input signal, the *embedded computer* may then deliver an
appropriate output signal determined by it's implemented logic.

**Embedded computer systems** are designed to run one predetermined application
or a collection of software, and perform in what may be a low-requirement
environment where limits on cost and power are imposed. Such a system isn't
expected to deliver power to demanding peripherals like those found in PCs and
servers where applications may involve disk storage, graphics and high-speed
networking hardware. Their design requirements might not include the need for
that functionality.

The embedded computer system is responsible for it's slice of logic as part
of a larger system. The design of the *embedded computer system* could be
orientated towards *simplicity* or *redundancy*, contributing to it's 
**reliability**; it's purpose could be very important. In other words, the
system is given a job it should do as best as it can. A failure of a PC or
server system vary in impact, and this extendsto an embedded computer system.  
The impact of a Television or Projector failure, is different to one that might
occur in an plane or a *smart door-lock*.

(further)  
[https://en.wikipedia.org/wiki/Reduced_instruction_set_computer]  
[https://riscv.org/]  
[https://riscv.org/risc-v-cores/] \(you will find something useful here)

(insight)  
Do not overlook the power demands of an embedded computer system. In the
appended video, the guy with a swiss accent explores an embedded system design.
This design was geared towards a maximum runtime for the responsibility of
measuring and transmitting a value every two minutes. Giving this
responsibility to the ESP8266 microcontroller atop an ESP12 module (board and
parts accompanying the microcontroller), and a specific coin-cell battery, he
was able to achieve 26 hours of runtime. He also explores variations in design
requirements and responsibility, and I would strongly recommend a watch.  
[https://www.youtube.com/watch?v=IYuYTfO6iOs]
