#### Diagonal Matrix
```
class Solution {
public:
    vector<int> findDiagonalOrder(vector<vector<int>>& mat) {
        bool flag=0;
        int n=mat.size();
        int m=mat[0].size();
        vector<vector<int>>level(n+m-1);
        for(int i=0 ;i<n ;i++)
        {
            for(int j=0 ;j<m ;j++)
            {
                level[i+j].push_back(mat[i][j]);
            }
        }
        vector<int>ans;
        for(auto i: level)
        {
            if(flag==0)
            {
                reverse(i.begin(),i.end());
                flag=1;
            }
            else{
                flag=0;
            }
            for(auto g:i)
            {
                ans.push_back(g);
            }
        }
        return ans;
    }
};
```
