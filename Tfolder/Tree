from collections import deque

# Class for a binary tree node
class Node:
    def __init__(self, val):
        self.data = val
        self.left = None
        self.right = None

# Function to perform inorder traversal (Left, Root, Right)
def inorder(root):
    if root is None:
        return
    inorder(root.left)
    print(root.data, end=" ")
    inorder(root.right)

# Function to perform preorder traversal (Root, Left, Right)
def preorder(root):
    if root is None:
        return
    print(root.data, end=" ")
    preorder(root.left)
    preorder(root.right)

# Function to perform postorder traversal (Left, Right, Root)
def postorder(root):
    if root is None:
        return
    postorder(root.left)
    postorder(root.right)
    print(root.data, end=" ")

# Function for level order traversal (breadth-first)
def level_order(root):
    if root is None:
        return
    q = deque([root])

    while q:
        current = q.popleft()
        print(current.data, end=" ")

        if current.left:
            q.append(current.left)
        if current.right:
            q.append(current.right)

# Function to calculate the height of the tree
def height(root):
    if root is None:
        return 0
    return 1 + max(height(root.left), height(root.right))

# Main function
if __name__ == "__main__":
    # Constructing a sample binary tree
    root = Node(1)
    root.left = Node(2)
    root.right = Node(3)
    root.left.left = Node(4)
    root.left.right = Node(5)
    root.right.left = Node(6)
    root.right.right = Node(7)

    # Inorder traversal
    print("Inorder traversal: ", end="")
    inorder(root)
    print()  # Output: 4 2 5 1 6 3 7

    # Preorder traversal
    print("Preorder traversal: ", end="")
    preorder(root)
    print()  # Output: 1 2 4 5 3 6 7

    # Postorder traversal
    print("Postorder traversal: ", end="")
    postorder(root)
    print()  # Output: 4 5 2 6 7 3 1

    # Level order traversal
    print("Level order traversal: ", end="")
    level_order(root)
    print()  # Output: 1 2 3 4 5 6 7

    # Height of the tree
    print(f"Height of the tree: {height(root)}")  # Output: 3
