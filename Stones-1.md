* https://atcoder.jp/contests/dp/tasks/dp_k
```cpp
const int N=1e5+5;
int dp[2][N];
int dfs(int t,int rem,int n,vector<int>&arr){
    if(rem<arr[0]){
        if(t==1)return 0;
        else return 1;
    }
    if(dp[t][rem]!=-1)return dp[t][rem];
    if(t==1){
        for(int i=0;i<n;i++){
            if(rem-arr[i]>=0){
                int res=dfs(0,rem-arr[i],n,arr);
                if(res==1){
                    return dp[t][rem]=1;
                }
            }
        }
        return  dp[t][rem]=0;
    }else{
        for(int i=0;i<n;i++){
            if(rem-arr[i]>=0){
                int res=dfs(1,rem-arr[i],n,arr);
                if(res==0){
                    return  dp[t][rem]=0;
                }
            }
        }
        return  dp[t][rem]=1;
    }
}
void solve(){
    memset(dp,-1,sizeof(dp));
    int n,k;cin>>n>>k;
    vector<int>arr(n);
    for(auto &i:arr)cin>>i; 
    int res=dfs(1,k,n,arr);
    if(res==1)print("First");
    else print("Second");
}
```

```cpp
const int N=1e5+5;
int dp[2][N];
int dfs(int t,int rem,int n,vector<int>&arr){
    if(rem<arr[0]){
        if(t==1)return 0;
        else return 1;
    }
    if(dp[t][rem]!=-1)return dp[t][rem];
    
    for(int i=0;i<n;i++){
        if(rem-arr[i]>=0){
            int res=dfs(!t,rem-arr[i],n,arr);
            if(res==t){
                return dp[t][rem]=t;
            }
        }
    }
    return  dp[t][rem]=!t;
   
}
void solve(){
    memset(dp,-1,sizeof(dp));
    
    int n,k;cin>>n>>k;
    vector<int>arr(n);
    for(auto &i:arr)cin>>i; 

    int res=dfs(1,k,n,arr);
    if(res==1)print("First");
    else print("Second");
}
```

```cpp
const int N=1e5+5;
int dp[N];
vector<int>arr;
int dfs(int rem){
    if(rem<arr[0]){
        return 0;
    }
    if(dp[rem]!=-1)return dp[rem];
    for(auto i:arr){
        if(rem-i>=0 and !dfs(rem-i)){
            return dp[rem]=1;
        }
    }
    return dp[rem]=0;
   
}
void solve(){
    memset(dp,-1,sizeof(dp));

    int n,k;cin>>n>>k;
    arr.resize(n);
    for(int i=0;i<n;i++){
        cin>>arr[i];
    }
    
    if(dfs(k))print("First");
    else print("Second");
}
```

```cpp
const int N=1e5+5;
int dp[N];

void solve(){
    int n,k;cin>>n>>k;
    vector<int>arr(n);
    for(int i=0;i<n;i++){
        cin>>arr[i];
    }

    for(int i=1;i<=k;i++){
        for(auto x:arr){
            if(i-x>=0 and dp[i-x]==0){
                dp[i]=1;
            }
        }
    }
    
    if(dp[k])print("First");
    else print("Second");
}
```
