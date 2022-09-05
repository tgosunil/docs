Program to implement a linked list
==================================

SEPTEMBER 29, 2018 ~ ADMIN@EMBEDDEDPROGRAMS.COM

``` c
#include <stdio.h>
#include <stdlib.h>

struct node {
	int data;
	struct node *next;
};

/* Count all element of List */
void CountElements(struct node *ptr) {
	int count = 0;

	while (ptr != NULL) {
		count++;
		ptr = ptr->next;
	}

	printf("List Count = %dn", count);
}

/* Print all element of List */
void printList(struct node *ptr) {
	printf("Start --> ");
	while (ptr != NULL) {
		printf("%d --> ", ptr->data);
		ptr = ptr->next;
	}

	printf(" NULL n");
}

/* Add element by Index */
int addElement(struct node **ptr, int num) {
	struct node *p, *t = *ptr;	/* Allocate node */
	p = (struct node *)malloc(sizeof(struct node));
	p->data = num;
	p->next = NULL;

	if (t == NULL) {
		*ptr = p;
	} else {
		while (t->next != NULL)
			t = t->next;
		t->next = p;
	}

	return 0;
}

/* Add element by Index */
int addElementAtIndex(struct node **ptr, int index, int num) {
	struct node *q = NULL, *p = *ptr;
	int count = 1;		/* Allocate node */

	q = (struct node *)malloc(sizeof(struct node));
	q->data = num;
	q->next = NULL;

	while ((p != NULL) && (++count < index)) {
		p = p->next;
	}

	if (count != index)
		return -1;
	q->next = p->next;
	p->next = q;
	return 0;
}

/* Delete element by content */
int delElementByValue(struct node **ptr, int num) {
	struct node *p = *ptr;
	struct node *q = NULL;

	if (p->data == num) {
		q = p;
		(*ptr) = q->next;
		free(q);
	} else {
		q = (*ptr)->next;

		while ((q != NULL) && (q->data != num)) {
			p = p->next;
			q = q->next;
		}

		if (q != NULL) {
			p->next = q->next;
			free(q);
		}
	}

	return 0;
}

/* Delete element by Index */
int delElementByIndex(struct node **ptr, int index) {
	struct node *p = *ptr;
	struct node *q = NULL;
	int count = 1;

	while ((p != NULL) && (++count < index)) {
		p = p->next;
	}

	if (count != index)
		return -1;
	if (p != NULL) {
		q = p->next;
		p->next = q->next;
		free(q);
	}

	return 0;
}

/* Reverse Link List */
int reverseList(struct node **ptr) {
	struct node *q = *ptr, *p = *ptr;
	struct node *r = NULL;

	if ((p == NULL) || (p->next == NULL)) {
		return 0;
	}

	while (q != NULL) {
		q = p->next;
		p->next = r;
		r = p;
		p = q;
	}

	(*ptr) = r;
	return 0;
}

int main() {
	struct node *list = NULL;

	addElement(&list, 43);
	addElement(&list, 54);
	printList(list);

	reverseList(&list);
	printList(list);

	addElement(&list, 35);
	addElement(&list, 67);
	addElement(&list, 94);
	addElement(&list, 86);
	printList(list);

	CountElements(list);
	delElementByValue(&list, 67);
	delElementByValue(&list, 43);
	printList(list);

	delElementByIndex(&list, 3);
	printList(list);

	addElementAtIndex(&list, 3, 44);
	printList(list);

	reverseList(&list);
	printList(list);

	return 0;
}
```
