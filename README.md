# Coding

## Question 1, 3 and 4: Binary Search Tree Insertion and Inorder traversal:
```
#include <stdio.h>
#include <stdlib.h>

struct node {
	int key;
	struct node *left, *right;
};

struct node* newNode(int item)
{
	struct node* temp = (struct node*)malloc(sizeof(struct node));
	temp->key = item;
	temp->left = temp->right = NULL;
	return temp;
}

void inorder(struct node* root)
{
    
	if (root != NULL) {
		inorder(root->left);
		printf("%d \n", root->key);
		inorder(root->right);
	}
}

void preorder(struct node* root)
{
    
	if (root!=NULL){
		printf("%d \n", root->key);
		preorder(root->left);
		preorder(root->right);
	}
}
struct node* insert(struct node* node, int key)
{
	if (node == NULL)
		return newNode(key);

	if (key < node->key)
		node->left = insert(node->left, key);
	else if (key > node->key)
		node->right = insert(node->right, key);
	
	return node;
}

int main()
{
	struct node* root = NULL;
	root = insert(root, 50);
	insert(root, 30);
	insert(root, 20);
	insert(root, 40);
	insert(root, 70);
	insert(root, 60);
	insert(root, 80);
	printf("Inorder");
	inorder(root);
	printf("Preorder");
	preorder(root);
	
	return 0;
}
```
## Question 2 and 12: Searching in linked list and Simple Linked List Implementation:
```
#include<stdio.h>
#include<stdlib.h>
#include<stdbool.h>

struct Node
{
	int key;
	struct Node* next;
};


void push(struct Node** head_ref, int new_key)
{
	struct Node* new_node = 
				(struct Node*) malloc(sizeof(struct Node));
	new_node->key = new_key;
	
	new_node->next = (*head_ref);
	(*head_ref) = new_node;
}


bool search(struct Node* head, int x)
{
	struct Node* current = head;
	while (current != NULL)
	{
		if (current->key == x)
			return true;
		current = current->next;
	}
	return false;
}

int main()
{
	struct Node* head = NULL;
	int x = 21;
	push(&head, 10);
	push(&head, 30);
	push(&head, 11);
	push(&head, 21);
	push(&head, 14);

	search(head, 21)? printf("Yes") : printf("No");
	return 0;
}
```

## Question 5: Queue (Enque – Dequeue):
```
#include <stdio.h>
#define SIZE 5

void enQueue(int);
void deQueue();
void display();

int items[SIZE], front = -1, rear = -1;

int main() {
  deQueue();
  enQueue(1);
  enQueue(2);
  enQueue(3);
  enQueue(4);
  enQueue(5);
  enQueue(6);

  display();
  deQueue();
  display();

  return 0;
}

void enQueue(int value) {
  if (rear == SIZE - 1)
    printf("\nQueue is Full!!");
  else {
    if (front == -1)
      front = 0;
    rear++;
    items[rear] = value;
    printf("\nInserted -> %d", value);
  }
}

void deQueue() {
  if (front == -1)
    printf("\nQueue is Empty!!");
  else {
    printf("\nDeleted : %d", items[front]);
    front++;
    if (front > rear)
      front = rear = -1;
  }
}
void display() {
  if (rear == -1)
    printf("\nQueue is Empty!!!");
  else {
    int i;
    printf("\nQueue elements are:\n");
    for (i = front; i <= rear; i++)
      printf("%d  ", items[i]);
  }
  printf("\n");
}

```



## Question 6 and 7: nPr and nCr :
```
#include <stdio.h>
long factorial(int);
long find_ncr(int, int);
long find_npr(int, int);
int main(){
	int n, r;
	long ncr, npr;
	printf("Enter the value of n and r\n");
	scanf("%d%d",&n,&r);
	ncr = find_ncr(n, r);
	npr = find_npr(n, r);
	printf("%dC%d = %ld\n", n, r, ncr);
	printf("%dP%d = %ld\n", n, r, npr);
	return 0;
}
long find_ncr(int n, int r) {
	long result;
	result = factorial(n)/(factorial(r)*factorial(n-r));
	return result;
}
long find_npr(int n, int r) {
	long result;
	result = factorial(n)/factorial(n-r);
	return result;
}
long factorial(int n) {
	int c;
	long result = 1;
	for (c = 1; c <= n; c++)
		result = result*c;
	return result;
}
```

## Question 8: Print Address and Value:
```
#include <stdio.h>
int main() {
    int a=3;
    int * p=&a;
    printf("%d\n",a);
    printf("%p\n",&a);
    return 0;
}
```
## Question 9: Adding 2 numbers using pointers:
```
#include <stdio.h>
int main()
{
	int first, second, *p, *q, sum;
	printf("Enter two integers to add\n");
	scanf("%d%d", &first, &second);
	p = &first;
	q = &second;
	sum = *p + *q;
	printf("Sum of the numbers = %d\n", sum);
	return 0;
}
```

