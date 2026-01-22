# Module 5: Structured Knowledge, Expert Systems, and Learning

## 5.1 Structured Knowledge Representation

Structured knowledge representations organize information to facilitate access and reasoning, often mirroring how humans might structure thoughts.

### 5.1.1 Associative Networks (Semantic Networks)
*   **Concept:** Represents knowledge as a graph of labeled nodes and directed (labeled) arcs.
*   **Nodes:** Objects, concepts, or events.
*   **Arcs:** Relationships (e.g., `is-a`, `has-part`, `instance-of`).
*   **Common Relation:** `IS-A` (Inheritance).
    *   Example: `Bird` --(is-a)--> `Animal`. `Robin` --(is-a)--> `Bird`.
*   **Inference:** Property inheritance (e.g., if Animal breathes, Robin breathes).

### 5.1.2 Conceptual Graphs
*   **Concept:** A logic-based knowledge representation formalism developed by John Sowa.
*   **Components:**
    *   **Concept Nodes:** Boxes representing entities (e.g., [Cat], [Mat]).
    *   **Relation Nodes:** Circles representing relations (e.g., (Sitting-On)).
*   **Structure:** Bipartite graph (Concept nodes connect only to Relation nodes and vice versa).
*   **Example:** [Cat] -> (Sitting-On) -> [Mat].

### 5.1.3 Frames Structures
*   **Concept:** Developed by Marvin Minsky (1974). Represents stereotypical situations.
*   **Structure:** A collection of "slots" and "fillers".
*   **Slots:** Attributes of the object.
*   **Fillers:** Values, default values, or procedures (attached daemons like `if-needed`, `if-added`).
*   **Example:**
    *   **Frame:** Hotel Room
    *   **Slots:**
        *   Bed: (Default: King)
        *   Bath: (Range: Yes/No)
        *   Rate: (Procedure: Calculate based on season)

## 5.2 Expert Systems

Al programs that achieve expert-level competence in solving problems in specialized domains by bringing to bear the knowledge of human experts.

### 5.2.1 Rule-Based Systems (Production Systems)
*   **Components:**
    1.  **Knowledge Base:** Set of IF-THEN rules (Production Rules).
    2.  **Working Memory:** Current facts/state of the world.
    3.  **Inference Engine:** Cycle of Match-Select-Act.
        *   **Match:** Find all rules whose IF part matches working memory.
        *   **Select:** Conflict resolution (pick one rule).
        *   **Act:** Executive the THEN part (add/remove facts).

### 5.2.2 Non-Production Systems

#### Decision Tree Architectures
*   **Structure:** A tree where internal nodes represent tests on attributes, branches represent outcomes, and leaf nodes represent class labels (decisions).
*   **Inference:** Traversing from root to leaf based on input values.
*   **Benefits:** Highly interpretable.

#### Blackboard System Architecture
*   **Metaphor:** Experts standing around a blackboard solving a puzzle.
*   **Components:**
    1.  **Blackboard:** Global database holding the emerging solution.
    2.  **Knowledge Sources (KS):** Independent modules (experts) that read/write to the blackboard.
    3.  **Control Component:** Selects which KS should run next.
*   **Use Cases:** Complex problems like speech recognition (HEARSAY-II).

#### Neural Network Architecture
*   **Concept:** Connected units (neurons) that process information in parallel.
*   **Difference:** Knowledge is not explicit rules but implicit "weights" between connections.
*   **Use Cases:** Pattern recognition, classification.

## 5.3 Learning

**Machine Learning** is the field of study that gives computers the ability to learn without being explicitly programmed.

### 5.3.1 Types of Learning
1.  **Rote Learning:** Memorization (caching results).
2.  **Supervised Learning:** Learning from labeled examples (Input -> Output).
3.  **Unsupervised Learning:** Finding patterns in unlabeled data (Clustering).
4.  **Reinforcement Learning:** Learning from feedback (rewards/punishments) after actions.

### 5.3.2 General Learning Model
1.  **Environment:** Supplies information.
2.  **Learning Element:** Makes improvements.
3.  **Performance Element:** Selects external actions (the agent itself).
4.  **Critic:** Provides feedback on performance.
5.  **Problem Generator:** Suggests actions that will lead to new and informative experiences.

### 5.3.3 Learning by Induction
Learning a general function or rule from specific input-output examples.

#### Generalization & Specialization
*   **Generalization:** Extending a specific rule to cover more examples (e.g., seeing a red robin and a blue jay -> "Birds fly").
*   **Specialization:** Narrowing a rule to exclude negative examples (e.g., "Birds fly" -> "Birds except Penguins fly").

#### Example of Inductive Learner
*   **Version Space Learning:** Keeps track of the "space" of all hypothesis consistent with the examples seen so far.
*   **Candidate-Elimination Algorithm:** Maintains two sets:
    *   **G (General):** Most general consistent hypotheses.
    *   **S (Specific):** Most specific consistent hypotheses.
    *   As examples arrive, G is specialized and S is generalized until they converge on the concept.
