# SearchinRotatedSortedArrayCodeStudio

int getPivot(vector<int>& arr, int n){

    int s = 0;
    int e = n-1;
    int mid = s + (e-s)/2;

    while(s<e){
        if(arr[mid]>=arr[0]){
            s = mid+1;
        }
        else{
            e = mid;
        }
        mid = s + (e-s)/2;
    }
    return s;
}

int binarysearch(vector<int>& arr, int s, int e, int key){
    int start = s;
    int end = e;
    int mid = start + (end-start)/2;
    while(start<=end){
        if(arr[mid]==key){
            return mid;
        }
        // Go To Right part
        if(key>arr[mid]){
            start = mid + 1;
        }
        // Go To Left part
        else{
            end = mid - 1;
        }
        mid = start + (end-start)/2; // For update the mid
    }
    return -1;
}
    
    
int findPosition(vector<int>& arr, int n, int k)
{
    
    // Return the position of K in ARR else return -1.
    int pivot = getPivot(arr, n);
    if(k >= arr[pivot] && k <= arr[n-1]){
        // Binary Search in First Line
        return binarysearch(arr, pivot, n-1, k);
    }
    else{
        // Binary Search in Second Line
        return binarysearch(arr, 0, pivot-1, k);
    }
}

