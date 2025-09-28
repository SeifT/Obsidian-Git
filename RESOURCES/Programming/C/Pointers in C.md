### Void Pointers (`void *`)

**Definition:**  
A **void pointer** (`void *`) is a special type of pointer in C that can point to any data type. Unlike pointers to a specific type (e.g., `int *`, `char *`), a void pointer does not have a type associated with the data it points to.

**Why use void pointers?**

- To write functions that can accept (or return) pointers to any data type.
    
- Useful in generic programming (e.g., standard library functions like `qsort` and `bsearch` use void pointers).
    
- Common in multithreading APIs, such as pthreads.
    

**Syntax:**

```c
void *ptr;
```

This creates a pointer called `ptr` that can point to any data type.

**Example usage in a function:**

```c
void *fn(void *arg) {
    // Function body
    return NULL; // or another void pointer
}
```

This function takes a void pointer as an argument and returns a void pointer.

**Important notes:**

- You **cannot dereference** a void pointer directly; you must cast it to another pointer type first:
    
    ```c
    int x = 10;
    void *ptr = &x;
    int value = *(int *)ptr; // Cast before dereferencing
    ```
    
- You can assign the address of any data type to a void pointer without casting.
    

**Common use cases:**

- Thread start routines (e.g., with `pthread_create`)
    
- Memory allocation functions (`malloc` returns `void *`)
    
- Functions requiring a generic pointer argument
    

---

**See also:**
- [[Difference between * and & in Pointers]]
- [[Understanding the '*' Operator in C - Pointers, Declarations, and More]]
---
