# DAA
Insertion Sort

/* Online C++ Compiler and Editor */
#include <iostream>
#include <cstdlib>
#include <vector>
#include <algorithm>

using namespace std;

int lins(vector<int> v, int x)
{
    int n = v.size();
    for (int i=0; i<n; i++)
    {
        if (v[i] == x)
            return i + 1;
    }
    return -1;
}

int bins(vector<int> v, int x)
{
    int n = v.size();
    int st = 0;
    int ed = n-1;
    while (st<=ed)
    {
        int mid = (int)(st + ed) / 2;
        cout<<"tr: "<<mid<<endl;
        if (v[mid] == x)
            return mid + 1;
        else if (v[mid]<x)
            st = mid+1;
        else
            ed = mid-1;
    }
    return -1;
}

vector<int> isort(vector<int> v)
{
    int n = v.size();
    for (int i=1; i<n; i++)
    {
        int key = v[i];
        for (int j=i-1; j>-1; j--)
        {
            if (v[j]>key)
            {
                int temp = v[j];
                v[j] = v[j+1];
                v[j+1] = temp;
                key = v[j];
            }
            else
                break;
        }
    }
    return v;
}

int main()
{
    int n;
    vector<int> v = {5, 1, 4, 2, 3};
    n = v.size();
    vector<int> sv = isort(v);
    for (int i=0; i<n; i++)
        cout<<sv[i]<<" ";
    cout<<endl;
    cout<<"Linear Search: "<<lins(v, 2)<<endl;
    cout<<"Binary Search: "<<bins(v, 2)<<endl;
    return 0;
}
