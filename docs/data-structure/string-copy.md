Write a program to copy a string ?
==================================

SEPTEMBER 29, 2018 ~ SUNIL KUMAR

``` c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

/*
 * function to copy string
 * dst = output string
 * src = source string
 */
void xstrcpy(char *dst,const char *src) {
	while ( (*dst++ = *src++) != '0');
}

void main() {
	char str[]="India is Great";
	char *result;

	result = (char *) malloc(strlen(str));

	xstrcpy(result,str);
	printf("%sn",result);

	free(result);
}
```
