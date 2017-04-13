# Check-a-graph-is-acyclic
#include <bits/stdc++.h>
using namespace std;

int dfs(int i,vector<int> m[],int white[],int grey[],int black[]);
int cyclic(vector<int> m[],int white[],int grey[],int black[],int n);

int main() {
    
	int n,t,a,b,i;
	
	cin>>n;
	
	
	vector<int> m[n];
	
	
int white[n];
int grey[n];
int black[n];

	cin>>t;
	
	while(t-->0)
	{
	 cin>>a>>b;
	 m[a].push_back(b);
	}
	
	for( i=0;i<n;i++)
	{
	    white[i]=1;
	    grey[i]=0;
	black[i]=0;
	
	}

	if(cyclic(m,white,grey,black,n))
	cout<<"Cyclic";
	else
	cout<<"Acyclic";
	
	return 0;
	
	
}
int cyclic(vector<int> m[],int white[],int grey[],int black[],int n)
{
    for(int i=0;i<n;i++)
    {
        if(white[i]==1)
        {
            if(dfs(i,m,white,grey,black))
            return 1;
        }
    }
    return 0;
}


int dfs(int i,vector<int> m[],int white[],int grey[],int black[])
{
    
    white[i]=0;
    grey[i]=1;
    
    for(int j=0;j<m[i].size();j++)
    {
        int a=m[i].at(j);
    if(black[a]==1)
    continue;
    
    if(grey[a]==1)
    return 1;
    
    if(dfs(a,m,white,grey,black))
    return 1;
    
    }
    grey[i]=0;
    black[i]=1;
    
    return 0;
    
}

    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
    
