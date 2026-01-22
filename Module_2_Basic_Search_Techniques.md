# Module 2: Basic Search Techniques

## 2.1 Solving Problems by Searching

Search is the fundamental technique of AI when the sequence of steps to reach a goal is unknown. It involves exploring a state space to find a path from the initial state to a goal state.

KEY TERMS:
*   **Search Node:** Representation of a state in the search tree.
*   **Fringe (or Frontier):** The set of all nodes that have been generated but not yet expanded.
*   **Expansion:** Generating the child nodes of a parent node by applying valid operators.

## 2.2 Uniform Search Strategies (Uninformed Search)

Uninformed search strategies have no additional information about states beyond the problem definition (i.e., they don't know if they are getting closer to the goal).

### 2.2.1 Breadth-First Search (BFS)
*   **Strategy:** Expand the shallowest unexpanded node first.
*   **Implementation:** Use a FIFO (First-In, First-Out) queue for the fringe.
*   **Completeness:** Yes (if branching factor *b* is finite).
*   **Optimality:** Yes (if path cost is a non-decreasing function of the depth of the node).
*   **Time Complexity:** O(b^d), where *b* is branching factor and *d* is depth of solution.
*   **Space Complexity:** O(b^d) (Requires keeping all nodes in memory).

### 2.2.2 Depth-First Search (DFS)
*   **Strategy:** Expand the deepest unexpanded node first.
*   **Implementation:** Use a LIFO (Last-In, First-Out) stack for the fringe.
*   **Completeness:** No (can get stuck in infinite loops or infinitely deep paths).
*   **Optimality:** No (might find a deeper solution first).
*   **Time Complexity:** O(b^m), where *m* is the maximum depth of the search space.
*   **Space Complexity:** O(b*m) (Linear space complexity, very memory efficient).

### 2.2.3 Depth-Limited Search (DLS)
*   **Strategy:** DFS with a predetermined depth limit *l*.
*   **Purpose:** To prevent DFS from getting stuck in infinite paths.
*   **Completeness:** No (if solution is deeper than *l*).
*   **Optimality:** No.

### 2.2.4 Iterative Deepening Search (IDS)
*   **Strategy:** Repeatedly run DLS with increasing depth limits (0, 1, 2, ...).
*   **Benefits:** Combines the benefits of BFS (completeness, optimality) and DFS (space efficiency).
*   **Time Complexity:** O(b^d).
*   **Space Complexity:** O(b*d).

### 2.2.5 Bidirectional Search
*   **Strategy:** Run two simultaneous searches: one forward from the initial state and one backward from the goal state. Stop when they meet.
*   **Benefit:** Reduces time complexity significantly (O(b^(d/2)) instead of O(b^d)).
*   **Challenge:** Efficiently computing predecessors (backward search) and matching states in the middle.

## 2.3 Heuristic Search (Informed Search) Fundamentals

While Module 3 covers this in depth, "Best-First Search" is often introduced as the general framework here.

### 2.3.1 Best-First Search
*   **Strategy:** Select the node for expansion based on an **evaluation function, f(n)**, which estimates the "desirability" of the node.
*   **Implementation:** Priority Queue.
*   **Greedy Best-First Search:** f(n) = h(n) (heuristic only). Expands the node that appears closest to the goal.

## 2.4 Comparing Search Strategies

| Strategy | Completeness | Optimality | Time Complexity | Space Complexity |
| :--- | :--- | :--- | :--- | :--- |
| **BFS** | Yes | Yes (if step costs equal) | O(b^d) | O(b^d) |
| **DFS** | No | No | O(b^m) | O(b*m) |
| **Depth-Limited** | No | No | O(b^l) | O(b*l) |
| **Iterative Deepening** | Yes | Yes (if step costs equal) | O(b^d) | O(b*d) |
| **Bidirectional** | Yes | Yes | O(b^(d/2)) | O(b^(d/2)) |

*   **b:** Branching factor
*   **d:** Depth of least-cost solution
*   **m:** Maximum depth of state space
*   **l:** Depth limit

**Conclusion:**
*   Use **BFS** if the solution is shallow and meaningful memory is available.
*   Use **DFS** if memory is limited and deep paths are not an issue.
*   Use **IDS** for the best balance of time and memory in uninformed search.
