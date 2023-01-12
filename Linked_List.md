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
Given the head of a singly linked list, return the middle node of the linked list.
If there are two middle nodes, return the second middle node.
Solution:
```
class Solution {
public:
    ListNode* middleNode(ListNode* head) {
        ListNode*slow=head,*fast=head;
        while(fast!=NULL && fast->next!=NULL)
        {
        slow=slow->next;
        fast=fast->next->next;
        }
        return slow;
    }
};
```
#### Question 4:
You are given the heads of two sorted linked lists list1 and list2.

Merge the two lists in a one sorted list. The list should be made by splicing together the nodes of the first two lists.

Return the head of the merged linked list.
Solution:
```
class Solution {
public:
    ListNode* mergeTwoLists(ListNode* list1, ListNode* list2) {
        if(list1 == NULL)
            return list2;
        if(list2 == NULL)
            return list1;
        
        ListNode * ptr = list1;
        if(list1 -> val > list2 -> val)
        {
            ptr = list2;
            list2 = list2 -> next;
        }
        else
        {
            list1 = list1 -> next;
        }
        ListNode *curr = ptr;
        while(list1 &&  list2)
        {
            if(list1 -> val < list2 -> val){
                curr->next = list1;
                list1 = list1 -> next;
            }
            else{
                curr->next = list2;
                list2 = list2 -> next;
            }
            curr = curr -> next;
                
        }
        if(!list1)
            curr -> next = list2;
        else
            curr -> next = list1;
            
        return ptr;
    }
};
```
