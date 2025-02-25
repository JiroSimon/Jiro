### **Code Analysis**

This Python program demonstrates several operations using the `heapq` module, which provides a **priority queue** implementation using a **min-heap**. In this program, the heap is manipulated in two forms: a **max-heap** (simulated using negation) and a **min-heap** (the default behavior of `heapq`). Additionally, the program shows how to perform heap sort by leveraging the heap structure.

---

### **Functions & Methods**

1. **`print_heap` function:**
```python
def print_heap(heap):
    print(" ".join(map(str, heap)))
```
- **Purpose**: This utility function takes a list `heap` as input and prints it in a readable format.
- It converts each element to a string and joins them with spaces.

---

2. **`main` function:**
The main function showcases various operations on heaps.

---

### **Max Heap Creation**

```python
max_heap = [3, 1, 4, 1, 5, 9, 2, 6]
max_heap = [-x for x in max_heap]  # Negate values to simulate max heap
heapq.heapify(max_heap)  # Convert list to a heap (min-heap of negated values)
```
- **Purpose**: A **max-heap** is simulated by negating the values in the original list `max_heap`. This is because `heapq` by default creates a **min-heap**. Negating the values allows us to treat the smallest element (in the min-heap) as the largest element in the original list.
- **heapify**: Converts the list into a valid heap structure, but since the values are negated, it forms a **min-heap of the negated values**.

```python
print("Max Heap:", end=" ")
print_heap([-x for x in max_heap])  # Negate back to print actual max heap
```
- **Purpose**: After converting to a heap, we negate the values back to print them in their original form as a **max-heap**.

---

### **Inserting into the Heap**

```python
heapq.heappush(max_heap, -10)  # Insert a new element (negated to maintain max-heap)
```
- **Purpose**: The function `heappush` inserts a new value into the heap. Since we're simulating a **max-heap**, we negate the value `10` (to insert `-10`).
- After insertion, the heap is reorganized to maintain the heap property.

```python
print("Max Heap after insertion:", end=" ")
print_heap([-x for x in max_heap])
```
- **Purpose**: Prints the heap after inserting a new element.

---

### **Removing from the Heap (Removing the Largest Element)**

```python
heapq.heappop(max_heap)  # Remove the largest element (smallest in negated min-heap)
```
- **Purpose**: The `heappop` function removes and returns the smallest element in the heap (which is the largest element in the **max-heap**, due to negation).
- After popping, the heap is restructured.

```python
print("Max Heap after removal:", end=" ")
print_heap([-x for x in max_heap])
```
- **Purpose**: Prints the heap after removal of the largest element.

---

### **Min Heap Creation (Default Behavior)**

```python
min_heap = [3, 1, 4, 1, 5, 9, 2, 6]
heapq.heapify(min_heap)  # Convert list to a min-heap (default behavior of heapq)
```
- **Purpose**: The `heapq.heapify()` function is used to create a **min-heap**. In a **min-heap**, the smallest element is always at the root.
- The heap is rearranged to satisfy the heap property (parent nodes are smaller than child nodes).

```python
print("Min Heap:", end=" ")
print_heap(min_heap)
```
- **Purpose**: Prints the heap after creating the **min-heap**.

---

### **Heap Sort**

```python
unsorted = [3, 1, 4, 1, 5, 9, 2, 6]
heapq.heapify(unsorted)  # Create a min-heap
```
- **Purpose**: The list `unsorted` is converted into a **min-heap** using `heapq.heapify()`. This ensures the smallest element is at the root.

```python
sorted_array = []
while unsorted:
    sorted_array.append(heapq.heappop(unsorted))  # Pop the smallest element one by one
```
- **Purpose**: This block of code demonstrates **heap sort**. It repeatedly pops the smallest element from the heap (which is the root of the min-heap) and appends it to `sorted_array`.
- As elements are popped, they are placed into `sorted_array`, resulting in a sorted array in **ascending order**.

```python
print("Sorted array (using heap sort):", end=" ")
print_heap(sorted_array)
```
- **Purpose**: Prints the `sorted_array` which contains the elements sorted in ascending order.

---

### **Expected Output**

Given the input lists and operations, the output of the program will be:

```
Max Heap: 9 6 5 3 1 1 2 4 
Max Heap after insertion: 10 6 9 3 1 1 2 4 5 
Max Heap after removal: 6 5 9 3 1 1 2 4 
Min Heap: 1 1 2 3 5 9 4 6 
Sorted array (using heap sort): 1 1 2 3 4 5 6 9 
```

### **Explanation of Output**

1. **Max Heap (Initial)**:
   - The max heap is represented by the negated values (`[-9, -6, -5, -3, -1, -1, -2, -4]`), but when negated back, the largest value (`9`) is at the root of the heap.
   
2. **Max Heap after Insertion**:
   - A new element (`10`) is inserted. After heapify, the largest element (`10`) becomes the root of the heap.

3. **Max Heap after Removal**:
   - The largest element (`10`) is removed, and the heap is rearranged to maintain the heap property.

4. **Min Heap**:
   - The min-heap is created using the default behavior of `heapq`. The smallest element (`1`) is at the root.

5. **Heap Sort**:
   - The `heapq` min-heap is used to perform heap sort. After extracting elements from the min-heap one by one, the list is sorted in ascending order: `[1, 1, 2, 3, 4, 5, 6, 9]`.

---

### **Time Complexity**
- **Heapify**: `O(n)` where `n` is the number of elements in the list.
- **Insertion (heappush)**: `O(log n)` for each insertion.
- **Removal (heappop)**: `O(log n)` for each removal.
- **Heap Sort**: `O(n log n)` since we perform `n` pops, each costing `O(log n)`.

### **Space Complexity**
- **Heap**: `O(n)` where `n` is the number of elements in the heap.
