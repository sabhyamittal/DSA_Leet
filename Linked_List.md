#### Question 1:
Given the head of a singly linked list, reverse the list, and return the reversed list.
Solution:
```
class Solution {
public:
    ListNode* reverseList(ListNode* head) {
        ListNode*dummynode=NULL;
        while(head!=NULL)
        {
        ListNode*next=head->next;
        head->next=dummynode;
        dummynode=head;
        head=next;
        }
        return dummynode;
    }
};
```

#### Question 2:
Given the head of a linked list, remove the nth node from the end of the list and return its head.
Solution:
```
class Solution {
public:
    ListNode* removeNthFromEnd(ListNode* head, int n) {
        ListNode*dummy=new ListNode();
        dummy->next=head;
        ListNode*fast=dummy;
        ListNode*slow=dummy;
        for(int i=0 ;i<n ;i++)
        {
            fast=fast->next;
        }
        while(fast->next!=NULL)
        {
            fast=fast->next;
            slow=slow->next;
        }
        slow->next=slow->next->next;
        return dummy->next;
    }
};
```
#### Question 3:
Solution:
