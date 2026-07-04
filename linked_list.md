#include <iostream>
using namespace std;

struct Node {
    int data;
    Node* next;
};

void display(Node* head) {
    Node* current = head;

    while (current != nullptr) {
        cout << current->data << " -> ";
        current = current->next;
    }

    cout << "NULL" << endl;
}

void insertAtBeginning(Node*& head, int value) {
    Node* newNode = new Node;

    newNode->data = value;
    newNode->next = head;

    head = newNode;
}

void insertAtEnd(Node*& head, int value) {
    Node* newNode = new Node;

    newNode->data = value;
    newNode->next = nullptr;

    if (head == nullptr) {
        head = newNode;
        return;
    }

    Node* current = head;

    while (current->next != nullptr) {
        current = current->next;
    }

    current->next = newNode;
}

void deleteNode(Node*& head, int value) {
    if (head == nullptr) {
        return;
    }

    if (head->data == value) {
        Node* temp = head;
        head = head->next;
        delete temp;
        return;
    }

    Node* current = head;

    while (current->next != nullptr &&
           current->next->data != value) {
        current = current->next;
    }

    if (current->next != nullptr) {
        Node* temp = current->next;
        current->next = temp->next;
        delete temp;
    }
}

int main() {
    Node* head = nullptr;

    insertAtEnd(head, 10);
    insertAtEnd(head, 20);
    insertAtEnd(head, 30);

    cout << "Original list:" << endl;
    display(head);

    insertAtBeginning(head, 5);

    cout << "After inserting 5 at beginning:" << endl;
    display(head);

    insertAtEnd(head, 40);

    cout << "After inserting 40 at end:" << endl;
    display(head);

    deleteNode(head, 20);

    cout << "After deleting 20:" << endl;
    display(head);

    return 0;
}
