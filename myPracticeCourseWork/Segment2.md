### **session 5**

## computer languages

Machine code "a low-level programming language that instructs a computer's central processing unit (CPU) on how to run programs"
Binary instructions to control the CPU, not really "used" as extremely diffcult to get perfect, Still a vital part as assembly code translates to machine code

https://en.wikipedia.org/wiki/Machine_code - most simple but detailed write up i could find 

Assembly code "a low-level programming language that corresponds to machine language instructions"
A simpler way for a programmer to give instructions to the CPU (machine code)
Still very simple and basic but makes alot more sense than machine code, Still lots of room for improvment still very limited

# High Level Languages
There are many many many high level languages such as C, Java or BASIC
These languages make it a lot easier for programmers to make more complicated programs as its far more readable, managable and maintanable.

https://www.bbc.co.uk/bitesize/guides/z6x26yc/revision/1 - relevant to all things above, explained very simply very quickly, but makes it all make sense!

interpreted languages - Changes to object code one line at a time
Compiled languages - Converts whole code to machine code before running

## Open source vs Closed
 Very simple

 Open source - Openly distrubuted anyone can use
 Closed source - Not openly distrubted can not be re used

 https://www.ibm.com/think/topics/open-source - history of open source
 Three cheers for Richard Stallman!

 ## Subroutines and stacks
A small piece of code that can be called upon over and over by the main program
https://www.bbc.co.uk/bitesize/guides/zh66pbk/revision/7#:~:text=Subroutines%20are%20smaller%2C%20named%20sections,points%20in%20the%20main%20program. once again simple quick but makes sense!

Stacks Store subroutine states, when new data is added the "stack pointer" is pushed to the next open space in the "stack" it can then be removed with a "pop" 

## interrupts

to put it simply, a interrupt interrupts the CPU, Which causing the CPU to jump to a subroutine before returning back to its previous task
for example, A user input from a mouse or keyboard 



### **session 6**

## operating systems
Scheduling "In computing, scheduling is the action of assigning resources to perform tasks. The resources may be processors, network links or expansion cards. The tasks may be threads, processes or data flows." (https://en.wikipedia.org/wiki/Scheduling_(computing))

https://www.youtube.com/watch?v=Jkmy2YLUbUY&ab_channel=JacobSorber Explains it better than i can ever put in any notes

Brief : scheduling is scheduling work for the cpu and deciding what order and when to do it.

## Memory Managment

Virtual memory (Disk Storage that pretends to be ram when not needed) is used when Physical RAM isn't needed at that second so pages are stored in Swap files on the disk until its needed and swapped to RAM.

This solved the issue of limited RAM on earlier PC's although now is less of a issue still good to have to stop crashes etc, also keeps background activited from hogging all ram

"uses both hardware and software to enable a computer to compensate for physical memory shortages, temporarily transferring data from random access memory (RAM) to disk storage."  https://www.techtarget.com/searchstorage/definition/virtual-memory#:~:text=Virtual%20memory%20is%20a%20common,(RAM)%20to%20disk%20storage.

Explained in better terms


## Kernel and user processes

Processes that run at Kernel level and have full access to all the memory in the system

IBM explain it better (funilly enough) https://www.ibm.com/docs/pl/aix/7.1?topic=processes-introduction-kernel


User processes are different in they operate outside of the kernel and are controlled by the kernel in what they can do
 User processes are what 99% of users use every day, e.g browsers.

 ### Session 7

 ## O.S Structure

 O.S = Kernel > Services ran in Kernel space + Utilities ran in User space

 https://www.geeksforgeeks.org/different-approaches-or-structures-of-operating-systems/ Explains kernels and different types of structures with different combos of various kernel types (e.g Monolithic e or micro-kernel)

 Monolithic = Entire O.s Is a Single large process in kernel mode.
 Micro-kernel = remove all Non essential components from kernel and implementing them as user/system programs (smaller kernel) (All on above website^^)

## What is a Kernel

https://www.youtube.com/watch?v=5S-tTDeFZfY&ab_channel=Techquickie Good explanation made quite simple and quick!

Works as a interface between the Physical hardware and the processes running on it.
Also prevents software going where it shouldn't!

## Rest of lesson

was all quite self explanatory e.g UI, permissions, Boot system etc 


### Session 8

Cisco Cyber security (Cert number to follow)










 

 
 

 









