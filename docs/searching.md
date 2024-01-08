# Searching Algorithms

https://www.geeksforgeeks.org/searching-algorithms/

## Intro

Searching algorithms are designed to check for an element or retrieve an element from any data structure where it is stored. <br>
These algorithms are generally classified into two categories:

1. **Sequential Search**: The elements are traversed sequentially and every element is checked. e.g. linear search.
2. **Interval Search**: These algorithms are specifically designed for searching in sorted data-structures. e.g. binary search.

## Linear Search

- Just check out the element one by one, simple and straightforward.
- Time complexity: O(n)
- Rarely used practically because there are usually faster searching algorithms.

## Binary Search

- Search a sorted array by repeatedly dividing the search interval in half. Begin with an interval covering the whole array. If the value of the search key is less than the item in the middle of the interval, narrow the interval to the lower half. Otherwise narrow it to the upper half. Repeatedly check until the value is found or the interval is empty.
- Time complexity: O(log n)

## Jump Search

- Like Binary Search, Jump Search is another searching algorithm for sorted arrays. The basic idea is to check fewer elements by jumping ahead by fixed steps or skipping some elements in place of searching all elements.<br>

  e.g. Consider the array [0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144, 233, 377, 610](16 elements). Say you want to find the value of 55 and the block size to be jumped is 4, you need to do the following steps:

  1. Jump from index 0 to 4.
  2. Jump from index 4 to 8.
  3. Jump from index 8 to 12.
  4. Now, since the element at index 12(144) is greater than 55, we will jump back a step to come to index 8
  5. Perform linear search from index 8 to 12 and get the element 55.

- The best block size to be skipped.
  In the worst case, we have to do `n/m` jumps and if the last checked value is greater than the element to be searched for, we perform `m-1` comparisons more for linear search. Therefore the total number of comparisons in the worst case will be `((n/m) + m-1)`. The value of the function `((n/m) + m-1)` will be minimum when `m = √n`. Therefore, the best step size is `m = √n`. Also its time complexity is O(√n).

- Binary Search is better than Jump Search, but Jump search has an advantage that we traverse back only once (Binary Search may require up to O(Log n) jumps, consider a situation where the element to be searched is the smallest element or smaller than the smallest). So in a system where binary search is costly, we use Jump Search.

## Interpolation Search

- Interpolation search is an improvement over binary search for instances, where the values in a sorted array are uniformly distributed. Binary search always goes to the middle element to check, while interpolation search may go to different locations according to the value of the key being searched. For example, if the value of the key is closer to the last element, interpolation search is likely to start search toward the end side.

- To find the position to be searched, it uses following formula:

```
pos = lo + ((x - arr[lo]) * (hi - lo) / (arr[hi] - arr[lo]))
arr[] - Array where elements need to be searched
x - The element to be searched
lo - Starting index in arr[]
hi - Ending index in arr[]
```

- Steps

1. In a loop, calculate the value of `pos` using the above formula.
2. If it is a match, return the index of the item.
3. If the item is less than `arr[pos]`, calculate he probe position of the left sub-array. Otherwise, calculate the same in the right sub-array.
4. Repeat until a match is found or the sub-array reduces to zero.

- Time complexity: If elements are uniformly distributed, then O(log(logn)). In worse case, it can take O(n).

## Exponential Search

- The name of the searching algorithm may be misleading as it works in O(log n) time.
- It involves two steps: Find range where element is present and do binary search in the above range.
- How to find the range where element may be present? The idea is to start with sub-array size 1, compare its last element with x, then try size 2, then 4 and so on until last element of a sub-array is not greater. Once we find an index i, we know that the element must be present between i/2 and i.
