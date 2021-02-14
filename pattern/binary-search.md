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
***

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
## Number range
**Problem Statement:**
Given an array of numbers sorted in ascending order, find the range of a given number ‘key’. The range of the ‘key’ will be the first and last position of the ‘key’ in the array.

```
public static int[] findRange(int[] arr, int key) {
    int[] result = new int[] { -1, -1 };
    result[0] = search(arr,key,false);// get the lower bound
    
    // check for the lower bound if it is present otherwise key not found
    if(result[0]!=-1){
      result[1]=search(arr,key,true);// get the upper bound
    }
    return result;
  }

  private static int search(int[] arr, int key, boolean isMax){
    int n = arr.length-1;
    int start = 0;
    int end = n-1;
    int index = -1;// index of the lower or upper bound
    
    while(start<=end){
      int mid = start + (end-start)/2;
      if(key<arr[mid]){
        end = mid-1;
      }else if(key>arr[mid]){
        start = mid+1;
      }else{
      // modification for getting the lower and upper bound
        index=mid;
        if(isMax){
          start=mid+1;// to get upper move right till the key is found
        }else{
          end=mid-1;// to get lower move left till the key is found 
        }
      }
    }
    return index;
  }
 ```
 ***

## Search in a Sorted Infinite Array
**Problem Statement:**
Given an infinite sorted array (or an array with unknown size), find if a given number ‘key’ is present in the array. Write a function to return the index of the ‘key’ if it is present in the array, otherwise return -1.

```
  public static int search(ArrayReader reader, int key) {
    int start = 0; 
    int end = 1;
    
    // need to find the boundary
    // looping till we found the boundary
    while(reader.get(end)<key){
      int newStart = end+1;
      
      // max index is the => end + (length of the current boundary) * 2
      end+=(end-start+1)*2;
      
      // update the start index
      start=newStart;
    }
    
    // now we know the boundary then search the element in the array
    return binarySerach(reader, key, start, end);
  }

  public static int binarySerach(ArrayReader reader, int key, int start, int end){
    while(start<=end){
      int mid = start+(end-start)/2;
      if(key<reader.get(mid)){
        end=mid-1;
      }else if(key>reader.get(mid)){
        start=mid+1;
      }else{
        return mid;
      }
    }
    return -1;
  }
```
***

## Minimum Difference Element
**Problem Statement:**
Given an array of numbers sorted in ascending order, find the element in the array that has the minimum difference with the given ‘key’.

```
  public static int searchMinDiffElement(int[] arr, int key) {
    if (key < arr[0])
      return arr[0];
    if (key > arr[arr.length - 1])
      return arr[arr.length - 1];

    int start = 0, end = arr.length - 1;
    while (start <= end) {
      int mid = start + (end - start) / 2;
      if (key < arr[mid]) {
        end = mid - 1;
      } else if (key > arr[mid]) {
        start = mid + 1;
      } else {
        return arr[mid];
      }
    }

    // at the end of the while loop, 'start == end+1'
    // we are not able to find the element in the given array
    // return the element which is closest to the 'key'
    if ((arr[start] - key) < (key - arr[end]))
      return arr[start];
    return arr[end];
  }
```
***








