Infix to Prefix conversion using Stack with Linklist
====================================================

OCTOBER 16, 2018 ~ ADMIN@EMBEDDEDPROGRAMS.COM

``` c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

struct stack {
	char data;
	struct stack *next;
};

void push(struct stack **top, char num) {
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

char pop(struct stack **top) {
	struct stack *temp;
	char data;

	if ((*top) == NULL) {
		//printf("Stack is emptyn");
		return NULL;
	}

	temp = (*top);
	(*top)=(*top)->next;
	data = temp->data;
	free(temp);
	return(data);
}

char gettop(struct stack **top) {
	if ((*top) == NULL) {
		//printf("Stack is emptyn");
		return NULL;
	}

	return((*top)->data);
}

void display(struct stack *top) {
	struct stack *ptr = top;

	//ptr=top;
	printf("| TOP |n");
	while ( ptr != NULL ) {
		printf ("| %c |n",ptr->data);
		ptr = ptr->next;
	}
}

void strrev(char *str) {
	int i,j;

	for (i=0,j=strlen(str)-1;i<j;i++,j--) {
		str[i]^=str[j]^=str[i]^=str[j];
	}
}

int isoper(char ch) {
	switch(ch) {
		case '%':
		case '/':
		case '*':
		case '+':
		case '-':
		case '$':
		case '^':
			return 1;
		default:
			return 0;
	}
}

int prio(char ch) {
	if ( (ch == '^') || (ch == '$'))
		return 3;
	else if ((ch == '/') || (ch == '%') || (ch == '*'))
		return 2;
	else if ((ch == '+') || (ch == '-'))
		return 1;
	else
		return 0;
}

void infix2prefix(struct stack **top, char *str,char *result) {
	int i=0;
	char x;

	while (*str != '0') {
		if ((*str == "") || (*str == 't'))
			continue;
		if( isoper(*str) ) {
				while ((prio(*str) < prio(gettop(top)))) {
				result[i++] = pop(top);
			}

			push(top,*str);
		} else if ( *str == ')') {
			push(top,*str);
		} else if ( *str == '(') {
			while( (x = pop(top)) != ')' ) {
				result[i++] = x;
			}
			//pop(top);
		} else {
			result[i++] = *str;
		}
		str++;
	}

	while( (x = pop(top)) != NULL ) {
		result[i++] = x;
	}
	result[i] = '0';
}

void main() {
	struct stack *top = NULL;
	char expr[] = "4$2*3-3+8/4/(1+1)";
	char *result;

	result = malloc(sizeof(expr));
	printf("infix expression = %sn",expr);
	strrev(expr);
	printf("reverse expression = %sn",expr);
	infix2prefix(&top,expr,result);
	strrev(result);
	printf("prefix expression = %sn",result);
}
```
