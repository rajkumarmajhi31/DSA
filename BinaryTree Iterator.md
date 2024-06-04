/**
 * Definition for a binary tree node.
 * struct TreeNode {
 *     int val;
 *     TreeNode *left;
 *     TreeNode *right;
 *     TreeNode() : val(0), left(nullptr), right(nullptr) {}
 *     TreeNode(int x) : val(x), left(nullptr), right(nullptr) {}
 *     TreeNode(int x, TreeNode *left, TreeNode *right) : val(x), left(left), right(right) {}
 * };
 */
class BSTIterator {
    private:
    vector<int> v;
    int i =0;
    void inOrderTraversal(TreeNode* root) {
        if (root == nullptr) {
            return;
        }
        inOrderTraversal(root->left);
        v.push_back(root->val);
        inOrderTraversal(root->right);
    }

    public:


    BSTIterator(TreeNode* root) {
        inOrderTraversal(root); 
    }
    
    int next() {
            int ans = v[i];
            i++;
            return ans;
    
    }
    
    bool hasNext() {
        return i < v.size();
    }

    
    // same solution but only in vector they are storing the TreeNode*
    // vector<TreeNode*> inorder;
    // int i;
    // int m;

    // BSTIterator(TreeNode* root) {
        
    //     makeIn(root, inorder);
    //     i = -1;
    //     m = inorder.size();
    // }
    
    // void makeIn(TreeNode* ptr, vector<TreeNode*>& inorder){
    //     if(ptr == NULL){
    //         return;
    //     }
        
    //     makeIn(ptr->left, inorder);
    //     inorder.push_back(ptr);
    //     makeIn(ptr->right, inorder);
    //     return;
    // }

    // int next() {
    //     i++;
    //     return inorder[i]->val;
    // }
    
    // bool hasNext() {
    //     return i<m-1;
    // }

    //stack can also be used to solve this problem statement firstly we store all the left element then stack top would be the first most root then after pop of top most element add its right node also for completion of inorder traversal

    
    // stack<TreeNode*>st;
    // void pushAllNodes(TreeNode* root){
    //     while(root!=NULL){
    //         st.push(root);
    //         root=root->left;
    //     }
    // }
    // BSTIterator(TreeNode* root) {
    //     pushAllNodes(root);
    // }
    
    // int next() {
    //     TreeNode* temp=st.top();
    //     st.pop();
    //     pushAllNodes(temp->right);
    //     return temp->val;
    // }
    
    // bool hasNext() {
    //     return !st.empty();
    // }

    
};

/**
 * Your BSTIterator object will be instantiated and called as such:
 * BSTIterator* obj = new BSTIterator(root);
 * int param_1 = obj->next();
 * bool param_2 = obj->hasNext();
 */
