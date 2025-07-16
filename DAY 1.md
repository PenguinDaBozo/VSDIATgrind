# Sky130 DAY 1 - Inception of open-source EDA, OpenLANE and Sky130 PDK
## How to talk to computers

### 0 - Introduction to QFN-48 Package, chip, pads, core, die and IPs

A very common Arduino board, yet there's a whole industry that lies within that chip.
<img width="371" height="293" alt="image" src="https://github.com/user-attachments/assets/0a49e86c-5ae0-4750-ad90-fffbb5ea83a8" /><br>

This board can also be described in the form of a block diagram:
<img width="1169" height="786" alt="image" src="https://github.com/user-attachments/assets/9f84f641-6a83-483a-a2df-b5ca90e514c0" /><br>
The center is a processor and around it is all the programs that go into the processor. This is a typical diagram of a board.

But the other stuff ain't that important, so let's dive deeper into the chip. 
<img width="456" height="443" alt="image" src="https://github.com/user-attachments/assets/ffa30fdb-2e30-44f8-b65f-2dacf8c8cece" /><br>
This is a chip or in more technical terms: a package. 

The chip is sitting at the center. Wire bunch connects the pins to the boundary of the chip, which allows signals to travel to the chip. 

<img width="411" height="257" alt="image" src="https://github.com/user-attachments/assets/27edb3b3-3b65-4788-aa43-47074990fb0d" /><br>

PADS: Signal travels through the pads and into the pins and vice versa.
CORE: Place where digital logic sits.
DIE: Silicon that the circuit is fabricated on.

<img width="517" height="275" alt="image" src="https://github.com/user-attachments/assets/59581eb8-a8c5-4f12-b1da-0b3b7a7aaae6" />
The core includes some components like the RISCV SoC, SRAM, adc0, adc1, dac, PLE, and SPI.

All performances depend on the foundry, the place where chips get manufactured. Engineers contact foundries.

Foundry IP's or Intelligent Property: This need some amount of integllegine to build this block.
Macros: Pure digital logic.

