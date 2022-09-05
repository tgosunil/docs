Program to set multiple bits
============================

SEPTEMBER 29, 2018 ~ ADMIN@EMBEDDEDPROGRAMS.COM

``` c
/* Write a program to set multiple bits */

#include <stdio.h>

/*
 * Set bits from m to n bits (both inclusive) for value x
 * where x is positive integer number
 * and 31 >= n > m >=0
 */

#define BITMASK_METHOD1(m,n) (((1<<(n-m+1))-1)<<m)
#define BITMASK_METHOD2(m,n) ((~(~0 << ((n) -(m)+1))) << (m))
#define SETBITS(x,m,n) ((x) | (((1<<((n)-(m)+1))-1)<<(m)))

int main() {
	int num1=0, num2=0;

	num1=0x1b;

	num2=SETBITS(num1,3,7);

	printf("num1=0x%x num2=0x%xn",num1 ,num2);

	return 0;
}
```
