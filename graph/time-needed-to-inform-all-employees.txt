class Solution {
public:
    unordered_map<int,vector<int>> adj;
    int maxi = 0, ans = 0;
    
    void dfs(int mng,vector<int>& informTime){
        maxi = max(maxi,ans);
        for(auto emp : adj[mng]){
            ans += informTime[mng];
            dfs(emp,informTime);
            ans -= informTime[mng];
        }
    }

    int numOfMinutes(int n, int headID, vector<int>& manager, vector<int>& informTime) {
        // Ajacency List
        for(int i=0;i<n;i++){
            int mng = manager[i];
            // Checking for headID
            if(mng!=-1){
                adj[mng].push_back(i);
            }
        }
        dfs(headID,informTime);
        return maxi;
    }
};