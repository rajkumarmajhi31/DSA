/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    ListNode* reverseBetween(ListNode* head, int left, int right) {
     ListNode* dummy = new ListNode(0);

     dummy->next = head;

     ListNode* currNode = head;
     ListNode* leftprev = dummy;

     for(int i =0; i<left-1; i++){
        currNode = currNode->next;
        leftprev = leftprev->next;
     }   

     ListNode* newHead = currNode;
     ListNode* prevNode = NULL;

     for(int i =0; i<=right-left; i++){
        ListNode* nextNode = currNode->next;
        currNode->next = prevNode;
        prevNode = currNode;
        currNode = nextNode;

     }

     leftprev->next = prevNode;
     newHead->next = currNode;
     return dummy->next;
    }
};
