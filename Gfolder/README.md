### **Code Analysis**

This Python program implements **Dijkstra's Algorithm** for finding the shortest path from a source vertex to all other vertices in a weighted, undirected graph. It uses a **min-heap (priority queue)** to optimize the process of choosing the next vertex to process based on the shortest known distance.

Here's a breakdown of the code:

---

### 1. **Edge Class**
```python
class Edge:
    def __init__(self, to, weight):
        self.to = to  # The destination vertex of the edge
        self.weight = weight  # The weight (cost) of the edge
```
- **Purpose**: Defines the `Edge` class to represent a directed edge in the graph with a destination vertex `to` and a weight `weight`.

---

### 2. **Function to Add Edges to the Graph**
```python
def add_edge(adj, u, v, w):
    adj[u].append(Edge(v, w))  # Add an edge from u to v with weight w
    adj[v].append(Edge(u, w))  # Add an edge from v to u with weight w (for undirected graph)
```
- **Purpose**: Adds an edge between two vertices `u` and `v` with weight `w`. The graph is undirected, so the edge is added in both directions: `u -> v` and `v -> u`.

---

### 3. **Dijkstra’s Algorithm**
```python
def dijkstra(adj, start):
    n = len(adj)  # Number of vertices in the graph
    dist = [float('inf')] * n  # Initialize distances to infinity
    dist[start] = 0  # The distance to the start vertex is 0

    pq = []  # Priority queue to store vertices and their distances
    heapq.heappush(pq, (0, start))  # Push the start vertex with distance 0
```
- **Purpose**: Initializes the `dist` array where `dist[i]` will hold the shortest distance from the source `start` to vertex `i`. The priority queue `pq` stores vertices along with their current shortest distances.
- The algorithm starts by setting the distance to the `start` vertex to 0.

```python
    while pq:
        d, u = heapq.heappop(pq)  # Pop the vertex with the smallest distance
        if d > dist[u]:
            continue  # Skip if the distance is already updated
```
- **Purpose**: The algorithm enters a loop where the vertex `u` with the smallest known distance `d` is processed.
- **Optimization**: If `d` is greater than the already known distance `dist[u]`, it is skipped to avoid unnecessary processing.

```python
        for edge in adj[u]:
            v = edge.to
            weight = edge.weight
```
- **Purpose**: For each neighboring vertex `v` of `u`, the algorithm checks if the shortest path to `v` can be improved by going through `u`.

```python
            if dist[u] + weight < dist[v]:
                dist[v] = dist[u] + weight  # Update the shortest distance to v
                heapq.heappush(pq, (dist[v], v))  # Push the updated vertex to the priority queue
```
- **Relaxation**: If the path through `u` offers a shorter path to `v`, the distance to `v` is updated and the updated vertex `v` is added to the priority queue.

```python
    return dist  # Return the shortest distances from the start vertex to all other vertices
```
- **Return**: After processing all the vertices, the `dist` array contains the shortest distances from the `start` vertex to every other vertex in the graph.

---

### 4. **Main Function**
```python
def main():
    num_vertices = 6
    adj = [[] for _ in range(num_vertices)]  # Initialize the adjacency list for 6 vertices
```
- **Graph Initialization**: The `adj` list is created with 6 empty lists, each corresponding to a vertex in the graph.

```python
    # Build the graph (example)
    add_edge(adj, 0, 1, 4)
    add_edge(adj, 0, 2, 2)
    add_edge(adj, 1, 2, 1)
    add_edge(adj, 1, 3, 5)
    add_edge(adj, 2, 3, 8)
    add_edge(adj, 2, 4, 10)
    add_edge(adj, 3, 4, 6)
    add_edge(adj, 3, 5, 5)
    add_edge(adj, 4, 5, 4)
```
- **Graph Construction**: Edges are added to the graph using the `add_edge` function. These edges represent a weighted, undirected graph.

```python
    start_vertex = 0  # Choose the start vertex
    shortest_paths = dijkstra(adj, start_vertex)
```
- **Running Dijkstra**: The `dijkstra` function is called to compute the shortest paths from vertex `0` (the start vertex) to all other vertices.

```python
    print(f"Shortest paths from vertex {start_vertex}:")
    for i in range(num_vertices):
        print(f"To vertex {i}: ", end="")
        if shortest_paths[i] == float('inf'):
            print("Infinity")
        else:
            print(shortest_paths[i])
```
- **Output**: The shortest paths from vertex `0` to all other vertices are printed. If a vertex is unreachable, the distance is displayed as `"Infinity"`.

---

### **Example Output**

For the graph built in the `main()` function, the output will be:

```
Shortest paths from vertex 0:
To vertex 0: 0
To vertex 1: 3
To vertex 2: 2
To vertex 3: 8
To vertex 4: 12
To vertex 5: 10
```

### **Explanation of Output**

- The shortest path from vertex `0` to vertex `1` is `3`, which is achieved by following the edge `0 -> 2 -> 1` (with weights `2` and `1` respectively).
- The shortest path from vertex `0` to vertex `2` is `2` via the direct edge `0 -> 2` with weight `2`.
- The shortest path from vertex `0` to vertex `3` is `8`, achieved via `0 -> 2 -> 3`.
- The shortest path from vertex `0` to vertex `4` is `12`, achieved via `0 -> 2 -> 4`.
- The shortest path from vertex `0` to vertex `5` is `10`, achieved via `0 -> 2 -> 5`.

### **Time Complexity**

- The time complexity of Dijkstra’s algorithm with a priority queue (min-heap) is `O((V + E) * log(V))`, where:
  - `V` is the number of vertices.
  - `E` is the number of edges.
- Each vertex is processed once, and each edge is processed at most once.

### **Space Complexity**

- The space complexity is `O(V + E)`, where:
  - `V` is the number of vertices (for the adjacency list and distance array).
  - `E` is the number of edges (for the adjacency list).

---

Let me know if you need further explanations or improvements!
