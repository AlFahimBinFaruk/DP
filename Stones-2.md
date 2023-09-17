* https://atcoder.jp/contests/abc270/tasks/abc270_d
```cpp
const int N=1e4+5,mxn=1e9;
int dp[2][N];
vector<int>arr;
int dfs(int t,int rem){
    if(rem<arr[0])return 0;
    if(dp[t][rem]!=-1){
        return (dp[t][rem]);
    }
    
    if(t==1){
        int ans=0;
        for(auto i:arr){
            if(rem-i>=0){
                ans=max(ans,dfs(0,rem-i)+i);
            }
        }
        return dp[t][rem]=ans;
    }else{
        int ans=mxn;
        for(auto i:arr){
            if(rem-i>=0){
                ans=min(ans,dfs(1,rem-i));
            }
        }
        return dp[t][rem]=ans;
    }
}

void solve(){
    memset(dp,-1,sizeof(dp));
    int n,k;cin>>n>>k;
    arr.resize(k);
    for(int i=0;i<k;i++){
        cin>>arr[i];
    }
    print(dfs(1,n));
}
```

```cpp
const int N=1e4+5,mxn=1e9;
int dp[N];
vector<int>arr;
int dfs(int rem){
    if(rem<arr[0])return 0;
    if(dp[rem]!=-1)return dp[rem];
    int ans=0;
    for(auto i:arr){
        if(rem-i>=0){
            ans=max(ans,rem-dfs(rem-i));
        }
    }
    return dp[rem]=ans;
}

void solve(){
    memset(dp,-1,sizeof(dp));
    int n,k;cin>>n>>k;
    arr.resize(k);
    for(int i=0;i<k;i++){
        cin>>arr[i];
    }
    print(dfs(n));
}
```

```cpp
const int N=1e4+5,mxn=1e9;
int dp[N];
void solve(){
    int n,k;cin>>n>>k;
    vector<int>arr(k);
    for(int i=0;i<k;i++){
        cin>>arr[i];
    }
    for(int i=1;i<=n;i++){
        for(auto item:arr){
            if(i-item>=0){
                dp[i]=max(dp[i],i-dp[i-item]);
            }
        }
    }
    print(dp[n]);
}
```

