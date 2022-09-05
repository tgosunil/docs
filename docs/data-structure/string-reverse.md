Program to reverse input string
===============================

SEPTEMBER 29,2018 ~ ADMIN@EMBEDDEDPROGRAMS.COM

/*

* file: strrev.c

*/

``` c
/* Program to reverse string */
#include <stdio.h>

/* Declarations */
void swap(char *s, char *d) ;
int xstrrev(char *);

int main(int argc, char *argv[]) {
	int res=0;
	char *str=argv[1];

	if (argc < 2 ) {
		printf("Invalid argumentn");
		printf("Usage: %s <string> n", argv[0]);
		return -1;
	}

	printf("Input String: %sn", str);
	res = xstrrev(str);
	printf("Reverse String : %sn", str);

	return 0;
}

void swap(char *s, char *d) {
	char t;
	t = *s;
	*s= *d;
	*d = t;
}

int xstrrev(char *str) {
	int count=0;
	char *ptr=str;
	char *rptr=str;

	for(count=0; *rptr != 0; rptr++, count++) /* empty */;
	rptr--;
	while (ptr < rptr ) {
		swap(ptr++,rptr--);
	}

	return 0;
}
```
