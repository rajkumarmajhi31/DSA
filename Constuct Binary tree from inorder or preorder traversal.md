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
class Solution {
public:
    TreeNode* buildTree(vector<int>& preorder, vector<int>& inorder) {
        
        unordered_map<int,int> m;
        for(int i =0; i<inorder.size(); i++){
            m[inorder[i]] = i;
        }

        TreeNode* root = buildnewTree(preorder, 0, preorder.size()-1,inorder , 0, inorder.size()-1,m);
        return root;
    }

    TreeNode* buildnewTree( vector<int>& preorder, int prestart, int preEnd, vector<int>& inorder, int instart, int inEnd, unordered_map<int, int>& m){

          if(prestart>preEnd || instart>inEnd){
            return NULL;
        }
        TreeNode* root = new TreeNode(preorder[prestart]);
      
        int inshot = m[preorder[prestart]];
        int numberleft = inshot- instart;

        root->left = buildnewTree( preorder, prestart+1, prestart+numberleft, inorder, instart, inshot-1,m);
        root->right = buildnewTree(preorder, prestart+numberleft+1, preEnd, inorder, inshot+1, inEnd,m);
        return root;
    }

};
