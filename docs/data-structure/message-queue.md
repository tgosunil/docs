Program to implement Message Queue
==================================

SEPTEMBER 29, 2018 ~ SUNIL KUMAR

## mq_reader:

``` c
/*
 * file: mq_reader.c
 */
#include <stdio.h>
#include <fcntl.h>
#include <sys/stat.h>
#include <mqueue.h>
#include <errno.h>
#include <unistd.h>
#include <string.h>

#define MSG_Q_NAME "/MSG_Q"
#define NO_MAX_MSG 10
#define MAX_MSG 1024
#define STOP_CMD "exit"

/* main () */
int main(int agrc, char *argv[]) {
	mqd_t msg_q;
	struct mq_attr attr;
	char message[MAX_MSG];
	int mq_len;

	attr.mq_flags = 0;
	attr.mq_maxmsg = NO_MAX_MSG;
	attr.mq_msgsize = MAX_MSG;
	attr.mq_curmsgs = 0;
	msg_q = mq_open (MSG_Q_NAME,O_CREAT|O_RDONLY,S_IRUSR | S_IWUSR| S_IRGRP| S_IROTH, &attr);
	if ( -1 == msg_q) {
		perror("mq_open");
		_exit(-1);
	}

	do {
		bzero(message, MAX_MSG);
		mq_len = mq_receive(msg_q, message, MAX_MSG, NULL);

		if ( -1 == mq_len) {
			perror("mq_receive");
			mq_close(msg_q);
			mq_unlink(MSG_Q_NAME);
			_exit(-1);
		}

		printf("nReceived $ %sn", message);
	} while (!(0 == strcmp(message,STOP_CMD)));

	printf("nmq_reader: Exitn");
	mq_close(msg_q);
	mq_unlink(MSG_Q_NAME);
	return 0;
}
```

## Program mq_writer:
``` c
/*
 * file: mq_writer.c
 */
#include <stdio.h>
#include <fcntl.h>
#include <sys/stat.h>
#include <mqueue.h>
#include <errno.h>
#include <unistd.h>
#include <string.h>

#define MSG_Q_NAME "/MSG_Q"
#define NO_MAX_MSG 10
#define MAX_MSG 1024
#define STOP_CMD "exit"

/* main () */
int main(int agrc, char *argv[]) {
	mqd_t msg_q;
	struct mq_attr attr;
	int mq_len;
	char message[MAX_MSG];

	attr.mq_flags = 0;
	attr.mq_maxmsg = NO_MAX_MSG;
	attr.mq_msgsize = MAX_MSG;
	attr.mq_curmsgs = 0;
	msg_q = mq_open (MSG_Q_NAME,O_WRONLY,S_IRUSR | S_IWUSR | S_IRGRP | S_IROTH, &attr);
	if ( -1 == msg_q) {
		perror("mq_open");
		_exit(-1);
	}

	printf("nEnter "exit" to stop: ");
	do {
		bzero(message, MAX_MSG);
		printf("nSend $ ");
		gets(message);
		mq_len = strlen(message);
		if ( -1 == mq_send(msg_q, message, mq_len, 0)) {
			perror("mq_send");
			mq_close(msg_q);
			mq_unlink(MSG_Q_NAME);
			_exit(-1);
		}
	} while (!(0 == strcmp(message, STOP_CMD)));

	printf("mq_writer: Exitn");
	mq_close(msg_q);
	mq_unlink(MSG_Q_NAME);
	return 0;
}
```

## Compilation Steps:
```
$ gcc -o mq_writer mq_writer.c -lrt
$ gcc -o mq_reader mq_reader.c -lrt
```

## Output:
```
$ ./mq_reader&
$ ./mq_writer
Enter "exit" to stop:
Send $ hello are u
Received $ hello are u
Send $ exit
Received $ exit
mq_writer: Exit
mq_reader: Exit
[1]+ Done ./mq_reader
```
