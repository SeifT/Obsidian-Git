### `pthread_create`

```c
int pthread_create(
    pthread_t *thread,
    const pthread_attr_t *attr,
    void *(*start_routine)(void *),
    void *arg
);
```

- **Purpose:** Create a new thread that runs `start_routine(arg)`.
    
- **Arguments:**
    
    - `pthread_t *thread` – OUT: Where the thread ID is stored.
        
    - `const pthread_attr_t *attr` – IN: Thread attributes (`NULL` for default).
        
    - `void *(*start_routine)(void *)` – IN: Function the thread will run.
        
    - `void *arg` – IN: Argument to pass to `start_routine`.
        
- **Returns:** `0` on success, error code otherwise.
    

---

### `pthread_exit`

```c
void pthread_exit(void *retval);
```

- **Purpose:** Terminates the calling thread, returning `retval` to any joining thread.
    
- **Arguments:**
    
    - `void *retval` – IN: Value returned to a joining thread.
        
- **Note:**
    
    - Returning from the thread function is equivalent to calling `pthread_exit` with the return value.
        

---

### `pthread_join`

```c
int pthread_join(pthread_t thread, void **retval);
```

- **Purpose:** Waits for the specified thread to finish, optionally retrieving its return value.
    
- **Arguments:**
    
    - `pthread_t thread` – IN: Thread to wait for.
        
    - `void **retval` – OUT: Address to store the thread's return value (or `NULL` if unused).
        
- **Returns:** `0` on success, error code otherwise.
    

---

### Example

```c
void *thread_func(void *arg) {
    int *result = malloc(sizeof(int));
    *result = 123;
    return result;
}

pthread_t tid;
pthread_create(&tid, NULL, thread_func, NULL);

void *ret;
pthread_join(tid, &ret);
printf("Returned: %d\n", *(int *)ret);
free(ret);
```

---

**Tip:**  
For most use cases, pass `NULL` for thread attributes. Use `pthread_join` to wait for threads and collect results.

---

**See also:**
- [[POSIX Process Functions]]