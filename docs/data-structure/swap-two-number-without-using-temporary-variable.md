Program to swap two number without using temporary variable
===========================================================

SEPTEMBER 29, 2018 ~ ADMIN@EMBEDDEDPROGRAMS.COM

/*

* file: swap_number.c

*/

#include <stdio.h>

/* Swap a number without using temp variable */
void swap(int *a, int *b) {
	*a ^= *b;
	*b ^= *a;
	*a ^= *b;
}

/* main routine */
int main(int argc, char *argv[]) {
	int x=5, y =8;

	printf("nEnter 1st Number: ");
	scanf("%d", &x);

	printf("nEnter 2nd Number: ");
	scanf("%d", &y);

	printf("Before: x=%d, y=%d\n", x,y);
	swap(&x,&y);
	printf("After : x=%d, y=%d\n", x,y);

	return 0;
}
```
### Compilation Steps:
```
$ gcc -o swap_number swap_number.c
```
### Output:
```
Enter 1st Number:34
Enter 2nd Number:43
Before: x=34, y=43
After : x=43, y=34
```
