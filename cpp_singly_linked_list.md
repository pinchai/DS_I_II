#include <iostream>
using namespace std;

int main() {
	struct Node{
		int data;
		Node* next;
	};
	
	Node node1;
	Node node2;
	Node node3;
	
	node1.data = 1;
	node2.data = 2;
	node3.data = 3;
	
	node1.next = &node2;
	node2.next = &node3;
	node3.next = NULL;
	
	Node* first = &node1;
	while(first != NULL){
		cout<<first->data;
		first = first->next;
	}
	
	
	return 0;
}
