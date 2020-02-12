# Intersection of two Linked Lists (Merge Point)
## https://leetcode.com/problems/intersection-of-two-linked-lists

Write a program to find the node at which the intersection of two singly linked lists begins.

**Notes:**

If the two linked lists have no intersection at all, return null.
The linked lists must retain their original structure after the function returns.
You may assume there are no cycles anywhere in the entire linked structure.
Your code should preferably run in O(n) time and use only O(1) memory.

# Implementation : Brute Force
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

        while(headA != null){
            ListNode listBStart = headB;
            while(listBStart != null){
                if(listBStart == headA)
                    return headA;
                listBStart = listBStart.next;
            }
            headA = headA.next;
        }
        return null;
    }
    
}
```
