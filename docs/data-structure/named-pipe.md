Program to Read & Write Named Pipe
==================================

SEPTEMBER 29,2018 ~ ADMIN@EMBEDDEDPROGRAMS.COM

``` c
/*
 * file: named_pipe.c
 */
#include <stdio.h>
#include <sys/types.h>
#include <sys/stat.h>
#include <fcntl.h>
#include <unistd.h>
#include <errno.h>
#define MAX_SIZE 1024
#define FIFO_NAME "MYFIFO"
/* main()*/
int main(int argc, char *argv[])
{
	char *fifo_f = FIFO_NAME;
	int fifo_fd;
	char send_msg[MAX_SIZE];
	char rec_msg[MAX_SIZE];

	/* create fifo */
	if (-1 == mkfifo(fifo_f, S_IRUSR | S_IWUSR | S_IRGRP | S_IROTH)) {
		perror("reader:mkfifo");
		_exit(-2);;
	}

	/* open fifo */
	fifo_fd = open(fifo_f, O_CREAT | O_TRUNC | O_RDWR, S_IRUSR
		       | S_IWUSR | S_IRGRP | S_IROTH);
	if (-1 == fifo_fd) {
		perror("file open");
		_exit(-3);;
	}

	printf("nSend $ ");
	gets(send_msg);
	//scanf("%[^n]s", send_msg);

	/* write fifo */
	if (-1 == write(fifo_fd, send_msg, sizeof(send_msg))) {
		perror("write fails");
		_exit(-4);;
	}

	/* write fifo */
	if (-1 == read(fifo_fd, &rec_msg, sizeof(send_msg))) {
		perror("read fails");
		_exit(-4);;
	}

	printf("nReceived $ %sn", rec_msg);
	/* close fifo fd */
	close(fifo_fd);

	/* close fifo */
	unlink(fifo_f);
	return 0;
}
```
