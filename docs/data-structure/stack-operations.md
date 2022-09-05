Programs for Stack operations
=============================

OCTOBER 14, 2018 ~ ADMIN@EMBEDDEDPROGRAMS.COM

``` c
#include <stdio.h>
#include <string.h>
#include <stdlib.h>
#include <ctype.h>

#define MAX 30

struct stack {
	char *data ;
	int top;
	int limit;
};

int init_stack(struct stack **s, int size) {
	struct stack *p=(*s);

	p=malloc(sizeof(struct stack));
	if (p == NULL)
		return -1;

	p->top =-1;
	p->limit = size;
	p->data = (char *)malloc(sizeof(p->limit));
	if (p->data == NULL) {
		free(p);
		return -2;
	} else {
		strcpy(p->data,"");
	}

	(*s)=p;
	return 0;
}

void destroy_stack(struct stack **s) {
	if ((*s) && (*s)->data != NULL)
		free((*s)->data);

	if(*s)
		free(*s);
}

void push(struct stack **s, char ch) {
	struct stack *p=*s;

	if (p->top >= MAX) {
		printf("nStack is fulln");
	} else {
		++p->top;
		p->data[p->top] = ch;
	}
}

char pop(struct stack **s) {
	struct stack *p=(*s);
	char ch;

	if ( p->top == -1) {
		printf("nStack is emptyn");
	} else {
		ch = p->data[p->top];
		--p->top;
		//printf("n%s: top=%d",__func__,p->top);
	}
	return ch;
}

char gettop(struct stack *s) {
	return s->data[s->top];
}

void print_stack(struct stack *p) {
	int i=-1;
	if(p) {
		printf("nStack elements are (top=%d): ", p->top);
		for (i=0;i<=p->top;i++) {
			printf("%c",p->data[i]);
		}
	}
}

int main() {
	struct stack *stk;

	init_stack(&stk,MAX);

	push(&stk,'c');
	push(&stk,'d');

	pop(&stk);

	print_stack(stk);
	printf("nStack top element is %c",gettop(stk));

	destroy_stack(&stk);

	return 0;
}
```
