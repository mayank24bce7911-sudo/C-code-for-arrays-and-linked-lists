#include <stdio.h>
#include <stdlib.h>

typedef struct Node {
    int data;
    struct Node* next;
} Node;


Node* newNode(int value) {
    Node* n = (Node*)malloc(sizeof(Node));
    n->data = value;
    n->next = NULL;
    return n;
}

// Insert at end of linked list
void insertEnd(Node** head, int value) {
    Node* n = newNode(value);
    if (*head == NULL) {
        *head = n;
        return;
    }
    Node* temp = *head;
    while (temp->next) temp = temp->next;
    temp->next = n;
}


void displayList(Node* head) {
    while (head) {
        printf("%d -> ", head->data);
        head = head->next;
    }
    printf("NULL\n");
}


void arrayOps(int arr[], int size) {
    printf("Array contents: ");
    for (int i = 0; i < size; i++)
        printf("%d ", arr[i]);
    printf("\n");
}

int main() {
    // Array simulation
    int arr[] = {10, 20, 30, 40, 50};
    int size = sizeof(arr)/sizeof(arr[0]);
    arrayOps(arr, size);

 
    Node* head = NULL;
    insertEnd(&head, 10);
    insertEnd(&head, 20);
    insertEnd(&head, 30);
    insertEnd(&head, 40);
    insertEnd(&head, 50);

    printf("Linked List contents: ");
    displayList(head);

    return 0;
}
