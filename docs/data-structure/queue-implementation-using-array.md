Queue implementation using array
================================

[OCTOBER 16,
2018](https://embeddedprograms.wordpress.com/2018/10/16/queue-implementation-using-array/)
~
[ADMIN@EMBEDDEDPROGRAMS.COM](https://embeddedprograms.wordpress.com/author/embeddedprograms/)

``` c
#include <stdio.h>
#include <stdlib.h>
#define MAX (4)

struct queue {
	int data[MAX];
	short int front;
	short int rear;
};

void init_queue (struct queue *q) {
	q->front =q->rear = -1; /* empty */
}

void addq(struct queue *q, int num) {
	if (q->rear == MAX - 1) {
		printf("Cannot insert %d, Queue is fulln", num);
		return;
	}

	q->rear++;
	q->data[q->rear] = num;
	if (q->front == -1 ) {
		q->front = q->rear;
	}
}

int delq(struct queue *q) {
	int data;

	if (q->front == -1 ) {
		printf("Queue is emptyn");
		return -1;
	}
	data=q->data[q->front];
	if (q->front == MAX-1 ) {
		q->rear=q->front = -1;
	} else {
		q->front++;
	}

	return data;
}

void showq(struct queue *q) {
	int counter=0;

	printf("nFRONT(%d) --> ", q->front);
	for (counter = q->front; q->front != -1 && counter <= q->rear; counter++) {
		printf("%d --> ", q->data[counter]);
	}

	printf(" --> REAR(%d)n",q->rear);
}

int main() {
struct queue que;
int x,i;

	printf("Hello Queuen");
	init_queue(&que);
	addq(&que, 12);
	addq(&que, 45);
	addq(&que, 34);
	addq(&que, 77);
	addq(&que, 83);
	showq(&que);

	for (i=0;i<1;i++) {
		x=delq(&que);
		printf("Item delete = %dn", x);
	}

	showq(&que);
	addq(&que, 83);
	showq(&que);
	return 0;
}
```
