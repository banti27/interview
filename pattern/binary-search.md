## Order-agnostic Binary Search 

**Problem Statement:**
Given a sorted array of numbers, find if a given number ‘key’ is present in the array. Though we know that the array is sorted, we don’t know if it’s sorted in ascending or descending order. You should assume that the array can have duplicates.

```
  public static int search(int[] arr, int key) {
    int start = 0;
    int end = arr.length - 1;
    boolean isAsc = arr[start] < arr[end];
    
    while (start <= end) {
      // calculate the middle of the current range
      int mid = start + (end - start) / 2;

      // return the index if found
      if (key == arr[mid])
        return mid;
      
      // solve for assending order
      if (isAsc) { 
        if (key < arr[mid]) {
          end = mid - 1; // the 'key' can be in the first half
        } else { // key > arr[mid]
          start = mid + 1; // the 'key' can be in the second half
        }
      }
      // solve for descending order
      else {         
        if (key > arr[mid]) {
          end = mid - 1; // the 'key' can be in the first half
        } else { // key < arr[mid]
          start = mid + 1; // the 'key' can be in the second half
        }
      }
    }
    return -1; // element not found
  }
```
***

## Ceiling of a Number
**Problem Statement:**
Given an array of numbers sorted in an ascending order, find the ceiling of a given number ‘key’. The ceiling of the ‘key’ will be the smallest element in the given array greater than or equal to the ‘key’.

```
  public static int searchCeilingOfANumber(int[] arr, int key) {
    int start = 0;
    int end = arr.length-1;

    if(key>arr[end])
      return -1;// no celing found as ceiling should be grater than or equal to the key

    while(start<=end){
      int mid = start + (end-start)/2;

      if(key<arr[mid]){
        end = mid-1;
      }else if(key>arr[mid]){
        start = mid+1;// this index moves the pointer to the next grater element
      }else{
        return mid;// found ceiling
      }
    }
    return start;// ceiling: the next greater element is the element present at the start index
  }
```

