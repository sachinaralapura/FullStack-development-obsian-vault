#### O(1) - **Constant Time**
The time taken is constant, regardless of the input size. Example: Accessing an element in an array by its index. This occurs when a program takes constant time to execute. It is independent of the input size.

```js
function getFirstElement(arr) {
  // This operation takes the same amount of time whether the array has 1 element or 1 million elements.
  return arr[0];
}
const smallArray = [10, 20, 30];
const largeArray = Array.from({ length: 1000000 }, (_, i) => i + 1);
console.log("O(1) Example (JS):");
console.log(getFirstElement(smallArray)); // Output: 10
```

Accessing an element in an array by its index is a fundamental operation. The computer's memory architecture allows direct calculation of the memory address for any element given its base address and index. This calculation takes a fixed number of CPU cycles, irrespective of how many elements are in the array. Thus, it's considered constant time.

---
#### O(logn) - **Logarithmic Time**

The time taken grows logarithmically with the input size. This often happens when the problem size is halved in each step. Example: Binary search.

**Example: Binary Search**
```js
function binarySearch(arr, target) {
  let low = 0;
  let high = arr.length - 1;

  while (low <= high) {
    const mid = Math.floor((low + high) / 2);
    if (arr[mid] === target) {
      return mid; // Found
    } else if (arr[mid] < target) {
      low = mid + 1; // Discard left half
    } else {
      high = mid - 1; // Discard right half
    }
  }
  return -1; // Not found
}

const sortedArray = Array.from({ length: 1024 }, (_, i) => i * 2); // 0, 2, 4, ..., 2046

console.log("\nO(log n) Example (JS - Binary Search):");
console.log(binarySearch(sortedArray, 500)); // Output: 250 (index of 500)
console.log(binarySearch(sortedArray, 1)); // Output: -1
```

**Explanation (O(logn)):** Binary search works on a sorted array by repeatedly dividing the search interval in half. With each comparison, the possible range where the target might be found is reduced by half. For an array of size n:

- After 1 comparison, the search space is n/2.
- After 2 comparisons, the search space is n/4.
- ...
- After k comparisons, the search space is n/2k. In the worst case, the algorithm stops when the search space is reduced to 1 element. So, n/2k=1⟹n=2k⟹k=log2​n. This logarithmic relationship means that even for very large inputs, the number of operations doesn't grow dramatically. For example, if n is a million, log2​(1,000,000) is roughly 20.

---
#### O(n) - **Linear Time**
The time taken grows linearly with the input size. When n is very large, constant values become negligible. Therefore, an+b≈n
	
**Example: Summing Array Elements**

```js
function sumArrayElements(arr) {
  let sum = 0;
  // We need to visit each element once to add it to the sum.
  for (let i = 0; i < arr.length; i++) {
    sum += arr[i];
  }
  return sum;
}

const smallArray = [1, 2, 3];
const largeArray = Array.from({ length: 1000000 }, (_, i) => i + 1);

console.log("\nO(n) Example (JS):");
console.log(sumArrayElements(smallArray)); // Output: 6
console.log(sumArrayElements(largeArray)); // Output: 500000500000 (takes longer for large array)
```
**Explanation (O(n)):** To sum all elements in an array, you must examine each element exactly once. If the array has n elements, you perform n addition operations (and n access operations). Therefore, the time taken is directly proportional to n.

---
#### O(nlogn) - **Linearithmic Time**
Common in efficient sorting algorithms. Example: Merge Sort, Quick Sort (average case).

**Example: Merge Sort**
```js
function mergeSort(arr) {
  if (arr.length <= 1) {
    return arr;
  }

  const mid = Math.floor(arr.length / 2);
  const left = arr.slice(0, mid);
  const right = arr.slice(mid);

  // Recursively sort halves (log n depth)
  const sortedLeft = mergeSort(left);
  const sortedRight = mergeSort(right);

  // Merge the sorted halves (n operations per merge level)
  return merge(sortedLeft, sortedRight);
}

function merge(left, right) {
  let result = [];
  let leftIndex = 0;
  let rightIndex = 0;

  while (leftIndex < left.length && rightIndex < right.length) {
    if (left[leftIndex] < right[rightIndex]) {
      result.push(left[leftIndex]);
      leftIndex++;
    } else {
      result.push(right[rightIndex]);
      rightIndex++;
    }
  }

  return result.concat(left.slice(leftIndex)).concat(right.slice(rightIndex));
}

const unsortedArray = [38, 27, 43, 3, 9, 82, 10];
const largeUnsortedArray = Array.from({ length: 100000 }, () => Math.floor(Math.random() * 100000));

console.log("\nO(n log n) Example (JS - Merge Sort):");
console.log(mergeSort(unsortedArray)); // Output: [3, 9, 10, 27, 38, 43, 82]
// mergeSort(largeUnsortedArray); // Would take noticeable time but still efficient for its size
```
**Explanation (O(nlogn)):** Merge Sort works by:
1. **Divide:** Recursively dividing the array into two halves until individual elements are reached. This division process creates a logarithmic number of levels in the recursion tree (logn levels, similar to binary search).
2. **Conquer (Merge):** Merging the sorted halves back together. At each level of the recursion tree, the merging operation involves iterating through all elements at that level. Summing up the operations at each level, each level of merging requires O(n) comparisons/operations to combine the sub-arrays.
Since there are logn levels of division/merging, and each level involves roughly n operations, the total time complexity becomes O(nlogn).

