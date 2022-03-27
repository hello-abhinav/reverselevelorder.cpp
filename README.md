# reverselevelorder.cpp
# https://leetcode.com/problems/binary-tree-level-order-traversal-ii/submissions/

  vector<vector<int>> levelOrderBottom(TreeNode* root) {
        vector<int> ans;
        vector<vector<int> >res;
        queue<TreeNode*> q;
        q.push(root);
        if(root==NULL)
        {
            return {}; 
        }
        q.push(NULL);
        while(!q.empty())
        {
            TreeNode* temp=q.front();
            q.pop();
            //it means level is finished
            if(temp==NULL)
            {
                res.push_back(ans);
                ans.clear();
                if(!q.empty())
                {
                    q.push(NULL);
                }
            }
            else{
                ans.push_back(temp->val);
                if(temp->left)
                {
                    q.push(temp->left);
                }
                if(temp->right)
                {
                    q.push(temp->right);
                }
                
            }
        }
        reverse(res.begin(),res.end());
        return res;
        
    }
};
