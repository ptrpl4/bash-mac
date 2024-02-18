# 🔢 Algorithms

## Binary search

Binary search is an efficient search algorithm used to find a specific value within a sorted list or array.

* Start with the middle element of the sorted array.
* Compare the middle element with the target value.
* If the target value is equal to the middle element, the search is over – the target is found.
* If the target value is less than the middle element, repeat the process with the lower half of the array.
* If the target value is greater than the middle element, repeat the process with the upper half of the array.
* Repeat these steps until the target value is found or the subarray becomes empty.

Binary search operates with a time complexity of O(log n), where n is the number of elements in the array. This makes it much faster than linear search (which has a time complexity of O(n)) for large datasets, as it effectively halves the search space with each comparison.

The key to binary search is that it takes advantage of the fact that the array is sorted. Each comparison helps to narrow down the search space, which allows the algorithm to quickly locate the target value if it exists within the array .

```python
# example on python
def binary_search(list, item):
    low = 0
    high = len(list) - 1
    while low <= high:
        mid = (low + high)
        guess = list[mid]
        if guess == item:
            return mid
        if guess > item:
            high = mid - 1
        else:
            low = mid + 1
    return None

my_list = [1, 3, 5, 7, 9]

print(binary_search(my_list,3)) # expect 1
```

## Logarithm helper <a href="#firstheading" id="firstheading"></a>

<figure><img src="../../.gitbook/assets/Screenshot 2024-02-09 at 14.04.43.jpeg" alt=""><figcaption></figcaption></figure>

## Big _O_ notation

Used to classify algorithms according to how fast the execution time of the algorithm increases with increasing input data size.

Big O used worst (slowest case)

* Getting an element of a collection is O(1). \
  Whether retrieving by an index in an array, or by a key in a dictionary in Big O notation it is O(1)
* Going through a collection is O(n)
* Nested loops over the same collection is O(n^2)
* Divide and Conquer is always O(log n)
* Iterations that use Divide and Conquer are O(n log n)
