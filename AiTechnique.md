# AI Techniques

AI techniques are a specific set of methods used to solve complex problems that are difficult for conventional programming 
paradigms to handle. These problems are typically characterized by uncertainty, high complexity, and a lack of a clear, 
step-by-step algorithmic solution.

According to standard AI literature (e.g., *Rich & Knight*), a method is considered an **AI Technique** if it efficiently handles 
complexity using three core principles: **Knowledge**, **Search**, and **Abstraction**.

## 1. Use of Knowledge
Standard algorithms (like sorting or calculating a square root) follow a fixed recipe on data. AI techniques, however, 
rely heavily on **domain knowledge** to solve problems.

*   **What it is:** AI systems must capture, organize, and utilize knowledge about the world (e.g., rules of a game, medical symptoms, grammar).
*   **Why it's unique:** The knowledge is often voluminous, constantly changing, and difficult to represent precisely. AI techniques allow this knowledge to be separated from the control code.
    *   *Example:* In Expert Systems, the "Knowledge Base" (facts/rules) is separate from the "Inference Engine" (logic that applies rules).
*   **Application:** A medical diagnosis system doesn't just match strings; it understands relationships like `Symptom A -> Disease B` and uses that knowledge to infer probabilities.

## 2. Heuristic Search
Many AI problems are "NP-hard" or have search spaces so vast (e.g., Chess, Go, Route Planning) that checking every possibility is impossible within a reasonable time.

*   **What it is:** Search is the process of navigating through states to find a solution. **Heuristics** are "rules of thumb" or educated guesses used to guide this search toward the goal more efficiently, sacrificing guaranteed perfection for speed.
*   **Why it's unique:** Unlike a standard database query that finds an exact match, AI search explores options. A heuristic might say "moving this chess piece looks promising because it controls the center," helping the AI ignore millions of bad moves.
*   **Application:** In **A* Search** (commonly used in Maps/GPS), the algorithm doesn't explore every single road; it prioritizes roads that head generally towards the destination.

## 3. Abstraction
Real-world problems are messy and detailed. AI techniques simplify these problems to make them computable.

*   **What it is:** Abstraction involves hiding unnecessary details to focus on the essential features of a problem.
*   **Why it's unique:** It reduces the complexity of the state space. By ignoring "noise," the AI can apply generalized rules to a wide range of situations.
*   **Application:** When an AI learns to recognize a "chair," it abstracts the concept (legs, seat, back) rather than memorizing every specific pixel configuration of every chair in existence.

## Comparison: AI Techniques vs. Standard Programming

| Feature | Standard Programming | AI Techniques |
| :--- | :--- | :--- |
| **Focus** | **Data driven:** Algorithms process data. | **Knowledge driven:** Knowledge directs the processing. |
| **Precision** | **Exact:** Exact solution is usually required. | **Heuristic:** A "good enough" solution is often acceptable. |
| **Input** | **Specific:** Designed for rigid, specific input. | **Generalizable:** Uses abstraction to handle variation and ambiguity. |
| **Structure** | Control and data are often mixed. | Control (inference) is separate from knowledge. |
| **Modification** | Changing code affects the program structure. | Knowledge can be updated without rewriting the engine. |
