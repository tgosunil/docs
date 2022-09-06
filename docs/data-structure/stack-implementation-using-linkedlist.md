Implementation of Stack using Linklist
======================================

OCTOBER 16, 2018 ~ SUNIL KUMAR

``` c
#include <stdio.h>
#include <stdlib.h>

struct stack {
	int data;
	struct stack *next;
};

void push(struct stack **top, int num) {
	struct stack *temp;

	temp=malloc(sizeof(struct stack));
	if (temp == NULL) {
		printf("Stack is fulln");
		return;
	}

	temp->data = num;
	temp->next = NULL;
	if ((*top) == NULL) {
		(*top)=temp;
	} else {
		temp->next = (*top);
		(*top) = temp;
	}
}

int pop(struct stack **top) {
	struct stack *temp;
	int data;

	if ((*top) == NULL) {
		printf("Stack is emptyn");
		return NULL;
	}

	temp = (*top);
	(*top)=(*top)->next;
	data = temp->data;
	free(temp);
	return(data);
}

void display(struct stack *top) {
	struct stack *ptr;
	ptr=top;
	printf("| TOP |n");
	while (ptr != NULL ) {
		printf ("| %d |n",ptr->data);
		ptr = ptr->next;
	}
}

void main() {
	struct stack *top;

	push(&top,12);
	display(top);
}
```
