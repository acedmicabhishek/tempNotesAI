# 1.5 AI Languages

In the early days of Artificial Intelligence, researchers realized that standard procedural languages (like Fortran or C) were not ideal for the kinds of problems they were trying to solve. AI problems often involve **symbolic processing**—manipulating symbols and structures—rather than just crunching numbers. This led to the development of specialized AI languages.

The two most prominent AI languages are **LISP** and **Prolog**.

---

## 1.5.1 LISP (List Processing)

**LISP** is the second-oldest high-level programming language still in common use (after Fortran). It was created to facilitate symbolic computation and has deeply influenced the development of AI.

### Overview
*   **Developed By:** John McCarthy (father of AI) in 1958 at MIT.
*   **Key Feature:** **Homoiconicity**. This means "code is data." In Lisp, both source code and data structures are represented as **Lists**. This allows Lisp programs to easily manipulate other Lisp programs (metaprogramming).
*   **Primary Data Structure:** The Linked List.

### Major Strengths
1.  **Symbolic Manipulation:** Excellent at processing symbols and words, which is core to early AI.
2.  **Recursion:** It relies heavily on recursion as a control structure, which maps well to many AI algorithms (like tree search).
3.  **Dynamic Typing & Memory:** Automatic garbage collection relieves the programmer from manual memory management.
4.  **REPL (Read-Eval-Print Loop):** Allows for interactive programming and rapid prototyping.

### Basic Syntax (Common Lisp / Scheme flavor)
Lisp syntax uses **S-expressions** (symbolic expressions), which are parenthesized lists.
*   Prefix notation: The operator always comes first. `(operator operand1 operand2 ...)`

#### 1. Arithmetic
```lisp
(+ 1 2)        ; Returns 3
(* 5 (+ 2 3))  ; Returns 25. Evaluate inner parens first: (* 5 5)
```

#### 2. Defining Variables and Functions
```lisp
(defvar *x* 10)       ; Define a global variable x with value 10

; Function to square a number
(defun square (n)
  (* n n))

(square 5)            ; Returns 25
```

#### 3. List Operations
*   `car`: Returns the **first** element of a list (Heads).
*   `cdr`: Returns the **rest** of the list (Tails).
*   `cons`: Constructs a list.

```lisp
(car '(A B C))        ; Returns A
(cdr '(A B C))        ; Returns (B C)
(cons 'A '(B C))      ; Returns (A B C)
```

#### 4. Conditional Logic
```lisp
(if (> 10 5)
    'greater
    'smaller)         ; Returns GREATER
```

---

## 1.5.2 Prolog (Programming in Logic)

**Prolog** represents a fundamentally different paradigm called **Logic Programming**. Instead of telling the computer *how* to do something (step-by-step), you tell it *what* is true (facts) and *what* relationships exist (rules), and the computer figures out how to satisfy queries.

### Overview
*   **Developed By:** Alain Colmerauer and Robert Kowalski in 1972.
*   **Key Feature:** **Declarative Programming**. You define the logic, and the internal engine handles the control flow using resolution and unification.

### Major Strengths
1.  **Pattern Matching & Unification:** Powerful built-in engine for matching complex data structures.
2.  **Backtracking:** Automatically searches for solutions. If a path fails, it backs up and tries another possibility (like DFS) without you writing the loop.
3.  **Knowledge Representation:** Very natural for expressing "Relations" (e.g., `ParentOf(X, Y)`).
4.  **Applications:** Expert Systems, Natural Language Processing (NLP), Constraint Satisfaction Problems.

### Basic Syntax
Prolog programs consist of **Facts**, **Rules**, and **Queries**.
*   **Constants:** Lowercase (`john`, `cat`).
*   **Variables:** Uppercase (`X`, `Who`).

#### 1. Knowledge Base (Facts & Rules)
```prolog
% --- Facts ---
% "John is a parent of Mary"
parent(john, mary).
parent(john, tom).
parent(mary, ann).

% "Mary is female"
female(mary).
female(ann).
male(john).
male(tom).

% --- Rules ---
% "X is a sister of Y IF X and Y share a parent Z, and X is female, and X is not Y."
sister(X, Y) :-
    parent(Z, X),
    parent(Z, Y),
    female(X),
    X \= Y.

% Recursive Rule for Ancestry
ancestor(X, Y) :- parent(X, Y).              % Base case: Parent is an ancestor
ancestor(X, Y) :- parent(X, Z), ancestor(Z, Y). % Recursive step
```

#### 2. Queries (Asking the system)
You load the knowledge base and ask questions.

**Query 1: Is John the parent of Mary?**
```prolog
?- parent(john, mary).
true.
```

**Query 2: Who are John's children?** (Using variable `X`)
```prolog
?- parent(john, X).
X = mary ;   % User types semicolon to ask "anyone else?"
X = tom.
```

**Query 3: Who is Ann's grandfather?**
Prolog automatically finds the link: Ann -> Mary -> John.
```prolog
?- ancestor(X, ann), male(X).
X = john.
```

### Summary Comparison

| Feature | LISP | Prolog |
| :--- | :--- | :--- |
| **Paradigm** | Functional (Multi-paradigm) | Logic / Declarative |
| **Code Structure** | Recursive Functions over Lists | Facts and Inference Rules |
| **Primary/Unique** | Homoiconicity (Code = Data) | Unification & Backtracking |
| **Best For** | General AI, Search, Symbolic Math | Expert Systems, Reasoning, NLP |
