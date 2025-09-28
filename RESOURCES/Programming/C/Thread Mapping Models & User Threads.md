## 1. Thread Mapping Models

### 1.1 1:1 Model (One-to-One)

- **Description:**  
    Each user thread is mapped to a single kernel thread.
    
- **Threading handled by:**  
    The operating system (OS) — requires OS support.
    
- **Parallelism:**  
    ✓ _True parallelism possible._ Multiple threads can run on multiple CPU cores at the same time.
    
- **Ease of use:**  
    ✓ Threading is straightforward; programmer doesn't need to manage thread scheduling.
    
- **No control over scheduling:**  
    ✗ Programmers can’t directly influence thread scheduling beyond setting priorities/hints; all decisions made by the OS kernel scheduler.
    
- **Examples:**  
    `Pthreads` (C library), most Java Virtual Machines (JVMs).
    
- **Summary:**  
    You gain parallelism but lose low-level control over scheduling.
    

---

### 1.2 N:1 Model (Many-to-One)

- **Description:**  
    All user threads are mapped to a single kernel thread.
    
- **Threading handled by:**  
    User-level runtime/library. The OS only sees one thread (the kernel thread).
    
- **Parallelism:**  
    ✗ _No real parallelism._ Regardless of the number of user threads, only one can be running at a time (since there’s only one kernel thread).
    
- **Scheduling control:**  
    ✓ Full control at user-level; can implement custom scheduling, priorities, etc.
    
- **Reduced context switch overhead:**  
    ~ _Generally lower overhead_ because all context switches are handled in user space (faster than kernel context switches).  
    ~ _However, if a user thread makes a blocking system call, the entire process blocks._
    
- **Examples:**  
    Coroutines in Python, Lua, PHP.
    
- **Summary:**  
    More control and efficiency in some cases, but limited by lack of parallelism and blocking issues.
    

---

### 1.3 N:M Model (Many-to-Many)

- **Description:**  
    Multiple user threads are mapped to multiple kernel threads.
    
- **Threading handled by:**  
    Both the user-level runtime and the OS kernel.
    
- **Parallelism:**  
    ✓ _True parallelism possible._ Multiple kernel threads can run on multiple CPU cores.
    
- **Control over scheduling:**  
    ✓ _Greater flexibility._ User-level scheduler has control over user threads; kernel-level scheduler runs kernel threads.
    
- **Complexity:**  
    ✗ More complex to implement and manage (requires sophisticated runtime).
    
- **Performance issues due to scheduling conflicts:**  
    ✗ _Performance can suffer when user and kernel schedulers make conflicting decisions:_
    
    - If the user-level scheduler assigns a user thread to a kernel thread that is blocked (e.g., waiting on I/O), the user thread also becomes blocked.
        
    - Kernel scheduler might preempt or deprioritize kernel threads regardless of user-level priorities.
        
    - Load imbalance may occur if the runtime scheduler isn’t aware of the actual state of each kernel thread.
        
    - Double scheduling overhead: both user and kernel layers are making independent decisions.
        
- **Typical implementation:**  
    One kernel thread per core, multiple user threads mapped onto them.
    
- **Summary:**  
    Potentially the best of both worlds (parallelism & control), but also the hardest to get right.
    

---

## 2. User Threads and Blocking Operations

- **When multiple user threads share a kernel thread, they share the kernel thread’s state.**
    
- **If a user thread performs a blocking operation (e.g., disk read):**
    
    - All user threads sharing that kernel thread become blocked.
        
    - This can severely limit concurrency and responsiveness.
        

### 2.1 Ways to Avoid Blocking Issues

#### 1. **Use Asynchronous Operations & Wait-Free Algorithms**

- Replace blocking system calls (e.g., I/O) with non-blocking/asynchronous versions.
    
- Can be implemented:
    
    - Explicitly by programmers (increases code complexity).
        
    - Transparently by the runtime or compiler (preferred, but harder to implement).
        
- Examples: `async/await` in modern languages, callback-based I/O.
    

#### 2. **Cooperative Multithreading (Fibers)**

- User threads yield control voluntarily at defined points.
    
- If a thread is about to block, it yields so other threads can continue.
    
- Popular in language-level coroutines and fibers (e.g., Lua, Python’s asyncio, Windows Fibers).
    
- Lower overhead, but relies on well-behaved code (must yield frequently enough).
    

---

## 3. Summary Table

|Model|Parallelism|Scheduling Control|Blocking Issues|Complexity|Examples|
|---|---|---|---|---|---|
|1:1|Yes|No (OS only)|Minimal|Low|Pthreads, JVM|
|N:1|No|Yes (User only)|Severe|Low|Python coroutines, Lua, PHP|
|N:M|Yes|Yes (Both)|Possible|High|Some Haskell runtimes, custom thread libraries|

---

## 4. Notes & Further Reading

- **Obsidian Tags:**  
    `#operating-systems #threads #concurrency #parallelism`
    
- **Useful links:**
    
    - [Wikipedia: Thread (computing)](https://en.wikipedia.org/wiki/Thread_\(computing\))
        
    - [Operating Systems: Three Easy Pieces](https://pages.cs.wisc.edu/~remzi/OSTEP/)
        

