class LRUCache {
public:
    class node {
    public:
    
        int key;
        int val;
        node* next;
        node* prev;

        node(int _key, int _val){
            key = _key;
            val = _val;
        }
    };

    node* head = new node(-1,-1);
    node* tail = new node(-1,-1);

    unordered_map<int, node*> m;
    int cap ;

    LRUCache(int capacity) {

        cap = capacity;
        head->next = tail;
        tail->prev = head;
        
    }

    void addnode (node* newNode){
        node* temp = head->next;
        newNode->prev = head;
        newNode->next = temp;
        temp->prev = newNode;
        head->next = newNode;
    }

    void deletenode( node* delnode){
        node* delprev = delnode->prev;
        node* delnext = delnode->next;
        delprev->next = delnext;
        delnext->prev = delprev;

    }
    
    int get(int key) {

       if( m.find(key)!= m.end()){
         node* address = m[key];
        int res = address->val;
        m.erase(key);
        deletenode(address);
        addnode(address);
        m[key] = head->next;
        return res;
        }
        return -1;
    }
    
    void put(int key, int value) {
        if(m.find(key) != m.end()){
            node* address = m[key];
            m.erase(key);
            deletenode(address);
        }
        if(cap== m.size()){
            m.erase(tail->prev->key);
            deletenode(tail->prev);
        }

        addnode(new node(key, value));
        m[key] = head->next;
    }
};

/**
 * Your LRUCache object will be instantiated and called as such:
 * LRUCache* obj = new LRUCache(capacity);
 * int param_1 = obj->get(key);
 * obj->put(key,value);
 */
