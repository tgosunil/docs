Program to find factorial of a given number
===========================================

SEPTEMBER 29, 2018 ~ SUNIL KUMAR

``` c
/*
 * file: factorial.c
 */
#include <stdio.h>

/* function to find factorial of number */
int fact(int n) {
	int i, f=1;

	if ( n > 1 ){
		for (i=n; i !=1 ; i --) {
			f = f * i;
		}
	}

	return f;
}

/* main function */
int main () {
	int num=0;

	printf("Enter number to find factorial: ");
	scanf ("%d", &num);

	printf("Factorial of %d is %dn", num, fact(num));

	return 0;
}
```
### Compilation Steps:
```
$ gcc -o factorial factorial.c
```
### Output:
```
Enter number to find factorial: 7

Factorial of 7 is 5040
```
