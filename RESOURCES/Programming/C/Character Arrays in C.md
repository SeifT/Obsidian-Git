- **Most common array type in C:** Character array (used for strings).
    
- **Program example:** Reads multiple lines of text and prints the longest one.
    
    - Uses three pieces:
        
        1. `getline` — reads a line of input
            
        2. `copy` — copies a line
            
        3. `main` — controls the process
            

### Function Declarations & Communication

- **Functions are declared at the top** (e.g., `int getline(char s[], int lim);`, `void copy(char to[], char from[]);`).
    
- **main and getline communicate via:**
    
    - Arguments: character array (for input) and integer (for max size)
        
    - Return value: length of line read (`int`)
        
- **Size of character array:**
    
    - Provided in `main` (e.g., `char line[MAXLINE];`)
        
    - Not needed in `getline` itself
        
- **Return types:**
    
    - `getline` returns `int` (line length or 0 for EOF)
        
    - `copy` returns `void` (used only for its effect)
        

### String Handling

- **Strings in C:** Character arrays ending with `'\0'` (null character)
    
- **`getline` adds `'\0'`** at the end of each line to mark the string’s end
    
- **String constants** (e.g., `"hello\n"`) are stored with `'\0'` at the end automatically
    
- **printf with `%s`** expects a null-terminated string
    

### `copy` Function

- Copies characters from `from[]` to `to[]` **including the terminating `'\0'`**
    

### Error and Limit Handling

- **Potential issue:** What if the input line is longer than the array limit?
    
    - `getline` **stops safely** when the array is full (even without a newline)
        
    - `main` could check if the last char is `'\n'` to detect an overflow
        
    - This sample code omits handling long lines for simplicity
        
- **`getline` checks for overflow** (protects against overfilling the array)
    
- **`copy` does not check size:** Assumes destination array is large enough
    

---

**Summary:**

- Use functions to keep code modular and clear.
    
- Character arrays represent strings, always null-terminated in C.
    
- Always be aware of buffer sizes and potential overflow, especially when reading input.
    

---

Let me know if you want code snippets or diagrams included!