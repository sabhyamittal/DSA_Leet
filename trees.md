#### Same tree
```
class Solution {
public:
    bool isSameTree(TreeNode* p, TreeNode* q) {
        if(p==NULL && q==NULL)return true;
        if(p==NULL || q==NULL)return false;
        if(p->val!=q->val) return false;
        return isSameTree(p->left,q->left)&&isSameTree(p->right,q->right);
    }
};
```
#### Symmetric tree
```
class Solution {
public:
    bool solve(TreeNode* r1, TreeNode* r2){
        if(r1 == NULL && r2 == NULL)return true;
        else if(r1 == NULL || r2 == NULL)return false;
        if(r1->val == r2->val){
            return solve(r1->left,r2->right)&&solve(r1->right,r2->left);
        }
        return false;
    }
    bool isSymmetric(TreeNode* root) {
        return solve(root,root);
    }
};
```
#### Binary tree level order traversal
```
class Solution {
public:
    vector<vector<int>> levelOrder(TreeNode* root) {
        vector<vector<int>>ans;
        if(root==NULL)return {};
        queue<TreeNode*>q;
        q.push(root);
        while(!q.empty())
        {
            vector<int>res;
            int j=q.size();
            for(int i=0 ;i<j ;i++)
            {
                auto p=q.front();
                q.pop();
                res.push_back(p->val);
                if(p->left)q.push(p->left);
                if(p->right)q.push(p->right);
            }
            ans.push_back(res);
        }
        return ans;
    }
};
```
#### Binary tree level order traversal 2
```
class Solution {
public:
    vector<vector<int>> levelOrderBottom(TreeNode* root) {
        vector<vector<int>>ans;
        if(root==NULL)return {};
        queue<TreeNode*>q;
        q.push(root);
        while(!q.empty())
        {
            vector<int>res;
            int j=q.size();
            for(int i=0 ;i<j ;i++)
            {
                auto p=q.front();
                q.pop();
                res.push_back(p->val);
                if(p->left)q.push(p->left);
                if(p->right)q.push(p->right);
            }
            ans.push_back(res);
        }
        reverse(ans.begin(),ans.end());
        return ans;
    }
};
```
#### Average of levels in Binary Tree
```
class Solution {
public:
    vector<double> averageOfLevels(TreeNode* root) {
        vector<double>res;
        double avg=0;
        if(root==NULL)return {};
        queue<TreeNode*>q;
        q.push(root);
        while(!q.empty())
        {
            double j=q.size();
            double sum=0;
            for(int i=0 ;i<j ;i++)
            {
                auto p=q.front();
                q.pop();
                sum=sum+p->val;
                if(p->left)q.push(p->left);
                if(p->right)q.push(p->right);
            }
            avg=sum/j;
            res.push_back(avg);
        }
        return res;
    }
};
```
#### Maximum depth of binary tree
```
class Solution {
public:
    int maxDepth(TreeNode* root) {
       if(root==NULL)return 0;
        vector<vector<int>>res;
        queue<TreeNode*>q;
        q.push(root);
        while(!q.empty())
        {
            vector<int>ans;            
            int j=q.size();
            for(int i=0 ;i<j;i++)
            {
                auto p=q.front();
                q.pop();
                ans.push_back(p->val);
                if(p->left)q.push(p->left);
                if(p->right)q.push(p->right);
            }
            res.push_back(ans);
        }
        return res.size();
    }
};
```
