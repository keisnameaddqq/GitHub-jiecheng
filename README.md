# GitHub-jiecheng
#include<bits/stdc++.h>
using namespace std; 

long long mode=1000000007; 
long long fac[3001],finv[3001];
//fac[i]为 (i!)% mode    
//（fac[i+j]*finv[i]）% mode为（fac[i+j]/fac[j]）%mode==((i+j)!/j!)%mode 
//fac[]由 qpow函数实现，看不懂怎么实现的 
long long qpow(long long a,long long b){
    long long ans=1,base=a;
    while(b){
        if(b&1) ans=ans*base%mode;
        base=base*base%mode;
        b>>=1;
    }
    return ans;
}
void init(){
    fac[0]=finv[0]=1;
    for(int i=1;i<=3e3;i++){
        fac[i]=fac[i-1]*i%mode;
        finv[i]=qpow(fac[i],mode-2);
        cout<<"fac["<<i<<"]="<<fac[i]<<endl;
        cout<<"finv["<<i<<"]="<<finv[i]<<endl;
    }
}

int main()
{
 init();
 int n;
 cin>>n;
 for(int i=0;i<n;i++){
  int a,b;
  cin>>a>>b;
  cout<<fac[a]<<" "<<finv[b]<<endl;
  cout<<"(a!/b!)="<<fac[a]*finv[b]%mode<<endl;
 }
 return 0;
}
