# Module 3: Special Search Techniques & Symbolic Logic

This module covers advanced search strategies that go beyond the basic blind search, focusing on optimization, constraint handling, and logical reasoning.

---

## 3.1 Uninformed vs. Informed Search

*   **Uninformed (Blind) Search:**  
    Has no information about the number of steps or cost from the current state to the goal.  
    *Examples:* BFS, DFS, Uniform Cost Search.  
    *Drawback:* Inefficient for large state spaces.
*   **Informed (Heuristic) Search:**  
    Uses domain-specific knowledge (heuristics) to find solutions more efficiently.  
    *Examples:* Greedy Best-First, A*.

---

## 3.2 Heuristic Search

Heuristic search relies on a **Heuristic Function, h(n)**.
*   **Definition:** $h(n)$ = estimated cost of the cheapest path from the state at node $n$ to a goal state.
*   **Property:** If $n$ is a goal node, $h(n) = 0$.
*   **Example (Route Finding):** Straight-line distance between cities.

### 3.2.1 Greedy Best-First Search
*   **Strategy:** Always expands the node that appears to be closest to the goal.
*   **Evaluation Function:** $f(n) = h(n)$.
*   **Analysis:**
    *   **Complete?** No (can get stuck in loops).
    *   **Optimal?** No.
    *   **Time Complexity:** $O(b^m)$ (Worst case).
    *   **Use Case:** When speed is more important than the optimal path.

### 3.2.2 A* Search (A-Star)
The most widely used AI search algorithm. It combines the advantages of Uniform Cost Search (optimality) and Greedy Search (efficiency).

*   **Strategy:** Minimizes the total estimated solution cost.
*   **Evaluation Function:** $f(n) = g(n) + h(n)$
    *   $g(n)$: Actual cost to reach node $n$ from the start.
    *   $h(n)$: Estimated cost from $n$ to the goal.
*   **Analysis:**
    *   **Complete?** Yes (if there is a solution).
    *   **Optimal?** Yes, provided the heuristic is **Admissible** and **Consistent**.

#### Conditions for Optimality
1.  **Admissibility:** $h(n)$ never overestimates the cost to the goal.
    *   $0 \le h(n) \le h^*(n)$ (where $h^*$ is the true cost).
    *   *Example:* Straight line distance is admissible because you can't go faster than a straight line.
2.  **Consistency (Monotonicity):** The estimated cost of a reaching a goal from $n$ is no greater than the step cost to a successor $n'$ plus the estimated cost from $n'$.
    *   $h(n) \le c(n, a, n') + h(n')$
    *   Ensures the total cost $f(n)$ never decreases along a path.

---

## 3.3 Local Search Algorithms

Local search algorithms operation using a single current node (rather than multiple paths) and generally move only to neighbors of that node.
*   **Application:** Optimization problems (e.g., N-Queens, Factory Layout) where the path doesn't matter, only the final state.

### 3.3.1 Hill Climbing Search
*   **Metaphor:** "Climbing Mount Everest in thick fog." You simply take a step in the direction of steepest ascent.
*   **Simple Hill Climbing:** Examines neighbors one by one and selects the first one that optimizes the current cost.
*   **Steepest-Ascent Hill Climbing:** Examines *all* neighbors and selects the absolute best one.
*   **Drawbacks (Getting Stuck):**
    1.  **Local Maxima:** A peak that is higher than each of its neighbors but lower than the global maximum. The algorithm stops here erroneously.
    2.  **Ridges:** A sequence of local maxima that is difficult to navigate (requires moving "down" to go "up").
    3.  **Plateaux:** A flat area where seemingly no move improves the state.

### 3.3.2 Simulated Annealing
Designed to escape Local Maxima.
*   **Inspiration:** The process of annealing in metallurgy (heating and slowly cooling metal to toughen it).
*   **Mechanism:**
    *   Instead of always picking the best move, it sometimes picks a **worse** move.
    *   The probability of accepting a worse move is high at the start (High Temperature) and decreases as time goes on (Cooling Schedule).
    *   Formula for acceptance probability: $P = e^{\Delta E / T}$ where $\Delta E$ is the worsening in value and $T$ is temperature.

