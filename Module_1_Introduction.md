# Module 1: Introduction to Artificial Intelligence

## 1.1 Overview of AI

**Artificial Intelligence (AI)** is the branch of computer science concerned with building smart machines capable of performing tasks that typically require human intelligence. These tasks include learning, reasoning, problem-solving, perception, and language understanding.

### Definitions of AI
*   **Systems that think like humans:** "The exciting new effort to make computers think... machines with minds, in the full and literal sense." (Haugeland, 1985)
*   **Systems that think rationally:** "The study of mental faculties through the use of computational models." (Charniak and McDermott, 1985)
*   **Systems that act like humans:** "The art of creating machines that perform functions that require intelligence when performed by people." (Kurzweil, 1990)
*   **Systems that act rationally:** "Computational Intelligence is the study of the design of intelligent agents." (Poole et al., 1998)

## 1.2 Problems of AI

The core problems of AI research include:

1.  **Reasoning, Problem Solving:** Step-by-step reasoning used by humans to solve puzzles or make logical deductions.
2.  **Knowledge Representation:** Representing information about the world in a form that a computer system can utilize to solve complex tasks.
3.  **Planning:** Setting goals and achieving them by executing a sequence of actions.
4.  **Learning:** Improving performance based on experience (Machine Learning).
5.  **Natural Language Processing (NLP):** Giving machines the ability to read and understand human language.
6.  **Perception:** Using input from sensors (such as cameras and microphones) to deduce aspects of the world (Computer Vision, Speech Recognition).
7.  **Motion and Manipulation:** Moving and manipulating objects (Robotics).
8.  **Social Intelligence:** Affective computing and recognizing human emotion.

## 1.3 AI Techniques

AI techniques are methods used to solve problems that are difficult for conventional programming. Key characteristics of AI techniques:
*   **Use of knowledge:** AI programs capture, organize, and use knowledge.
*   **Heuristic search:** Often used when an exact solution is too costly or impossible to find.
*   **Abstraction:** Handling complex problems by hiding details.

Common techniques include:
*   **Search Algorithms:** BFS, DFS, A*, etc.
*   **Neural Networks:** Inspired by the biological brain.
*   **Logic-based systems:** Prolog, etc.
*   **Probabilistic methods:** Bayesian networks.

## 1.4 Problem Solving

Problem solving in AI is typically modeled as a search through a state space.

### 1.4.1 Problem Space and Search
A **Problem Space** is an abstract environment in which a problem can be formulated. It consists of:
*   **States:** Snapshots of the problem at a given moment.
*   **Operators:** Actions that transform one state into another.

**Search** is the process of navigating the problem space to find a path from the initial state to a goal state.

### 1.4.2 Defining the Problem as State Space Search
To define a problem formally, we need four components:
1.  **Initial State:** The state in which the agent begins.
2.  **Goal Test:** A condition that determines if a given state is the goal state.
3.  **Successor Function (Operators):** A description of possible actions available in a given state. Returns a set of <action, result> pairs.
4.  **Path Cost:** A function that assigns a numeric cost to each path.

**Example: The 8-Puzzle**
*   **States:** Location of each of the 8 tiles and the blank.
*   **Initial State:** Any state.
*   **Goal State:** Tiles arranged in order.
*   **Operators:** Move blank Left, Right, Up, Down.

### 1.4.3 Problem Characteristics
To choose an appropriate method, we analyze the problem's characteristics:
1.  **Is the problem decomposable?** Can it be broken down into smaller sub-problems? (e.g., integrals).
2.  **Can solution steps be ignored or undone?** (Ignorable: Theorem proving; Recoverable: 8-puzzle; Irrecoverable: Chess).
3.  **Is the universe predictable?** (Certainty vs. Uncertainty).
4.  **Is a good solution absolute or relative?** (Is there a "best" path or just "any" path?).
5.  **Is the knowledge base consistent?**
6.  **What is the role of knowledge?** (Is a lot of knowledge required or just search?).
7.  **Does the task require interaction with a person?**

### 1.4.4 Tic-Tac-Toe Problem
A classic example to illustrate state space search and complexity.
*   **States:** Board configurations (X's and O's).
*   **Complexity:** Small enough to be fully solved (9! initial estimates, but much smaller due to symmetry).
*   **Approach:**
    *   **Simple:** Look-up table (too large for complex games).
    *   **Heuristic:** Rule-based (e.g., "If 2 in a row, block").
    *   **Minimax Search:** Look ahead to see the outcome of moves.

## 1.5 AI Languages

Specialized languages were developed for AI to handle symbolic processing better than standard procedural languages.

### 1.5.1 LISP (List Processing)
*   **Developed:** By John McCarthy in 1958.
*   **Key Feature:** Everything is a list. Code and data are represented the same way (homoiconicity).
*   **Strengths:**
    *   Excellent for symbolic manipulation.
    *   Dynamic typing and memory management (Garbage Collection).
    *   Recursion is the primary control structure.
    *   REPL (Read-Eval-Print Loop) environment.
*   **Syntax Example:** `(+ 1 2)` adds 1 and 2.

### 1.5.2 Prolog (Programming in Logic)
*   **Developed:** By Alain Colmerauer and Robert Kowalski in 1972.
*   **Key Feature:** Declarative programming logic. You define *facts* and *rules*, and the engine figures out the control flow to satisfy a query.
*   **Strengths:**
    *   Pattern matching and unification.
    *   Automatic backtracking.
    *   Great for expert systems and natural language parsing.
*   **Syntax Example:**
    ```prolog
    parent(john, mary).     % Fact: John is the parent of Mary.
    female(mary).           % Fact: Mary is female.
    daughter(X, Y) :- parent(Y, X), female(X). % Rule
    ```
