# Searching Algorithms

## Intro

Searching algorithms are designed to check for an element or retrieve an element from any data structure where it is stored. <br>
These algorithms are generally classified into two categories:

1. **Sequential Search**: The elements are traversed sequentially and every element is checked. e.g. linear search.
2. **Interval Search**: These algorithms are specifically designed for searching in sorted data-structures. e.g. binary search.

## Algorithms

### Linear Search

- Just check out the element one by one, simple and straightforward.
- Time complexity: O(n)
- Rarely used practically because there are usually faster searching algorithms.

### Binary Search

- Search a sorted array by repeatedly dividing the search interval in half. Begin with an interval covering the whole array. If the value of the search key is less than the item in the middle of the interval, narrow the interval to the lower half. Otherwise narrow it to the upper half. Repeatedly check until the value is found or the interval is empty.
- Time complexity: O(log n)
