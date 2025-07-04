
# 🧭 Problem Set II: Graphs and Path Optimization (MIT 6.0002)

This project explores directed graphs and optimization under constraints using depth-first search (DFS). It simulates **MIT Campus Map** determining the best route between buildings on campus while respecting limits on total distance and outdoor exposure. This is part of the MIT 6.0002: *Introduction to Computational Thinking and Data Science course.*

![image](https://github.com/user-attachments/assets/71ca27f1-b14b-460c-9fe8-bfd7c43a0576)

## Implemented So Far

- **`WeightedEdge` Class**: Created a class to represent a weighted directed edge with total distance and outdoor distance.
- **`Digraph` Class**:
  - `add_node`: Method to add a node to the graph.
  - `add_edge`: Method to add a weighted edge between nodes.
- **`load_map` Function**: Parsed a text file and loaded the map into a digraph, testing its functionality.
  
---
## 🚧 Part B - Depth First Search Approach
Implemented a system to find the shortest path between buildings on a weighted, directed graph. The path must:

- Minimize the total distance traveled
- Obey a constraint on maximum outdoor distance
  
This simulates real-world constrained optimization problems such as routing ambulances through a campus during inclement weather or high-risk conditions.

## Algorithms Implemented

### ✅ Depth-First Search with Pruning
- Recursively traverses the graph while accumulating total and outdoor distance.
- Rejects paths that exceed the allowed outdoor distance or previously found shortest path.
- Uses backtracking and constraint checks to avoid unnecessary computation.

### ✅ Optimized Pathfinding Wrapper
- A `directed_dfs` function wraps the DFS logic, enforces final constraints, and returns the optimal path or raises a `ValueError`.

### ✅ Graph Infrastructure
- `WeightedEdge`: Represents directed edges with both total and outdoor distance weights.
- `Digraph`: A directed graph structure supporting node and edge insertion.
- `load_map`: Parses a text file into a graph.

## 📊 Results
This problem is more about **correctness under constraint** than runtime benchmarking. I validated my implementation against a full unit test suite that includes:
- Multi-step valid paths
- Edge cases with no valid paths
- Constraint violations (too much outdoor travel)

## ❗ Key Insight: Recursive State Management Is Hard
This problem pushed me deeper into understanding not just recursion, but how state propagates through recursive calls. I had to juggle:

- A custom path structure [`list of nodes, total distance, outdoor distance]`)
- Best-so-far path tracking
- Ensuring each recursive branch operated on its own copy of state
- Avoiding cycle re-visitation
- Avoiding variable scope errors like `UnboundLocalError`

What finally helped was realizing that recursion is not about "committing" to a path, but it's about exploring all options and letting the best one bubble up.

## 🛠️ Skills Used
- Recursive DFS with pruning and constraint checks
- Defensive programming and debugging recursion
- Understanding variable scope across recursive frames
- Designing and working with custom data structures ([path, total, outdoor])
- Class-based Python (inheritance for edges)
- Reading from and modeling real-world map data
- Testing with assertions and edge-case scenarios
- Git version control and incremental documentation
---
## Course Reference
This project is part of MIT 6.0002 – Introduction to Computational Thinking and Data Science
You can find the full course on MIT OpenCourseWare:

🔗 [https://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-0002-introduction-to-computational-thinking-and-data-science-fall-2016/]

Topic: Graph-Theoretic Models and Optimization  
---
### 💬 Personal Reflection
This was the hardest problem set so far, not because I did not understand DFS or recursion, but because I did not fully grasp how ***recursive functions manage state*** across branches. I had to slow down, trace each variable, and let go of the assumption that recursion "*knows*" what I want. It doesn't. 

What I took away form this is: logic is only good as the structure that carries it. 
Syntax matters. Scope matters. And clarity wins over cleverness. 

This problem reminded me that depth, not just in search but in *learning*, is where real growth happens.
