# `&c` — “Address of c”
- `&c` means **“the memory address of c”**.
    
- It gives you a pointer (an address) to where the variable `c` lives in memory.
    
- You use `&` when you want to create a pointer to `c`, or pass `c` by reference to a function.
**Example:**

```c
int c = 42;
int *p = &c; // p is now a pointer to c
```

- `p` holds the address of `c`.
    

---

## `*c` — “Value pointed to by c” (Dereferencing)

- `*c` means **“the value stored at the address c points to”**.
    
- You use `*` to **dereference a pointer**—that is, get the value at the address stored in the pointer.
    

**Example:**

```c
int c = 42;
int *p = &c; // p points to c
int value = *p; // value is now 42
```

- `*p` gives you the value that `p` points to, which is `42` (the value of `c`).
    

---

## Quick Analogy

- If `c` is your house,
    
    - `&c` is your house’s address.
        
    - `*p` (where `p = &c`) is looking up the house **at a given address**.
        

---

## Visual Table

|Symbol|Meaning|Example|What it returns|
|---|---|---|---|
|`&c`|Address of variable `c`|`&c`|Pointer to `c` (address)|
|`*p`|Value pointed by pointer `p`|`*p`|Value at address in `p`|

---

### TL;DR

- `&c` = “Where is c?” (address)
    
- `*c` = “What is stored at the place c points to?” (value at address)
    

Let me know if you want a small demo or another analogy!