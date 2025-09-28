C arrays represent a continuous block of memory which is used to store a fixed number of elements of the same data type. The following
int a[10];
declares an array containing 10 elements, each one is of type int. C does not have any own data type for strings, so strings are represented as an array of char, which ends with the character \0 (strings are null terminated).

So the string
char s[11];
contains 11 characters in total, including the terminating character \0. Strings can be initialized in the variable declaration, for example:
char s[11] = " helloworld";

When arrays are directly initialized in the declaration, the compiler can deduce and assign its length automatically.
char s[] = " helloworld " ;

It is possible to access the elements of an array directly by using its index position. For example:
a[2] = 13;