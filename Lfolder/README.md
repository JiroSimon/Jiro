### **Code Analysis**

This Python program demonstrates the implementation and manipulation of **Singly Linked List**, **Doubly Linked List**, and **Circular Linked List**. 

Each type of list has its own structure, insertion function, and display function:

---

### **Classes for Node Structures**

1. **`SinglyNode`**:
    - This class represents a node in a **Singly Linked List**.
    - It contains two attributes:
        - `data`: The value of the node.
        - `next`: A pointer to the next node in the list (initialized to `None`).

2. **`DoublyNode`**:
    - This class represents a node in a **Doubly Linked List**.
    - It contains three attributes:
        - `data`: The value of the node.
        - `next`: A pointer to the next node.
        - `prev`: A pointer to the previous node (initialized to `None`).

---

### **Linked List Operations**

#### 1. **Singly Linked List**

- **`insert_singly(head, data)`**:
    - This function inserts a new node with the given `data` at the end of the **Singly Linked List**.
    - If the list is empty (`head` is `None`), the new node becomes the head of the list.
    - Otherwise, it traverses to the last node and attaches the new node.

- **`display_singly(head)`**:
    - This function prints the elements of the **Singly Linked List** from the head to the end (`None`).
    - Each node is followed by `" -> "` until the end of the list is reached.

#### 2. **Doubly Linked List**

- **`insert_doubly(head, data)`**:
    - This function inserts a new node with the given `data` at the end of the **Doubly Linked List**.
    - If the list is empty, the new node becomes the head of the list.
    - Otherwise, it traverses to the last node, attaches the new node, and updates the `prev` pointer of the new node to point to the previous node.

- **`display_doubly(head)`**:
    - This function prints the elements of the **Doubly Linked List** from the head to the end.
    - Each node is followed by `" <-> "` to represent the bidirectional connections.

#### 3. **Circular Linked List**

- **`insert_circular(head, data)`**:
    - This function inserts a new node with the given `data` into a **Circular Linked List**.
    - If the list is empty, the new node becomes the head, and its `next` pointer points to itself.
    - Otherwise, it traverses the list until it reaches the node that points to the head and then attaches the new node.

- **`display_circular(head)`**:
    - This function prints the elements of the **Circular Linked List** starting from the head.
    - It prints each node followed by `" -> "` until it loops back to the head node, indicating the circular nature of the list.

---

### **Main Function Execution**

```python
if __name__ == "__main__":
    # Singly Linked List
    singly_head = None
    singly_head = insert_singly(singly_head, 10)
    singly_head = insert_singly(singly_head, 20)
    singly_head = insert_singly(singly_head, 30)
    print("Singly Linked List: ", end="")  # Output of singly linked list
    display_singly(singly_head)

    # Doubly Linked List
    doubly_head = None
    doubly_head = insert_doubly(doubly_head, 100)
    doubly_head = insert_doubly(doubly_head, 200)
    doubly_head = insert_doubly(doubly_head, 300)
    print("Doubly Linked List: ", end="")  # Output of doubly linked list
    display_doubly(doubly_head)

    # Circular Linked List
    circular_head = None
    circular_head = insert_circular(circular_head, 1)
    circular_head = insert_circular(circular_head, 2)
    circular_head = insert_circular(circular_head, 3)
    print("Circular Linked List: ", end="")  # Output of circular linked list
    display_circular(circular_head)
```

- **Singly Linked List**:
    - The program inserts three elements: 10, 20, and 30.
    - It then displays the list in the format: `10 -> 20 -> 30 -> None`.

- **Doubly Linked List**:
    - The program inserts three elements: 100, 200, and 300.
    - It then displays the list in the format: `100 <-> 200 <-> 300 <-> None`.

- **Circular Linked List**:
    - The program inserts three elements: 1, 2, and 3.
    - It then displays the list in the format: `1 -> 2 -> 3 -> (Back to Head)`.

---

### **Expected Output**

```
Singly Linked List: 10 -> 20 -> 30 -> None
Doubly Linked List: 100 <-> 200 <-> 300 <-> None
Circular Linked List: 1 -> 2 -> 3 -> (Back to Head)
```

---

### **Explanation of Output**

1. **Singly Linked List**:
    - The list consists of three nodes: 10, 20, and 30. Each node points to the next node, with the last node pointing to `None`.

2. **Doubly Linked List**:
    - The list consists of three nodes: 100, 200, and 300. Each node has both a `next` pointer (pointing to the next node) and a `prev` pointer (pointing to the previous node). The traversal is bidirectional.

3. **Circular Linked List**:
    - The list consists of three nodes: 1, 2, and 3. The last node points back to the head, creating a circular structure. The output clearly shows the cyclic nature of the list by printing ` (Back to Head)`.

---

### **Time and Space Complexity**

#### **Time Complexity**
- **Insertion in Singly Linked List**: `O(n)` where `n` is the number of nodes (due to traversal to the end).
- **Insertion in Doubly Linked List**: `O(n)` (similar to the singly linked list, traversal to the end).
- **Insertion in Circular Linked List**: `O(n)` (traversal to the last node).
- **Display in All Lists**: `O(n)` (linear traversal to print all nodes).

#### **Space Complexity**
- **For each list**: `O(n)` where `n` is the number of elements, as space is used to store the nodes.

This solution is efficient for typical list manipulations and provides clear visual output for the different types of linked lists.
