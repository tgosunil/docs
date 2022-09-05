Binary Tree without Recursion
=============================

[OCTOBER 17,
2018](https://embeddedprograms.wordpress.com/2018/10/17/c-program-to-create-binary-tree-without-recursion/)
~
[ADMIN@EMBEDDEDPROGRAMS.COM](https://embeddedprograms.wordpress.com/author/embeddedprograms/)

``` c
#include <stdio.h>
#include <stdlib.h>

struct node {
	char data;
	struct node *left;
	struct node *right;
};

void print_tree(struct node *p) {
	struct node *t=p;

	if ( t != NULL ) {
		print_tree(t->left);
		printf("%c ",t->data);
		print_tree(t->right);
	}
}

void build_tree(struct node **t, char *data, int count) {
	struct node *ptr[10];
	int i;

	for (i=0;i<count;i++) {
		ptr[i]=malloc(sizeof(struct node));
		ptr[i]->data = data[i];
		ptr[i]->left = ptr[i]->right = NULL;
	}

	for (i=0; i<count;i++) {
		/* update left child */
		if ((2*i+1) < count ) {
			ptr[i]->left = ptr[2*i+1];
		}

		/* update right child */
		if ((2*i+2) < count )
			ptr[i]->right = ptr[2*i+2];
	}

	(*t) = ptr[0];
}

void main() {
	/* tree representation in array form
	 * left subtree = 2*(index) + 1;
	 * right subtree = 2*(index) + 2;
	 */

	char data[] = {	'A','B','C','D','E','F','G','H','I','J'};

	/* pictorial view of above tree */
	/* 	 (A) 		*/
	/* 		 / \		*/
	/*	        /   \		*/
	/*	       /     \ 		*/
	/* 	      /       \		  */
	/* /  */
	/* (B) (C) */
	/* / / */
	/* /  /  */
	/* /  /  */
	/* /  /  */
	/* /  /  */
	/*     (D)  (E) (F) (G) */
	/*     / \ / */
	/*    /  / */
	/*   /  / */
	/* (H)          (I) (J) */

	struct node *btree=NULL;
	build_tree(&btree, data,(int)sizeof(data)/sizeof(data[0]));
	printf("nElement of the tree are:n");
	print_tree(btree);
}
```
