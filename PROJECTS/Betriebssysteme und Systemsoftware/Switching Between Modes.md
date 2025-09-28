When applications running in user mode need to use a privileged feature, they have to switch to supervisor mode.

This switching is performed through ==system calls==, which are function calls from user to supervisor mode.

Examples of system calls:
`read()` and `write()` for file manipulation, `listen()`, `send()` and `receive()` for networking

In addition to calling the function, a system call also checks that:
- The program is allowed to perform this request
- The arguments passed by the program are validw