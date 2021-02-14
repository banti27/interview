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

## Next leter
**Problem Statement:**
Given an array of lowercase letters sorted in ascending order, find the smallest letter in the given array greater than a given ‘key’. 
Assume the given array is a circular list, which means that the last letter is assumed to be connected with the first letter. This also means that the smallest letter in the given array is greater than the last letter of the array and is also the first letter of the array.

```
public static char searchNextLetter(char[] letters, char key) {
    int n = letters.length;// length of the array
    
    // return first element when key is smaller than first element or key is greater than last element
    if(key<letters[0]||key>letters[n-1]){
      return letters[0];
    }

    int start = 0;//start index
    int end = n-1;//end index


    while(start<=end){
      int mid = start + (end-start)/2;// mid index
      if(key<letters[mid]){
        end = mid -1;
      }else{
        start = mid+1;
      }
    }

    return letters[start%n];// assuming list is circular so reaminder wil always be less than length
 }
  
```
***
