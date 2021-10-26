# C-Exponential-Search
C++ Exponential Search

#include <bits/stdc++.h>
using namespace std;

//exponential search

int binarySearch(int arr[],int key, int start, int end){
    if(arr[start]==key){
        return start;
    }
    if(start<=end){
        int midIndex=start+(end-start)/2;
        if(arr[midIndex]==key){
            return midIndex;
        }else if(arr[midIndex]<key){
            return binarySearch(arr,key,midIndex+1,end);
        }else{
            return binarySearch(arr,key,start,midIndex-1);
        }
    }
    return -1;
}
int exponentialSearch(int arr[],int size, int key,int i=1,bool flag=false){
    if(arr[0]==key){
        return 0;
    }
    while(i<size){
        if(arr[i]==key){
            flag=true;
            return i;
        }else{
            i=i*2;
        }
    }
    if(flag==false){
        return binarySearch(arr, key, i/2,size-1);
    }
}

int main(){
    int size;
    cout<<"Enter Size of array: ";
    cin>>size;
    
    int arr[size];
    cout<<"Enter array elements(sorted): ";
    for(int i=0;i<size;++i){
        cin>>arr[i];
    }
    int key;
    cout<<"Enter key: ";
    cin>>key;
    
    cout<<exponentialSearch(arr,size,key);
    return 0;
}
