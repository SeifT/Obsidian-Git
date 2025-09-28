- **C passes function arguments by value**: functions receive _copies_ of variables, not the originals.
    
- **Changes to parameters inside a function do not affect variables in the caller.**
    
- **Arrays are an exception**: passing an array gives the function the _address_ of the first element. Changes to array elements inside the function _will affect_ the original array.
    
- **To modify other variables from a function**, pass a _pointer_ (address) and use it inside the function.
    

### Example

```c
int power(int base, int n) {
    for (int p = 1; n > 0; --n)
        p = p * base;
    return p;
}
// n is a copy; changing it doesn't affect the caller.
```

```c
void setZero(int *x) {
    *x = 0;
}
// Pass the address to modify the original variable.
```

---

|Type|Passed as|Can modify original?|
|---|---|---|
|int, float|Copy|No|
|array|Address|Yes (elements)|

---

_Call by value keeps functions safe from accidental changes, except for arrays and when using pointers._