---
#### O(n2) - **Quadratic Time**

The time taken grows quadratically with the input size. Often seen with nested loops. Example: Bubble Sort, Insertion Sort, Selection Sort. When n is very large, the n2 term is the most dominating. So, an2+bn+c≈n2

**Example: Bubble Sort**
```js
function bubbleSort(arr) {
  const n = arr.length;
  // Outer loop runs n times
  for (let i = 0; i < n - 1; i++) {
    // Inner loop runs approximately n times for each outer loop iteration
    for (let j = 0; j < n - 1 - i; j++) {
      if (arr[j] > arr[j + 1]) {
        // Swap elements
        [arr[j], arr[j + 1]] = [arr[j + 1], arr[j]];
      }
    }
  }
  return arr;
}

const unsortedArray = [64, 34, 25, 12, 22, 11, 90];
console.log("\nO(n^2) Example (JS - Bubble Sort):");
console.log(bubbleSort(unsortedArray)); // Output: [11, 12, 22, 25, 34, 64, 90]

// For a large array (e.g., 10000 elements), this would be 10000^2 = 100,000,000 operations, which is slow.
```
**Explanation (O(n2)):** In Bubble Sort, there are two nested loops. The outer loop runs `n−1` times. The inner loop, in the worst case, runs approximately n times for each iteration of the outer loop (it does `n−1` then `n−2`, etc., down to 1). The total number of comparisons (and potential swaps) is roughly
`(n−1)+(n−2)+⋯+1=n(n−1)/2=(n2−n)/2`. As n gets very large, the n2 term dominates, and constant factors and lower-order terms are ignored in Big O notation, leading to O(n2).

---
#### O(2n) - **Exponential Time**

The time taken grows exponentially with the input size. These algorithms are usually impractical for anything but very small inputs. Example: Solving the Traveling Salesperson Problem using brute force.

**Example: Recursive Fibonacci Number Calculation (Naive)**
```js
function fibonacciRecursive(n) {
  // Base cases
  if (n <= 1) {
    return n;
  }
  // This function calls itself twice for each n-2, leading to exponential growth
  return fibonacciRecursive(n - 1) + fibonacciRecursive(n - 2);
}

console.log("\nO(2^n) Example (JS - Naive Fibonacci):");
console.log(fibonacciRecursive(5));  // Output: 5 (0, 1, 1, 2, 3, 5)
console.log(fibonacciRecursive(10)); // Output: 55
// console.log(fibonacciRecursive(40)); // This would take a very long time
```
**Explanation (O(2n)):** The naive recursive Fibonacci calculation has a time complexity of `O(2n)` because of redundant calculations. To calculate `fib(n)`, it calls `fib(n-1)` and `fib(n-2)`. `fib(n-1)` in turn calls `fib(n-2)` and `fib(n-3)`, and so on. Notice that `fib(n-2)` is calculated multiple times. The call tree for `fib(n)` grows exponentially. Each node in the recursion tree (except leaves) typically branches into two more calls. The depth of the tree is n, and the number of nodes (representing function calls) roughly doubles at each level.

---
#### O(n!) - **Factorial Time**

Even slower than exponential time, often involves checking all permutations.
**Example: Generating all Permutations of an Array**
```js
function generatePermutations(arr) {
  const result = [];

  function backtrack(currentPermutation, remainingElements) {
    if (remainingElements.length === 0) {
      result.push([...currentPermutation]); // Add a copy
      return;
    }

    for (let i = 0; i < remainingElements.length; i++) {
      const char = remainingElements[i];
      currentPermutation.push(char);
      // Create a new array without the current character
      const newRemaining = remainingElements.slice(0, i).concat(remainingElements.slice(i + 1));

      backtrack(currentPermutation, newRemaining);
      currentPermutation.pop(); // Backtrack
    }
  }

  backtrack([], arr);
  return result;
}

console.log("\nO(n!) Example (JS - Permutations):");
console.log(generatePermutations([1, 2, 3]));
/* Output:
[
  [ 1, 2, 3 ],
  [ 1, 3, 2 ],
  [ 2, 1, 3 ],
  [ 2, 3, 1 ],
  [ 3, 1, 2 ],
  [ 3, 2, 1 ]
]
*/
// console.log(generatePermutations([1, 2, 3, 4, 5, 6, 7, 8])); // Would take a very, very long time
```
**Explanation (O(n!)):** Generating all permutations involves constructing every possible ordering of the elements.

- For the first position, there are n choices.
- For the second position, there are `n−1` choices remaining.
- For the third, `n−2` choices, and so on. The total number of permutations is `n×(n−1)×(n−2)×⋯×1=n!`. Since the algorithm must generate each permutation, and potentially perform some operations for each (like adding to a result list), the time complexity is proportional to `n!`. This grows incredibly fast; `5!=120`, but `10!=3,628,800, and 20!` is astronomically large.
---

