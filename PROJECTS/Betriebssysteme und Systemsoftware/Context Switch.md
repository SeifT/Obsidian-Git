**Context Switch**

A context switch is performed by the operating system when switching from one running process to another. Here are the steps involved:

1. **Change Process State:**
    
    - Change the state of the currently running process (A) from running to ready.
        
2. **Save Registers:**
    
    - Save the CPU registers into the Process Control Block (PCB) of process A.
        
3. **Load Registers:**
    
    - Copy the registers from the PCB of the next process (B) into the CPU registers.
        
4. **Change Process State:**
    
    - Change the state of process B from ready to running.
        

During a context switch, these steps ensure a smooth transition between processes, allowing the CPU to efficiently execute multiple processes.