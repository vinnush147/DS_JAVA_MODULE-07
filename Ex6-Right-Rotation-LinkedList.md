# Ex6 Right Rotation LinkedList
## DATE:22-11-2025
## AIM:
To write a Java  program to:
Create a singly linked list.
Rotate the linked list to the right by k positions.
Display the rotated linked list.
## Algorithm
1. Read n values to build the linked list and read k.
2. Find the length of the list and reach the last node.
3. Make the list circular by connecting last node to head.
4. Move length − (k % length) steps to find new tail.
5. Break the circle and print the list from the new head.
   

## Program:
```
/*
Program to  Right Rotation LinkedList
Developed by: Vinnush Kumar L S
RegisterNumber: 212223230244

import java.util.Scanner;

class Node {
    int data;
    Node next;
    Node(int data) {
        this.data = data;
        this.next = null;
    }
}

class prog {
    public static Node rotateRight(Node head, int k) {
        if (head == null || head.next == null || k == 0)
            return head;

        Node temp = head;
        int length = 1;
        while (temp.next != null) {
            temp = temp.next;
            length++;
        }

        temp.next = head;

        int stepsToNewHead = length - k % length;
        Node newTail = head;
        for (int i = 1; i < stepsToNewHead; i++) {
            newTail = newTail.next;
        }

        Node newHead = newTail.next;

        newTail.next = null;

        return newHead;
    }

    public static void printList(Node head) {
        Node temp = head;
        while (temp != null) {
            System.out.print(temp.data + " ");
            temp = temp.next;
        }
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();

        if (n <= 0) {
            sc.close();
            return;
        }

        Node head = new Node(sc.nextInt());
        Node tail = head;
        for (int i = 1; i < n; i++) {
            tail.next = new Node(sc.nextInt());
            tail = tail.next;
        }

        int k = sc.nextInt();

        head = rotateRight(head, k);

        System.out.print("LinkedList: ");
        printList(head);

        sc.close();
    }
}
 
*/
```

## Output:
<img width="898" height="213" alt="image" src="https://github.com/user-attachments/assets/f39e86c6-bde2-492f-8d51-2a46055ced76" />

## Result:
Thus, the Java program to perfom right rotation on linked list is implemented successfully.
