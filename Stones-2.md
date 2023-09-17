* https://atcoder.jp/contests/abc270/tasks/abc270_d
```cpp
const int N=1e4+5,mxn=1e9;
int dp[2][N];
int dfs(int k,int t,int rem,vector<int>&arr){
    if(rem<arr[0])return 0;
    if(dp[t][rem]!=-1){
        return (dp[t][rem]);
    }
    
    if(t==1){
        int ans=0;
        for(int i=k-1;i>=0;i--){
            if(rem-arr[i]>=0){
                ans=max(ans,dfs(k,0,rem-arr[i],arr)+arr[i]);
            }
        }
        return dp[t][rem]=ans;
    }else{
        int ans=mxn;
        for(int i=k-1;i>=0;i--){
            if(rem-arr[i]>=0){
                ans=min(ans,dfs(k,1,rem-arr[i],arr));
            }
        }
        return dp[t][rem]=ans;
    }
}
void solve(){
    memset(dp,-1,sizeof(dp));
    int n,k;cin>>n>>k;
    vector<int>arr(k);
    for(auto &i:arr)cin>>i;   
    print(dfs(k,1,n,arr));
}
```
