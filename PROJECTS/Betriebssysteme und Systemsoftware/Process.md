==A process is the abstraction that represents an instance of a running program.==


- Processes contain the set of information required for the program to execute properly:
- Code (the binary representation of the program’s instructions)
- Memory (variables, stack, heap, etc.)
- Registers (instruction pointer, stack pointer, etc.)
- Resources in use (open files, sockets, etc.)

Note: Program ≠ process! The program is the ‘recipe’ (the code) and the process is an execution of the program.

A new process can be created for various reasons:
- A user creates it by starting a new program
- Another process creates it using a process creation system call
- When the system starts

Depending on their purpose, processes can be classified as:
- Foreground processes that interact with the user
- Background processes that run by themselves with no user interaction required7

Most systems keep an association between a process and the process that created it, its parent.
In UNIX-based systems, all processes are linked in this way, creating a process tree.
The root of the tree is init, the first process created when the system boots.
The init process also adopts orphaned processes.

For each process, the OS maintains a process control block (PCB)
![[Pasted image 20250702092858.png]]

Another property of processes is that they are isolated from each other.
They act independently, as if they were running alone on the machine.
They do not share memory, open files, etc.