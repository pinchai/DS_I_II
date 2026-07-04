# Singly Linked List in C++

This example demonstrates how to create and manage a **dynamic singly
linked list** in C++.

## Features

-   Display all nodes
-   Insert a node at the beginning
-   Insert a node at the end
-   Delete a node by value

## Complete C++ Code

``` cpp
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
```

## Expected Output

``` text
Original list:
10 -> 20 -> 30 -> NULL

After inserting 5 at beginning:
5 -> 10 -> 20 -> 30 -> NULL

After inserting 40 at end:
5 -> 10 -> 20 -> 30 -> 40 -> NULL

After deleting 20:
5 -> 10 -> 30 -> 40 -> NULL
```

## Function Summary

  -----------------------------------------------------------------------
  Function                            Description
  ----------------------------------- -----------------------------------
  `display()`                         Displays every node in the linked
                                      list

  `insertAtBeginning()`               Adds a new node before the current
                                      head

  `insertAtEnd()`                     Adds a new node after the last node

  `deleteNode()`                      Deletes the first node containing
                                      the specified value
  -----------------------------------------------------------------------

## Linked List Structure

``` text
head
 |
 v
+------+-------+    +------+-------+    +------+---------+
| data | next  | -> | data | next  | -> | data | nullptr |
+------+-------+    +------+-------+    +------+---------+
```

## Important Concepts

### `Node* head`

The `head` pointer stores the address of the first node.

### `Node*& head`

This means a **reference to a pointer**. It allows a function to change
the original `head` pointer.

### `new Node`

Dynamically creates a new node in memory.

### `delete temp`

Releases the memory used by a deleted node.

### `nullptr`

Represents a null pointer in C++11 and newer.
