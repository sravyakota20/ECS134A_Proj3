# Project 3 README

* Student 1: Varshini Gurushankar (922249127)
* Student 2: Sravya Kota (919987625)

## Project Status
* Started the Project, Finished ADDER15
* Tested, ADDER15 - Test cases work
* Finished ALU15 - Need to test it and check for any miswires
* Finished REG15 - Need to test it and check for any miswires
* Tested ALU 15 - So far no miswiring
* Tested REG15 - No miswiring
* Finished IMM15 - Need to test and check for miswiring
* Finished decoder15 need to debug (I think I missed some logic can't seem to find it asked my partner to look it over)
* Finished CPU need to test for miswires and debug

## Known Issues
* Some kind of logic is wrong with the decoder need to debug/ check for miswires and logic

## References
* [Build an XOR gate from AND/NOT](https://electronics.stackexchange.com/questions/487529/build-an-xor-gate-from-and-not)
* [Some other link](https://stackoverflow.com)

* After failing to understand the purpose of tunnels this video made me understand that (https://www.youtube.com/watch?v=FDL2cpinIEE)
* this really helped me in building the circuit but I changed things in the given circuit accordingly maybe found a better way to build it and stuff like that (https://hackaday.io/project/131983/logs?sort=oldest&utm_)
  

## Generative AI Use

### Prompt 1
How do you create an XOR from only and/or/not gates?

### Response 1
To create an XOR (exclusive OR) gate using only AND, OR, and NOT gates, you can follow these steps. The XOR gate outputs true only when the inputs are different.

The truth table for XOR is:

| A | B | A XOR B |
|---|---|---------|
| 0 | 0 |    0    |
| 0 | 1 |    1    |
| 1 | 0 |    1    |
| 1 | 1 |    0    |

The Boolean expression for XOR can be derived as:\
A &oplus; B = (A &and; &not; B) &or; (&not; A &and; B)

This can be broken down into the following steps:

1. Create \(&not; A\) and \(&not; B\) using NOT gates.
1. Create \(A &and; &not; B\) and \(&not; A &and; B\) using AND gates.
1. Combine the results of the two AND gates using an OR gate.

Here is the step-by-step logic construction:

1. **NOT gates** to get \(&not; A\) and \(&not; B\):\
   NOT(A) &rarr; &not; A\
   NOT(B) &rarr; &not; B

1. **AND gates** to get \(A &and; &not; B\) and \(&not; A &and; B\):\
   A &and; &not; B &rarr; AND(A, &not; B)\
   &not; A &and; B &rarr; AND(&not; A, B)

1. **OR gate** to get the final result:\
   (A &and; &not; B) &or; (&not; A &and; B) &rarr; OR(AND(A, &not; B), AND(&not; A, B))

Putting it all together in a circuit diagram:

1. Input \(A\) goes to a NOT gate to produce \(&not; A\).
1. Input \(B\) goes to a NOT gate to produce \(&not; B\).
1. Input \(A\) and the output of the NOT gate for \(B\) go to an AND gate to produce \(A &and; &not; B\).
1. Input \(B\) and the output of the NOT gate for \(A\) go to an AND gate to produce \(&not; A &and; B\).
1. The outputs of the two AND gates go to an OR gate to produce the final output \(A &oplus; B\).

In terms of Boolean logic:\
XOR(A, B) = \(A &and; &not; B\) &or; \(&not; A &and; B\) 

This way, you have constructed an XOR gate using only AND, OR, and NOT gates.

### Prompt 2
How do branches work in a CPU design?

### Response 2 
Branches rely on three things: a way to compute a new PC target (usually PC + offset), a set of flags from the ALU (Zero, Negative, Overflow, etc.), and a decision unit that checks whether the branch condition is met. If the condition is true, the PC multiplexer selects the branch target; if not, it just continues with PC + 1. The key insight is that all of this happens in parallel, but only one path is committed each cycle.

### Prompt 3
How do I test the CPU with provided .asm files?

### Response 3
Run python3 assembler.py rtype0.asm.

Load rtype0.dat into ROM.

Step through execution in Logisim.

Watch registers update correctly.

### Prompt 4
How do I add extra credit interrupts?

### Response 4
Add SWI instruction: saves PC to stack, jumps to ISR.

Add RTI: restores PC from stack.

SSRF/SSRP to set/restore flags.

Extend PC MUX with ISR vector.

### Prompt 5
How to organize the architecture of a 15-bit ALU? 

### Response 5
Treat the ALU as parallel “candidate” units (adder path + logic paths) feeding a single result bus; use a small OP field decoded to one-hot selects so only one candidate drives the bus at a time; derive flags from the selected result.

### Prompt 6
What is a nice way to get the Z flag on a wide bus? 

### Response 6
Use a small OR/NOR reduction tree instead of a single giant gate to manage fan-in and layout.

### Prompt 7
How should I test ALU to check if it works before integrating it with the CPU?

### Response 7
Do directed tests (zero, max/min, overflow, borrow cases) then sprinkle randomized pairs; verify Z/N/O/C for each.

### Prompt 8
How to implement a CPU decoder without messy gates causing problems in the wiring of the circuit?

### Response 8
Two popular patterns: (a) combinational logic that directly maps opcode→controls, or (b) a tiny control ROM (microcode-ish) indexed by opcode that outputs control fields (ALUOP, ASEL, BSEL, REGW, etc.). ROM keeps things organized and easy to tweak.




### Changes 1
I needed XNOR, so changed it to:\
&not;\(\(A &and; &not; B\) &or; \(&not; A &and; B\)\)

### Changes 2 

I wanted to understand how branches work and realized that the stored FLAGS register helped with comparing the ALU outputs through this information

### Changes 3

Was struggling with testing the CPU, so I needed some assistance

### Changes 4

Wanted to add the extra credit interrupts but ran out of time, so no changes

### Changes 5

Organized ALU into two separate sides, arithmetic vs logic and combined them into one bus

### Changes 6

Used the tree method to make sure wiring and layout is more organized 

### Changes 7

Kinda followed ChatGPT's method, and looked through pdf of assignment to understand how to test. 

### Changes 8

Implemented mini ROMS per field so it breaks it down and organizes the circuit better. It was easier to go back and debug as well once I understood what I was doing and where I was messing up.  













