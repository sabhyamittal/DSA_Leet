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
OR
```
int maxDepth(TreeNode*root)
{
if(root==NULL)return 0;
int lh=maxDepth(root->left);
int rh=maxDepth(root->right);
return 1+max(lh,rh);
}
```
#### Zigzag order traversal
```
class Solution {
public:
    vector<vector<int>> zigzagLevelOrder(TreeNode* root) {
        
        vector<vector<int>>ans;
        if(root==NULL)return {};
        queue<TreeNode*>q;
        q.push(root);
        while(!q.empty())
        {
            int j=q.size();
            vector<int>res;
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
        for(int i=0;i<ans.size();i++)
        {
          if(i%2!=0){
              reverse(ans[i].begin(),ans[i].end());
          }
       }
        return ans;
    }
};
```
#### Minimum depth of binary tree
```
class Solution {
public:
    int minDepth(TreeNode* root) {
       if(root==NULL)return 0;
        queue<TreeNode*>q;
        q.push(root);
        int depth=0;
        while(!q.empty())
        {           
            int j=q.size();
            for(int i=0 ;i<j;i++)
            {
                auto p=q.front();
                q.pop();
                if(p->left==NULL && p->right==NULL)return depth+1;
                if(p->left)q.push(p->left);
                if(p->right)q.push(p->right);
            }       
            depth++;
        }
        return depth;
    }
};
```
#### Path Sum
```
class Solution {
public:
    bool hasPathSum(TreeNode* root, int targetSum) {
        if(root==NULL)return false;
        if(root->left==NULL && root->right==NULL && targetSum-root->val==0)return true;
        return hasPathSum(root->left , targetSum-root->val)|| hasPathSum(root->right, targetSum-root->val);
    }
};
```
#### Balanced Binary Tree
```
class Solution {
public:
    int check(TreeNode*root)
    {
        if(root==NULL) return 0;
        int lh=check(root->left);
        if(lh==-1)return -1;
        int rh=check(root->right);
        if(rh==-1)return -1;
        if(abs(lh-rh)>1)return -1;
        return max(lh,rh)+1;
    }
    bool isBalanced(TreeNode* root) {
        return check(root) !=-1;
    }
};
```
#### Diameter of Binary Tree
```
class Solution {
public:
    int diameterOfBinaryTree(TreeNode* root) {
        int maxi=0;
        dia(root,maxi);
        return maxi;
    }
    int dia(TreeNode*root,int &maxi){
        if(root==NULL)return 0;
        int lh=dia(root->left,maxi);
        int rh=dia(root->right,maxi);
        maxi=max(maxi,(lh+rh));
        return 1+max(lh,rh);
    }
};

```

