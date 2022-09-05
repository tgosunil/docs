Program to reverse bits in number
=================================

SEPTEMBER 29, 2018 ~ ADMIN@EMBEDDEDPROGRAMS.COM

``` c
/* Program to Reverse bits in a number */
#include <stdio.h>

/*
* Change NBITS as per your requirment
* NBIT = 1, reverse each bit
* NBIT = 4, reverse the nibble
* NBIT = 8, reverse the bytes
*/

#define NBITS 0x4
#define NBIT_MASK (~(~0 << NBITS))

int reverse_bits(int m){
	int n=0;
	while ( m != 0 ) {
		n <<=NBITS;
		n |= (m & NBIT_MASK);
		m >>= NBITS;
	}

	return n;
}

int main() {
	int num=0x1234;

	printf ("Initial Number=0x%xn", num);
	printf ("Reverse %d bits in Number=0x%xn",NBITS, reverse_bits(num));

	return 0;
}
```
