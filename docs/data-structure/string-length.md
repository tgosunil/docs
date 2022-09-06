Program to find length of given string
======================================

SEPTEMBER 29, 2018 ~ SUNIL KUMAR

``` c
/*
 * file: mystrlen.c
 */

/* Program to calculate string length */
#include <stdio.h>

int xstrlen(char *);
int ystrlen(char *);
int zstrlen(char *);

int main(int argc, char *argv[]) {
	int res=0;
	char *str=argv[1];

	if (argc < 2 ) {
		printf("Invalid argumentn");
		printf("Usage: %s <string> n", argv[0]);
		return -1;
	}

	/* Method 1 */
	printf("Input : %sn", str);
	res = xstrlen(str);
	printf("Length of String "%s" is : %dn", str, res);

	/* Method 2 */
	res=0;
	res =ystrlen(str);
	printf("Length of String "%s" is : %dn", str, res);

	/* Method 3 */
	res=0;
	res =zstrlen(str);
	printf("Length of String "%s" is : %dn", str, res);

	return 0;
}

/* Method 1: Using while loop */
int xstrlen(char *str) {
	int count=0;

	while (*str++ != '0' )
		count++;
	return count;
}

/* Method 2: Using for loop */
int ystrlen(char *str) {
	int count=0;

	for(count=0; *str != 0; str++, count++);

	return count;
}

/* Method 3: Using pointer */
int zstrlen(char *str) {
	char *ptr=str;

	while (*ptr++ != '0' );

	return (ptr - str -1);
}
```
### Compilation Steps:
```
$ gcc -o mystrlen mystrlen.c
```
### Output:
$ ./strlen "Hello World"
```
Input : Hello World
Length of String "Hello World" is : 11
Length of String "Hello World" is : 11
Length of String "Hello World" is : 11
```