## Question 10: One Variable with Many pointers:
```
#include <stdio.h>

int main() {
    int a=10;
    int * p=&a;
    int * q=&a;
    int * r=&a;
    *p=*p+5;
    printf("%d\n",*p);
    *q=*q+5;
    printf("%d\n",*q);
    *r=*r+5;
    printf("%d\n",*r);
    printf("%d\n",a);
    return 0;
}
```

## Question 11: String Reversal using Stack:
```
#include <stdio.h>  
#include <string.h>  
  
#define max 100  
int top,stack[max];  
  
void push(char x){  
  
      // Push(Inserting Element in stack) operation  
      if(top == max-1){  
          printf("Stack overflow");  
      }  else {  
          stack[++top]=x;  
      }  
  
}  
  
void pop(){  
    // Pop (Removing element from stack)  
      printf("%c",stack[top--]);  
}  
  
  
int main()  
{  
   char str[]="Manikanta Sandeep";  
   int len = strlen(str);  
   int i;  
  
   for(i=0;i<len;i++)  
        push(str[i]);  
  
   for(i=0;i<len;i++)  
      pop();  
}

```

## Question 13: Basic Stack:
```
#include <stdio.h>

int MAXSIZE = 8;       
int stack[8];     
int top = -1;            

int isempty() {

   if(top == -1)
      return 1;
   else
      return 0;
}
   
int isfull() {

   if(top == MAXSIZE)
      return 1;
   else
      return 0;
}


int peek() {
   return stack[top];
}

int pop() {
   int data;
        
   if(!isempty()) {
      data = stack[top];
      top = top - 1;   
      return data;
   } else {
      printf("Could not retrieve data, Stack is empty.\n");
   }
}

int push(int data) {

   if(!isfull()) {
      top = top + 1;   
      stack[top] = data;
   } else {
      printf("Could not insert data, Stack is full.\n");
   }
}

int main() {
   // push items on to the stack 
   push(3);
   push(5);
   push(9);
   push(1);
   push(12);
   push(15);

   printf("Element at top of the stack: %d\n" ,peek());
   printf("Elements: \n");

   // print stack data 
   while(!isempty()) {
      int data = pop();
      printf("%d\n",data);
   }

   printf("Stack full: %s\n" , isfull()?"true":"false");
   printf("Stack empty: %s\n" , isempty()?"true":"false");
   
   return 0;
}
```
## Question 14: Biomial Distribution:
```
#include<stdio.h>
#include<math.h>
int facto(int);
void main(){
    double p,result;            
    int n,r,nr,factN,factR,factNR;
    
    printf("binomial distribution\n");
    
    printf("enter the value of N:");
    
    scanf("%d",&n);
    
    printf("enter the value of R");
    
    scanf("%d",&r);
    
    printf("enter the value of P");
    
    scanf("%lf",&p);
    
    nr=n-r;
    
    factN=facto(n);
    
    factR=facto(r);
    
    factNR=facto(nr);
    
    result=((factN/(factR*factNR))*pow(p,r)*(pow((1-p),nr)));
    
    printf("\n result=%.5lf",result);
}

int facto(int num){
    if (num==0 | num==1){
        return 1;
    }
    facto(num-1)*num;

}
```
## Poisson Distribution:
```
#include<stdio.h>
int facto(int );
int main(){
    int x;
    double lambda;
    float e=2.72;
    double pr;
    scanf("%lf",&lambda);
    scanf("%d",&x);
    pr=(pow((lambda),x)/facto(x))*pow((e),(-lambda));
    printf("%lf",pr);
}
int facto(int a){
    if (a==0 | a==1){
        return 1;
    }
    return facto(a-1)*a;
}

```
## Question 15: Print all Permutations:
```
#include<stdio.h>  
#include<string.h>  
void generatePermutation(char * , int , int );  
  
int main()  
{  
  char str[] = "ABC";  
  int n =strlen(str);  
  printf("All the permutations of the string are: \n");  
  generatePermutation(str,0,n);  
}  
  
void generatePermutation(char *str,const int start, int end)  
{  
  char temp;  
  int i,j;  
  for(i = start; i < end-1; ++i){  
  for(j = i+1; j < end; ++j)  
  {  
    temp = str[i];  
  str[i] = str[j];  
    str[j] = temp;  
  generatePermutation(str , i+1 ,end);  
    temp = str[i];  
    str[i] = str[j];  
    str[j] = temp;  
  }  
  }  
  printf("%s\n",str);  
}
```
