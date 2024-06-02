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

    vector<int> rightSideView(TreeNode* root) {
        
        vector<vector<int>> arr;
        queue<TreeNode*> q;
        vector<int> ans;

        if(root== NULL){
            return ans;
        }
        q.push(root);

        while(!q.empty()){
            int size = q.size();
             vector<int> level;

            for(int i =0; i<size; i++){
                TreeNode* front = q.front();
                q.pop();
                level.push_back(front->val);

                if(front->left){
                    q.push(front->left);
                }
                if(front->right){
                    q.push(front->right);
                }
            }

            arr.push_back(level);
        }

        

        for(int i =0; i<arr.size(); i++){
           int index = arr[i].size()-1;
           ans.push_back(arr[i][index]);
        }

        return ans;

    }
};
