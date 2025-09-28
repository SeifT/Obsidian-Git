A unikernel, or library operating system, embeds all the software in supervisor mode.
The kernel as well as all user applications run in the same privileged mode.
It is used to build single application operating systems, embedding only the necessary set
of applications in a minimal image.

# Characteristics
- High peformance: system calls become regular function calls and no copies between
- user and kernel spaces
- Security: attack surface is minimized, easier to harden
- Usability: hard to build unikernels due to lack of features supported
![[Pasted image 20250701120248.png]]