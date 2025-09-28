There are four main architectures:
- [[Monolithic kernels]]
- [[Microkernels]]
- [[Hybrid kernels]]
- [[Unikernels]]


![[Pasted image 20250701120306.png]]

- The choice of architecture has various impacts on performance, safety and interfaces:
- Switching modes is costly: minimizing mode switches improves performance
- Supervisor mode is not safe: minimizing code in supervisor mode improves safety and reliability
- High level interfaces for programmers are in diﬀerent locations depending on the architecture