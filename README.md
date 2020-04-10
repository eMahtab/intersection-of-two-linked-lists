# Intersection of two Linked Lists (Merge Point)
## https://leetcode.com/problems/intersection-of-two-linked-lists

Write a program to find the node at which the intersection of two singly linked lists begins.

**Notes:**

If the two linked lists have no intersection at all, return null.
The linked lists must retain their original structure after the function returns.
You may assume there are no cycles anywhere in the entire linked structure.
Your code should preferably run in O(n) time and use only O(1) memory.

# Implementation 1 : Time : O(n+m) , Space : O(n)
```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
public class Solution {
    public ListNode getIntersectionNode(ListNode headA, ListNode headB) {
        if(headA == null || headB == null)
            return null;
        Set<ListNode> set = new HashSet<>();
        ListNode current = headA;
        while(current != null) {
            set.add(current);
            current = current.next;
        }
        current = headB;
        while(current != null) {
            if(set.contains(current))
                return current;
            current = current.next;
        }
        return null;
    }
}
```

## Implementation :

```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
public class Solution {
    public ListNode getIntersectionNode(ListNode headA, ListNode headB) {
        if(headA == null || headB == null)
            return null;

        int m = length(headA);
        int n = length(headB);
        //walk through d nodes of longer linked list
        int d = 0;
        if(n > m){
            d = n - m;
            for(int i = 0; i < d; i++)
                headB = headB.next;
        } else{
            d = m - n;
            for(int i = 0; i < d; i++)
                headA = headA.next;
        }
        while(headA != null && headB != null){
            if(headA == headB)
                return headA;
            headA = headA.next;
            headB = headB.next;
        }
        return null;
    }
    
    private int length(ListNode head){
        int length = 0;
        while(head != null){
            length++;
            head = head.next;
        }
        return length;
    }
    
}
```

# References :
https://www.youtube.com/watch?v=gE0GopCq378
