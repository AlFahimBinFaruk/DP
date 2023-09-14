* https://atcoder.jp/contests/dp/tasks/dp_k
```cpp
#include <bits/stdc++.h>
using namespace std;

#define nl "\n"
#define print(x) cout<<x<<nl
#define fastio() ios_base::sync_with_stdio(false);cin.tie(NULL);cout.tie(NULL)

#ifndef ONLINE_JUDGE
#include "../debug.h"
#else
#define debug(x)
#endif
/*--------------------------------------------------------
                                    Code starts from here.
--------------------------------------------------------------------------------------*/
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

signed main(){
    fastio();
    int t=1;
    while(t--)solve();
}
```

```cpp
#include <bits/stdc++.h>
using namespace std;

#define nl "\n"
#define print(x) cout<<x<<nl
#define fastio() ios_base::sync_with_stdio(false);cin.tie(NULL);cout.tie(NULL)

#ifndef ONLINE_JUDGE
#include "../debug.h"
#else
#define debug(x)
#endif
/*--------------------------------------------------------
                                    Code starts from here.
--------------------------------------------------------------------------------------*/
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

signed main(){
    fastio();
    int t=1;
    while(t--)solve();
}
```
