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


