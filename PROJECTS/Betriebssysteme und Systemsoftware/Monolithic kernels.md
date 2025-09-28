A monolithic kernel provides, in kernel space, a large amount of core features, e.g., process
and memory management, synchronization, file systems, etc., as well as device drivers.

# Characteristics
- Defines a high level interface through system calls
- Good performance when kernel components communicate (regular function calls in
- kernel space)
- Limited safety: if one kernel component crashes, the whole system crashes

Monolithic kernels can be modular and allow dynamic loading of code, e.g., drivers. These are sometimes called *modular monolithic kernels*.

![[Pasted image 20250701115901.png]]