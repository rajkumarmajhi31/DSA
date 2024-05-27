/*
// Definition for a Node.
class Node {
public:
    int val;
    Node* next;
    Node* random;
    
    Node(int _val) {
        val = _val;
        next = NULL;
        random = NULL;
    }
};
*/

class Solution {
public:
    Node* copyRandomList(Node* head) {

        Node* temp = head;
        while(temp){
            Node* newNode = new Node(temp->val);
            newNode->next = temp->next;
            temp->next = newNode;
            temp = temp->next->next;
        }

        temp = head;
        while(temp){
            if(temp->random != NULL){
                temp->next->random = temp->random->next;
                
            }
            else {
                temp->next->random = NULL;
            }

            temp =temp->next->next;
        }
        Node* dummyHead = new Node(-1);
        Node* rest = dummyHead;
        temp= head;

        while(temp){
            rest->next = temp->next;
            temp->next = temp->next->next;

            rest = rest->next;
            temp = temp->next;
        }
        return dummyHead->next;
    }
};