### 3.3.3 Genetic Algorithms (GA)
A variant of stochastic beam search inspired by biological evolution.
*   **Process:**
    1.  **Population:** Start with $k$ randomly generated states (chromosomes).
    2.  **Fitness Function:** Scores each state (higher is better).
    3.  **Selection:** Select pairs of states to reproduce based on fitness ("Survival of the Fittest").
    4.  **Crossover:** Split the parent states and swap parts to create offspring.
    5.  **Mutation:** With a small probability, randomly alter a bit in the offspring (maintains diversity).

---

## 3.4 Constraint Satisfaction Problems (CSP)

A CSP is a specific type of problem definition.
*   **Components:**
    *   $X$: A set of variables $\{X_1, ..., X_n\}$.
    *   $D$: A set of domains $\{D_1, ..., D_n\}$ (possible values).
    *   $C$: A set of constraints that specify allowable combinations of values.
*   **Goal:** Assign a value to every variable such that all constraints are satisfied.
*   **Example (Map Coloring):**
    *   Variables: WA, NT, Q, NSW, V, SA, T (States of Australia).
    *   Domain: {Red, Green, Blue}.
    *   Constraints: Adjacent regions must have different colors (e.g., $WA \neq NT$).

### Solving CSPs
1.  **Backtracking Search:** Depth-first search that assigns values one by one. If a constraint is violated, it backtracks.
2.  **Constraint Propagation:** using the constraints to reduce the legal values for a variable.
    *   **Forward Checking:** When keeping track of remaining legal values for unassigned variables. If a variable runs out of values, terminate immediately.
    *   **Arc Consistency (AC-3):** Checks every constraint arc to ensure consistency across the board. Stronger than forward checking.

---

## 3.5 Adversarial Search (Game Playing)

Used in multi-agent environments with correct info (e.g., Chess, Tic-Tac-Toe).

### 3.5.1 Minimax Algorithm
*   **MAX:** The agent trying to maximize the score.
*   **MIN:** The opponent trying to minimize the score.
*   **Process:**
    1.  Generate the entire game tree down to terminal states (or a depth limit).
    2.  Apply the Utility Function to terminal states.
    3.  Backtrack up the tree:
        *   At MAX nodes, take the `max` of child values.
        *   At MIN nodes, take the `min` of child values.

### 3.5.2 Alpha-Beta Pruning
An optimization technique for Minimax. It returns the exact same move but prunes away branches that cannot possibly influence the final decision.
*   **Alpha ($\alpha$):** The value of the best (highest) choice found so far for MAX along the path.
*   **Beta ($\beta$):** The value of the best (lowest) choice found so far for MIN.
*   **Pruning Rule:** If $\alpha \ge \beta$, stop searching this branch. (Because MIN would never let MAX get this far, or MAX already has a better option).

---

## 3.6 Symbolic Logic

Logic is the primary method of **Knowledge Representation**.

### 3.6.1 Propositional Logic (PL)
The simplest logic. Deals with facts that are either True or False.
*   **Syntax:**
    *   Atomic sentences: $P, Q, R$.
    *   Connectives: $\neg$ (Not), $\land$ (And), $\lor$ (Or), $\Rightarrow$ (Implies), $\Leftrightarrow$ (If and only if).
*   **Semantics:** Truth tables.
*   **Inference:**
    *   **Modus Ponens:** If $(P \Rightarrow Q)$ is true and $P$ is true, then $Q$ is true.
    *   **Resolution:** $(P \lor Q) \land (\neg P \lor R) \Rightarrow (Q \lor R)$.

### 3.6.2 First-Order Logic (FOL)
Propositional logic assumes the world contains facts. FOL assumes the world contains **Objects**, **Relations**, and **Functions**.
*   **Quantifiers:**
    *   **Universal ($\forall$):** "For all". $\forall x, King(x) \Rightarrow Person(x)$ (All kings are persons).
    *   **Existential ($\exists$):** "There exists". $\exists x, Crown(x) \land OnHead(x, John)$ (There exists a crown on John's head).

### 3.6.3 Inference in FOL
*   **Unification:** The process of finding substitutions that make different logical expressions identical.
    *   Unify($Knows(John, x)$, $Knows(John, Jane)$) $\rightarrow$ $\{x / Jane\}$.
*   **Resolution Refutation:** A powerful proof technique used in Prolog.
    1.  Negate the goal you want to prove.
    2.  Add it to the Knowledge Base.
    3.  Use Resolution to derive a contradiction (Empty clause).
    4.  If a contradiction is found, the original goal must be True.
