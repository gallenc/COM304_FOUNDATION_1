[Main Menu](../../sessions/README.md) | [session5](../session5/) | [Introduction to CPULator](../docs/IntroToCPULator.md)

# Introduction to ARM Assembler and C programming using CPUlator

In this section we will introduce programming an ARM processor using a simulator before looking at applying this to the Raspberry PI in the next session.

[CPULator](https://cpulator.01xz.net/) is a free CPU simulator for teaching use written in 2016 by [Henry Wong](https://www.stuffedcow.net/teaching) when he was doing his PhD at the University of Toronto. 

CPUlator is a simulator and debugger of a computer system (CPU, memory, and I/O devices) that runs inside a web browser. 
Simulation allows running and debugging programs without needing to use a hardware board.

CPULator can be used to simulate an ARM 7 processor which is similar to the processor used in the Raspberry Pi.
Although running much slower than a real CPU, the simulation is completely accurate and allows small programs to be writen and run as if they were running on real hardware.

Open a browser and browse to [https://cpulator.01xz.net/?sys=arm-de1soc](https://cpulator.01xz.net/?sys=arm-de1soc)

You will see a screen similar to the image below.

![alt text](../docs/images/CPUlator1.png "Figure CPUlator1.png")

## ARM Registers

THE full [ARM 7 documentation](https://developer.arm.com/documentation/ddi0406/latest/) is very complex, but we shall simplify it here.

On the left pane, you will see the ARM7 registers. 

The ARM architecture provides sixteen 32-bit general purpose registers (R0-R15) for software use. 

In addition the CSPR and SPSR store the results of previous operations in individual bits.

| name               | function                        |
|:-------------------|:--------------------------------|
|R13 (SP)            | Stack Pointer                   |
|R14 (LR)            | Link Register<BR>LR is link register used to hold the return address for a function call.                   |
|R15 (PC)            | Program Counter whose value is altered as the core executes instructions. An explicit write to R15 by software will alter program flow. |
|CPSR                | Current Program Status Register<BR>N, bit [31] Negative condition flag. Set to 1 if the result of the last flag-setting instruction was negative.<BR>Z, bit [30] Zero condition flag. Set to 1 if the result of the last flag-setting instruction was zero, and to 0 otherwise. A result of zero often indicates an equal result from a comparison.<BR>C, bit [29] Carry condition flag. Set to 1 if the last flag-setting instruction resulted in a carry condition, for example an unsigned overflow on an addition.<BR>V, bit [28] Overflow condition flag. Set to 1 if the last flag-setting instruction resulted in an overflow condition, for example a signed overflow on an addition. |
|SPSR                | Saved Program Status Register  a saved copy of the CPSR from the previously executed mode   |
|                    |                                 |


## Memory Mapped peripherals

On the right hand pane you will see a representation of each of the peripherals. 

As in most computers, the control registers for each peripheral are mapped into memory which can be accessed by the CPU.

In this simulator, each peripheral has a different address range and the peripheral is controlled by saving date into an address for the device.

```
Address range       Size    IRQ Name
00000000–3fffffff   1   G       DDR3 SDRAM (HPS)    
c0000000–c3ffffff   64  M       SDRAM   
c8000000–c803ffff   256 K       SRAM (Pixel buffer) 
c9000000–c9001fff   8   K       SRAM (Character buffer) 
ff200000–ff20000f   16          LEDs    
ff200020–ff20002f   16          Seven-segment displays  
ff200030–ff20003f   16          Seven-segment displays  
ff200040–ff20004f   16          Switches    
ff200050–ff20005f   16      73  Push buttons    
ff200060–ff20006f   16      11  Parallel port   
ff200070–ff20007f   16      12  Parallel port   
ff200100–ff200107   8       79  PS/2 keyboard or mouse  
ff200108–ff20010f   8       89  PS/2 keyboard or mouse  
ff201000–ff201007   8       80  JTAG UART   
ff202000–ff20200f   16      72  Interval Timer  
ff202020–ff20202f   16      74  Interval Timer  
ff203020–ff20302f   16          Video DMA Control (Pixel buffer)    
ff203030–ff20303f   16          Video DMA Control (Character buffer)    
ff203040–ff20304f   16      78  Audio (8 kHz)   
ff203060–ff20306f   16          Video-in control    
ff204000–ff20401f   32          ADC 
ff211020–ff211027   8       75  Carworld UART   
ffd02000–ffd02017   24      203 HPS L4 Watchdog Timer   
ffd03000–ffd03017   24      204 HPS L4 Watchdog Timer   
fffec100–fffec113   20          ARM Generic Interrupt Controller    
fffec600–fffec60f   16      29  Cortex-A9 Private Timer 
fffec620–fffec637   24      30  Cortex-A9 Watchdog Timer    
ffff0000–ffffffff   64  K       On-chip SRAM    
```

We are only going to play with the JTAG UART, the VGA display and the seven segment numbers.

## Exercise Running our first C program

Open the [CPULator ARM 7 simulator](https://cpulator.01xz.net/?sys=arm-de1soc) and paste the following C program in the Editor window.

```
#include <stdio.h>
int main() {
   // printf() displays the string inside quotation
   printf("Hello, World!");
   return 0;
}
```

Set the language button to `C` and press `Compile and Load`

After a few seconds, you will see `Compile Succeeded¬ in the Messages window

You will also see a `Disassembly` of the compiled C code in the Disassembly widow. 
This represents the compiled object code as it is located in the simulator's memory.

You will note that the simple program has created a lot of Assembler code

At the top of the CPUlator, you will see commands to run the program.

`Step Into` - runs one machine code instruction and pauses. 
You can look at the changes in registers and memory at each step.

`Continue` - runs the entire program until its end or until a `breakpoint` is encountered.

You can set breakpoints in the assembly code by clicking on the panel beside the Address of the instruction where you want to pause.
Try using these to pause your program and see what is in the registers and memory at each point.

Click `continue` and look at the output in the JTAG Uart window - which is actually simulating a terminal.

You should see "Hello, World!"

The GPULator disassembly window shows us all of the corresponding machine code which has been put in memory by the linker which also includes all of the assembly code to drive the printf function.

We can see the relevant translation of our program if we search for the `_main` lable

![alt text](../docs/images/HelloWorldDissassembly1.png "Figure HelloWorldDissassembly1.png")

I have added comments below so help you understand the assembly program.

```
push {r4, lr}               // at the start of the function call push r4 and lr Link Register onto the stack
movw r0, #30316 ; 0x766c    // fill bottom 16 bits of 32 bit register with 0x766c
movt r0, #1 ; x0x1          // fill top 16 bits of 32 bit register with 0x1  (so r0 points to address 0x1766c )
bl 0x8ab0 (0x8ab0: printf)  // call printf function
mov r0 #0 ; 0x0             // clear r0 (this is the return value 0 )
pop {r4,pc}                 // restore r4 and jump to next instruction which was in link register
```

If we look at memory location 0x1766c we can see it contains the string "Hello, world".

![alt text](../docs/images/HelloWorldDissassembly2.png "Figure HelloWorldDissassembly2.png")

## The same thing in assembler

We can see that the compiler has compiled our program into assembler.

The high level code is very easy to understand while the assembled code is much more difficult to follow.

However, raw assembler is still used because of its speed and small memory footprint (particularly important for small devices).

You also obviously need to understand assembler if you are writing compilers or interpreters.

I have provided some complete assembler examples including one which writes to the UART directly without using the printf function.

Try the exercises in [Assembler Examples](../docs/ASsemblerExamples) before moving on.

