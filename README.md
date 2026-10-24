# Remove-Zero-Sum-Consecutive-Nodes-from-Linked-List
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def removeZeroSumSublists(self, head: ListNode | None) -> ListNode | None:
        if head is None:
            return None
        r=[]
        temp=head
        while temp:
            r.append(temp.val)
            temp=temp.next
        i=0
        while i<len(r):
            c=0
            for j in range(i,len(r)):
                c+=r[j]
                if c==0:
                    del r[i:j+1]
                    break
            else:
                i+=1
        d=ListNode(0)
        temp=d
        for i in r:
            temp.next=ListNode(i)
            temp=temp.next
        return d.next
        
