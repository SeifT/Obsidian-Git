### `fork`

```c
pid_t fork(void);
```

- **Purpose:** Creates a new process by duplicating the calling process (copies its PCB and memory).
    
- **Returns:**
    
    - In parent: PID of the new child process.
        
    - In child: `0`
        
    - On error: `-1`
        
- **Common Use:** Parent can track/communicate with child process using PID.
    

---

### `exec[lvpe]` Family

```c
int exec[lvpe](const char *path, const char *arg, ...);
```

- **Purpose:** Replaces the current process image with a new program (`path`).
    
- **Arguments:**
    
    - `path` – Path to the executable to run.
        
    - `arg, ...` – Arguments passed to the new program (list or array).
        
- **Returns:**
    
    - On error: `-1`
        
    - On success: _Does not return_ (new program starts and takes over process).
        
- **Notes:**
    
    - Several variants: `execl`, `execv`, `execle`, `execve`, etc., differing in how they accept arguments/env.
        
    - Typically used after `fork()` to run a different program in the child.
        

---

### `wait`

```c
pid_t wait(int *status);
```

- **Purpose:** Suspends execution of the calling process until a child process terminates or changes state.
    
- **Arguments:**
    
    - `int *status` – OUT: Where exit status or state info is stored (can be `NULL` if not needed).
        
- **Returns:**
    
    - PID of the child process on success.
        
    - `-1` on failure.
        

---

### Example Pattern: Fork-Exec-Wait

```c
pid_t pid = fork();
if (pid == 0) {
    // Child process: Replace with another program
    execl("/bin/ls", "ls", "-l", NULL);
    perror("exec failed"); // Only runs if exec fails
    exit(1);
} else if (pid > 0) {
    // Parent process: Wait for child
    int status;
    wait(&status);
    // Analyze status if needed
} else {
    // Error handling for fork failure
}
```

---

**Tip:**  
Typical pattern: `fork()` → child does `exec*()` → parent uses `wait()` to synchronize.

---

**See also:**
- [[POSIX Thread Functions]]