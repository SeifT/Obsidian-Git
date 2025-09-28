So, to be very sure, setting up a visualization for a simple page table without levels vs. a multilevel page table, specifically 2-level. 

Let's look at a 32-bit system, so let the address space size be 4GiB. The Page size 4KiB. The physical memory is 2GiB. Therefore the number of pages is 1048576. The number of page frames is 524288. If I understand correctly, each process is then given a whole address space, so 4GiB, which is huge. 

Single Page Table: 
With 2 GiB of physical memory, we have a page frame number with 19 bits (2^31/2^12). And assume for metadata we use 12 bits, then we have 31 bits in total for the page table. 31 bits \times 1048576 pages = 31MiB 

Multilevel page table: 
Instead of using all 


Question here is: Including the main process, how many processes are created when executing this program?

The answer is 8. But let me verify my understanding of why.

The main process is the first one.

Then at the first iteration through the for loop (i=0), we create one child process. So we have two processes, say main with PID 254, then we have a child process with id 255 in the parent.

Since in the for loop we are in the child process, we print