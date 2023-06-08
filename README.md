#include<stdio.h>
#include<stdlib.h>
using namespace std;
struct node{
	int x;
	struct node* next;
};
node *makenode(int x){
	node *newnode=(node*)malloc(sizeof(node));
	newnode->x=x;
	newnode->next=NULL;
	return newnode;
}
void push_back(int x, node **head){
	node *newnode=makenode(x);
	if(*head==NULL){
		*head=newnode;
		return;
	}
	node *tmp=*head;
	while(tmp->next!=NULL){
		tmp=tmp->next;
	}
	tmp->next=newnode;
}
void push_front(int x, node **head){
	node *newnode= makenode(x);
	newnode->next=*head;
	*head=newnode;
	
}
void Sort(node **head){
	node *tmp1=*head;
	while(tmp1->next!=NULL){
		node *tmp2=tmp1->next;
		while(tmp2!=NULL){
			if(tmp1->x>tmp2->x){
				int tmp=tmp1->x;
				tmp1->x=tmp2->x;
				tmp2->x=tmp;
			}
			tmp2=tmp2->next;
		}
		tmp1=tmp1->next;
	}
}
void duyet(node *head){
	while(head!=NULL){
		printf("%d ", head->x);
		head=head->next;
	}
}
int main(){
	node *head=NULL;
	int n;
	scanf("%d", &n);
	for(int i=1;i<=n;i++){
		int x;
		scanf("%d", &x);
		push_front(x, &head);
	}
	Sort(&head);
	duyet(head);
	
}
