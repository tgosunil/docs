Program to implement IPC Pipes
==============================

SEPTEMBER 29, 2018 ~ ADMIN@EMBEDDEDPROGRAMS.COM

``` c
/*
 * file: pipes.c
 */
#include <stdio.h>
#include <unistd.h>
#include <errno.h>

#define MAX_SIZE 30

/*
 * main()
 */
int main(int argc,char *argv[]) {
	int pipefd[2];
	char recive_buffer[MAX_SIZE];
	char send_buffer[MAX_SIZE];

	/* create pipe */
	if (pipe(pipefd) < 0 ) {
		perror("Fail to open pipen");
		return -2;
	}

	printf("Enter String: ");
	scanf("%[^n]s", send_buffer);

	/* sending data on pipefd */
	printf("Sending data to pipe : %sn", send_buffer);
	write(pipefd[1], send_buffer, sizeof(send_buffer));

	/* receiving data on pipefd */
	read(pipefd[0], &recive_buffer, sizeof(send_buffer));
	printf("Received data from pipe : %sn", recive_buffer);

	close(pipefd[0]); /* close read end */
	close(pipefd[1]); /* close write end */
	return 0;
}
```
## Compilation Steps:
```
$ gcc -o pipes pipes.c
```
## Output:
```
Enter String: hello world
Sending data to pipe : hello world

Received data from pipe : hello world
```
