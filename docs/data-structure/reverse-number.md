Program to reverse a decimal number
===================================

SEPTEMBER 29, 2018 ~ SUNIL KUMAR

``` c
/* Program to Reverse a number */
#include <stdio.h>

int reverse_number(int n){
	int out = 0;

	while(n!=0){
		out *= 10;
		out += n%10;
		n /= 10;
	}
	return out;
}

int main() {
	int num=1234;

	printf ("Initial Number=%dn", num);
	printf ("Reverse Number=%dn",reverse_number(num));

	return 0;
}
```
