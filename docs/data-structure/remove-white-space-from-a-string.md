Program to remove leading space from a string 
=======================================================

SEPTEMBER 29, 2018 ~ SUNIL KUMAR

``` c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

/*
 * function to remove leading and trailing
 * space from 'src' and store it in 'dst'.
 */

void xtrim(char *dst,const char *src) {

	/* Remove leading white space */
	while ( (*src == ' ') || (*src == 't') ) {
		*src++;
	}

	while ( (*dst++ = *src++) != '0');

	/* Remove trailing white space */
	dst--; dst--;

	while ( (*dst == ' ') || (*dst == 't') ) {
		*dst--;
	}
	*++dst ='\0';
}

void main() {
	char str[]=" India is Great ";
	char *result;

	result = (char *) malloc(strlen(str));

	printf("length of string before trim = %dn", strlen(str));
	xtrim(result,str);

	printf("String = "%s"n",result);
	printf("length of string after trim = %dn", strlen(result));

	free(result);
}
```
