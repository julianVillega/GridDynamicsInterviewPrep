[link to ChatGPT chat](https://chatgpt.com/share/691e3d09-2a78-8003-9296-80f0bcf7cfab)

# 🔎 **1. Binary Search**

### ✅ **What it is**

Binary search is an algorithm used to find an element _quickly_ in a **sorted list**.  
Instead of checking every element, it repeatedly cuts the search space in half.

### ⚡ Time Complexity

- **O(log n)** — very efficient
    
- Only works on **sorted** data
    

### 🧠 Idea

1. Look at the middle element.
    
2. If target < mid → search left half
    
3. If target > mid → search right half
    
4. Repeat until found or search space is empty.
    

### 🐍 Python example (iterative)
```Python
def binary_search(arr, target):     
	left, right = 0, len(arr) - 1 
    while left <= right:         
	    mid = (left + right) // 2         
	    if arr[mid] == target:             
		    return mid         
		elif target < arr[mid]:             
			right = mid - 1         
		else:             
			left = mid + 1      
	return -1

```


### ❗ Common interview pitfalls

- Forgetting the array must be **sorted**
    
- Off-by-one errors in mid / left / right
    
- Infinite loops because you didn’t update boundaries correctly
    

---

# 🔁 **2. Recursion Basics**

### ✅ **What recursion is**

A function that calls **itself** to solve a problem.

### 🧠 When to use recursion

- When the problem can be defined in terms of smaller versions of itself
    
- Examples: factorial, Fibonacci, tree/graph traversal, divide-and-conquer algorithms
    

### ✔ Key parts of every recursive function:

1. **Base case** — stops the recursion
    
2. **Recursive case** — reduces the problem size
    

### 🐍 Example: factorial

`def factorial(n):     if n == 0:        # base case         return 1     return n * factorial(n - 1)   # recursive step`

### ⚡ Important: recursion depth limit

Python has a maximum recursion depth (around 1000).

Use iteration if deep recursion is needed.

---

# 🔃 **3. Sorting Algorithms (High-Level Understanding)**

You do NOT need to code them perfectly in interviews, but you must know:

- How they work
    
- Time complexity
    
- When they are used
    

Let’s break them down.

---

## 🫧 **Bubble Sort**

### Idea

Repeatedly swap adjacent elements if they are in the wrong order.

### Steps:

- Compare `arr[i]` and `arr[i+1]`
    
- Swap if `arr[i] > arr[i+1]`
    
- Repeat until no swaps
    

### Time Complexity

- Worst: **O(n²)**
    
- Best: **O(n)** if the list is already sorted (with optimization)
    

### Use cases

- Rarely used in real life
    
- Good for teaching purposes only
    

---

## 🔍 **Selection Sort**

### Idea

Repeatedly select the **smallest** element and put it at the front.

### Steps:

- Find min element in the unsorted portion
    
- Swap with the first unsorted element
    

### Time Complexity

- Always **O(n²)** (bad)
    
- Even if the array is sorted
    

### Use cases

- Very simple but inefficient; rarely practical
    

---

## 🔀 **Merge Sort**

### Idea (Divide and Conquer)

1. Divide the array into two halves
    
2. Sort each half recursively
    
3. Merge the two sorted halves
    

### Time Complexity

- Always **O(n log n)** — very efficient
    
- Space complexity: **O(n)**
    

### Why it’s important

- Stable sort
    
- Guarantees O(n log n)
    
- Often used in real systems (e.g., Python’s `sorted()` uses Timsort, partially inspired by merge sort)
    

### 🧠 High-level example

`[4, 2, 1, 3] → split into [4, 2] and [1, 3] → sort each: [2, 4] and [1, 3] → merge → [1, 2, 3, 4]`

---

# 📘 Summary Table

|Algorithm|Type|Best|Worst|Stable?|Notes|
|---|---|---|---|---|---|
|**Binary Search**|Searching|O(1)|O(log n)|—|Requires sorted array|
|**Bubble Sort**|Sorting|O(n)|O(n²)|Yes|Simple but slow|
|**Selection Sort**|Sorting|O(n²)|O(n²)|No|Always slow|
|**Merge Sort**|Sorting|O(n log n)|O(n log n)|Yes|Great performance|