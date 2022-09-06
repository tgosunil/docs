Program to draw diamond pattern
===============================

SEPTEMBER 29, 2018 ~ SUNIL KUMAR 

``` c
#include <stdio.h>

int main() {
	int i,j, N=10;

	for(i=N;i>=1;i--) {
		for(j=1;j<=2*N;j++) {
			if ((j < i) || (j > (2*N-i)))
				printf(" ");
			else
				printf("*");
		}
		printf("n");
	}

	for(i=1;i<=N;i++) {
		for(j=1;j<=2*N;j++) {
			if ((j < i) || (j > (2*N-i)))
				printf(" ");
			else
				printf("*");
		}
		printf("n");
	}
}
```
