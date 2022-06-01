#19. Remove Nth Node From End of List

To do this, I am going to use two pointers(first, second) as it stated on the title.

So the basic process is that the first and the second pointers goes right one step at a time.
However, the first pointer starts first and the second pointer starts after n step later.
By doing this, we can check the Nth node from end of linked list when the first pointer touch the last node of the list.

But I am not sure why this code is not working...

```
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next

class Solution:
    def removeNthFromEnd(self, head: Optional[ListNode], n: int) -> Optional[ListNode]:
        first = second = head
        prev = head
        count = 1
        while(count != n):
            first = first.next
            count += 1

        while(first.next!=None):
            prev = second
            second = second.next
            first = first.next

        if prev!=None and prev.next!=None:
            prev.next = second.next

        return head
```
So this code works for the example with n>1.

1) head = [1], n = 1 case is not working.
2) head = [1,2], n = 1 case is working.

```
class Solution:
    def removeNthFromEnd(self, head: Optional[ListNode], n: int) -> Optional[ListNode]:
        first = second = head
        prev = head
        count = 1

        if first.next==None: # if there is only one element -> n should be 1 => return None
            return None

        while(count != n): # move the first pointer
            first = first.next
            count += 1

        while(first!=None and first.next!=None): # move all three pointers -> prev is dummy pointer
            prev = second
            second = second.next
            first = first.next

        if prev!=None and prev.next!=None: # i think this conditinoal statement is not needed...?
            if prev == second: # if list is too short to move the second and the first pointer
                second = second.next # move
                prev = prev.next # move
                prev.next = second.next
                return prev # return prev here!!!
            else:
                prev.next = second.next

        return head

```

It works!

```

Complexity Analysis

Time complexity : O(L)
The algorithm makes one traversal of the list of L nodes.


Space complexity : O(1).
We only used constant extra space.

```
