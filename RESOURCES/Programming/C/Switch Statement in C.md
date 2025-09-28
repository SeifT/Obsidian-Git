
The `switch` statement allows you to execute one block of code out of many, based on the value of an expression. It's often used as a cleaner alternative to long chains of `if-else if-else` statements.

---

## **Syntax**

```c
switch (expression) {
    case constant1:
        // code block
        break;
    case constant2:
        // code block
        break;
    ...
    default:
        // code block
}
```

- **`expression`** must evaluate to an integer or character.
    
- **Each `case`** specifies a value to compare to the expression.
    
- The **`default`** case is optional; it's executed if none of the cases match.
    

---

## **Example: Day of the Week**

```c
int day = 4;

switch (day) {
    case 1:
        printf("Monday");
        break;
    case 2:
        printf("Tuesday");
        break;
    case 3:
        printf("Wednesday");
        break;
    case 4:
        printf("Thursday");
        break;
    case 5:
        printf("Friday");
        break;
    case 6:
        printf("Saturday");
        break;
    case 7:
        printf("Sunday");
        break;
    default:
        printf("Invalid day");
}
```

**Output:**

```
Thursday
```

---

## **Key Points**

- The **expression** in `switch(expression)` must be an integer or character type.
    
- **Each `case`** must end with a `break` to avoid "fall-through".
    
- The **`default`** case is optional but recommended for handling unexpected values.
    

---

## **What Happens Without `break`?**

If you **omit `break`**, execution continues into the next case, regardless of its condition. This is called **fall-through**, which is sometimes useful but often leads to bugs.

### **Example: Fall-through Pitfall**

```c
char ch = 'a';

switch (ch) {
    case 'a':
        printf("Good Afternoon\n");
        // No break!
    case 'e':
        printf("Good Evening\n");
        // No break!
    case 'm':
        printf("Good Morning\n");
}
```

**Output:**

```
Good Afternoon
Good Evening
Good Morning
```

> :warning: **Note:** All cases after `'a'` are executed because there are no `break` statements.

---

## **Best Practices**

- Always include a `break` at the end of each case unless you intentionally want fall-through.
    
- Use the `default` case to handle unexpected or invalid input.
    

---

## **When to Use `switch` vs `if-else`?**

- Use `switch` when comparing the same variable to many **constant values** (integers or characters).
    
- Use `if-else` for more complex conditions (ranges, multiple variables, expressions).
    

---

## **Summary Table**

|Feature|switch-case|if-else|
|---|---|---|
|Data Types|int, char (not float)|Any|
|Readability|Clear for many options|Can get messy|
|Fall-through|Possible (w/o break)|Not possible|
|Default case|Yes|Yes (else)|

---

## **Quick Quiz**

**What is the output?**

```c
int num = 2;
switch(num) {
    case 1:
        printf("One");
    case 2:
        printf("Two");
    case 3:
        printf("Three");
    default:
        printf("Default");
}
```

**Answer:**

```
TwoThreeDefault
```

Because there are **no breaks**, execution "falls through" from case 2 to 3 and then to default!

---

If you want to add **syntax highlighting** or more color, many Markdown editors (like Obsidian, Typora, Notion, VS Code) will render `c` code blocks with color. If you have a preferred color style, let me know!

---

Is there anything else you'd like to cover about `switch-case` statements? (E.g., usage in other languages, nested switch, etc.)