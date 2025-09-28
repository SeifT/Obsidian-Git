User domain (also referred to as U mode) has the lowest privilege level.

Programs running in this domain cannot:
- Use privileged instructions that modify the system state,
	- e.g., directly manipulate a hardware device
- Access some memory areas,
	- e.g., access the memory of another program

==This domain is used by all the applications outside of the kernel: high level operating system services and user applications.==
