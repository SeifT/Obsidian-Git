**Process Memory Layout Overview:**

- **Kernel Memory:** Shared among all processes, accessible in supervisor mode only.
    
    - **32-bit Linux:** 1 GB for kernel, 3 GB for user space.
        
    - **64-bit Linux:** 128 TB for both kernel and user space.
        
- **Text:** Program binary instructions executed by the CPU.
    
- **Data:** Static initialized variables (global, static local, constant strings).
    
- **BSS (Block Starting Symbol):** Static uninitialized variables.
    
- **Heap:** Dynamically allocated memory (e.g., malloc(), brk/sbrk, mmap()), grows upwards.
    
- **Stack:** Local variables, environment variables, calling context (stack frame), grows downwards.
    
