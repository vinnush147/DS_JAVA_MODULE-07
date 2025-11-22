# Ex8 Detection of Cycle and Finding the Starting Node in a Linked List
## DATE: 21/11/2025
## AIM:
To write a program that detects a cycle in a linked list and returns the node where the cycle begins.
If there is no cycle, the program should return null without modifying the linked list.
## Algorithm
1. Use two pointers slow and fast to traverse, with fast moving twice as fast.

2.If slow and fast ever meet, a cycle exists.

3.Set a new pointer entry at the head.

4.Move both entry and slow one step at a time.

5.The node where they meet is the start of the cycle; if they never meet, there is no cycle.
  

## Program:
```
/*
program that detects a cycle in a linked list and returns the node where the cycle begins.
If there is no cycle, the program should return null without modifying the linked list.
Developed by: Vinnush Kumar L S
RegisterNumber: 212223230244
import java.util.*;

public class Solution {

    static class ListNode {
        int val;
        ListNode next;

        ListNode(int x) {
            val = x;
            next = null;
        }
    }

    public ListNode detectCycle(ListNode head) {
        if (head == null || head.next == null) return null;

        ListNode slow = head, fast = head;

        while (fast != null && fast.next != null) {
            slow = slow.next;
            fast = fast.next.next;

            if (slow == fast) {
               
                ListNode entry = head;
                while (entry != slow) {
                    entry = entry.next;
                    slow = slow.next;
                }
                return entry;
            }
        }

        return null;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        Solution sol = new Solution();

        String headInput = sc.nextLine().trim().replaceAll("\\[|\\]", "");
        
        int pos = sc.nextInt();

        if (headInput.isEmpty()) {
            System.out.println("no cylce");
            return;
        }

        String[] parts = headInput.split(",");
        int[] values = Arrays.stream(parts).mapToInt(Integer::parseInt).toArray();

        ListNode head = new ListNode(values[0]);
        ListNode current = head;
        List<ListNode> nodeList = new ArrayList<>();
        nodeList.add(head);

        for (int i = 1; i < values.length; i++) {
            ListNode newNode = new ListNode(values[i]);
            current.next = newNode;
            current = newNode;
            nodeList.add(newNode);
        }

      
        if (pos >= 0 && pos < nodeList.size()) {
            current.next = nodeList.get(pos);
        }


        ListNode cycleStart = sol.detectCycle(head);

        if (cycleStart != null) {
            int index = 0;
            for (ListNode node : nodeList) {
                if (node == cycleStart) {
                    System.out.println("tail connects to node index " + index);
                    return;
                }
                index++;
            }
        } else {
            System.out.println("no cycle");
        }
    }
}
 
*/
```

## Output:
<img width="925" height="215" alt="image" src="https://github.com/user-attachments/assets/1cb05483-ba5b-4ad5-b74b-0b9f2d733fa1" />

## Result:
The program successfully detects whether a cycle exists in the linked list.
If a cycle is present, it correctly identifies and returns the node where the cycle begins.
