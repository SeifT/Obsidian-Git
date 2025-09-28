A microkernel contains only the minimal set of features needed in kernel space: address-
space management, basic scheduling and basic inter-process communication.
All other services are pushed in user space as servers: file systems, device drivers, high level interfaces, etc.
# Characteristics
- Small memory footprint, making it a good choice for embedded systems
- Enhanced safety: when a user space server crashes, it does not crash the whole system
- Adaptability: servers can be replaced/updated easily, without rebooting
- Limited performance: IPCs are costly and numerous in such an architecture

![[Pasted image 20250701120050.png]]