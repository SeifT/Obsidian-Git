```c
/* copy: copy 'from' into 'to'; assume 'to' is big enough */
void copy(char to[], char from[]) {
    int i = 0;
    while ((to[i] = from[i]) != '\0') {
        ++i;
    }
}
```

Here, the line while ((to[i] = from[i]) != '\0') is actually doing something, not just checking a condition. So you can write assignments inside of conditional loops to write more efficient and clean code.