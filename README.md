# DSA-Reverse-Linked-List-II
Given the head of a singly linked list and two integers left and right where left <= right, reverse the nodes of the list from position left to position right, and return the reversed list.
```
Input: head = [1,2,3,4,5], left = 2, right = 4
Output: [1,4,3,2,5]
```
```
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def reverseBetween(self, head: Optional[ListNode], left: int, right: int) -> Optional[ListNode]:
        if not head:
            return None
        curr=head
        prev=None
        while left>1: #time cost O(n)
            prev=curr
            curr=curr.next
            left,right=left-1,right-1
        tail,con=curr,prev
        while right: #time cost O(n)
            third=curr.next
            curr.next=prev
            prev=curr
            curr=third
            right-=1
        if con:
            con.next=prev
        else:
            head=prev
        tail.next=curr
        return head #space cost O(1)
    '''
    Total time cost 2O(n)=O(n)
    Total space cost O(1)
    '''

```
