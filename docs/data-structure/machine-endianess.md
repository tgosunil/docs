Program to find machine endianness
==================================

SEPTEMBER 29, 2018 ~ SUNIL KUMAR

``` c
/* Program to find machine endianness */
#include <stdio.h>

int main() {
	int x=0x1;
	char* c= (char *)&x;

	if (*c == 1)
		printf ("Little endiann");
	else
		printf ("Big endiann");

	return 0;
}
```
