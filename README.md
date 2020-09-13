# B.-Maximum-Product
#include <bits/stdc++.h>
using namespace std;
#define ull unsigned long long
 
struct pair1{
 
    int data;
    int sign;
    pair1(){
    data=0;
    sign=1;
    }
    pair1(int d,int s){
        data=abs(d);
        sign=s;
    }
 
};
 
bool cmp(pair1 first,pair1 second){
 
    if(first.data!=second.data){
        return first.data<second.data;
    }else{
        return first.sign<second.sign;
    }
 
}
 
int main(){
 
    int t;
    cin>>t;
    while(t--){
        int n;
        long long multi=1;
        cin>>n;
        vector<pair1> A(n);
        int x;
        for(int i=0;i<n;i++){
            cin>>x;
            int s;
            if(x>=0){
                s=1;
            }else s=-1;
            A[i]=pair1(x,s);
        }
        sort(A.begin(),A.end(),cmp);
        vector<int> ans;
        int negetive=0;
        int index;
        int p;
        for(int i=n-1;i>=n-5;i--){
            ans.push_back(A[i].data);
            if(A[i].sign==-1){
                negetive++;
                index=ans.size()-1;
            }else{
                p=ans.size()-1;
            }
 
        }
        if(negetive%2==0){
 
            for(int i=0;i<ans.size();i++){
                multi*=ans[i];
            }
            cout<<multi<<endl;
        }else{
 
            if(A.size()>5){
 
                if(negetive==5){
                        int flag=0;
                    for(int i=n-6;i>=0;i--){
                        if(A[i].sign==1){
                            ans[index]=A[i].data;
                            flag=1;
                            break;
                        }
                    }
                    if(flag==1){
                        long long multi=1;
                        for(int i=0;i<ans.size();i++){
                            multi*=ans[i];
                        }
                        cout<<multi<<endl;
                    }else{
 
                        for(int i=0;i<5;i++){
                            multi*=A[i].data;
                        }
                        multi=(-1)*multi;
                        cout<<multi<<endl;
                    }
                }
                else{
                        int index2=-1;
                        int index3=-1;
                        long long multi2=1;
                        long long multi3=1;
 
                        for(int i=n-6;i>=0;i--){
                            if(A[i].sign==1){
                               index2=i;
                                break;
                            }
                        }
                        if(index2>=0){
                            for(int i=0;i<ans.size();i++){
                                    if(i==index){
                                        multi2*=A[index2].data;
                                    }else
                                multi2*=ans[i];
                            }
 
                        }
                        for(int i=n-6;i>=0;i--){
                            if(A[i].sign==-1){
                               index3=i;
                                break;
                            }
                        }
                        if(index3>=0){
                            for(int i=0;i<ans.size();i++){
                                    if(i==p){
                                        multi3*=A[index3].data;
                                    }else
                                multi3*=ans[i];
                            }
                        }
                        if(index2==-1){
                            multi=multi3;
                        }else if(index3==-1){
                            multi=multi2;
                        }else{
                            if(multi2>multi3){
                                multi=multi2;
                            }else multi=multi3;
                        }
                        cout<<multi<<endl;
 
                }
 
            }else{
 
                long long multi=1;
            for(int i=0;i<ans.size();i++){
                multi*=ans[i];
            }
            multi=(-1)*multi;
            cout<<multi<<endl;
 
            }
 
        }
    }
    }
 
 
 
