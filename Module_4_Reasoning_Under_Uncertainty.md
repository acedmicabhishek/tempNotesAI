# Module 4: Reasoning Under Inconsistencies and Uncertainties

## 4.1 Reasoning Under Inconsistencies (Non-Monotonic Reasoning)

Classical logic is **monotonic**: if a sentence *P* is inferable from a knowledge base *KB*, it is still inferable from *KB + NewFact*.
**Non-monotonic reasoning** deals with situations where new information may invalidate previous conclusions (e.g., "Birds fly" -> "Penguins are birds" -> "Penguins don't fly").

### 4.1.1 Truth Maintenance Systems (TMS)
*   **Purpose:** To maintain the consistency of a knowledge base (KB) as new expressions are added or beliefs change.
*   **Justification-Based TMS (JTMS):** Every belief has a justification. If the justification becomes invalid, the belief is retracted.
*   **Assumption-Based TMS (ATMS):** Maintains multiple contexts (sets of assumptions) simultaneously.

### 4.1.2 Default Reasoning
*   **Concept:** Drawing plausible conclusions in the absence of evidence to the contrary.
*   **Default Logic:** Introduces new inference rules: A : B / C ("If A is true, and it is consistent to assume B, then infer C").
    *   Example: Bird(x) : Flies(x) / Flies(x).

### 4.1.3 Closed World Assumption (CWA)
*   **Assumption:** If a fact is not known to be true in the KB, it is assumed to be false.
*   **Application:** Database systems (e.g., if a flight isn't listed, it doesn't exist).

### 4.1.4 Predicate Completion
*   **Concept:** Completing a definition by assuming the "only if" direction.
*   **Example:** If the only rule for `Owl` is `Owl(x) => Bird(x)`, completion adds `Bird(x) => Owl(x)` (simplification), assuming these are the *only* conditions.

### 4.1.5 Circumscription
*   **Concept:** A formalized rule of conjecture that things are as expected unless specified otherwise. It minimizes the extension of abnormal predicates. "Everything is normal unless stated otherwise."

### 4.1.6 Fuzzy Logic
*   **Origin:** Lotfi Zadeh (1965).
*   **Concept:** Deals with degrees of truth rather than binary True/False.
*   **Fuzzy Sets:** An element belongs to a set with a certain **membership grade** (0 to 1).
    *   Example: "Tall" is not a crisp set. A person 180cm might be 0.7 "Tall".
*   **Application:** Control systems (washing machines, ABS brakes) where rules are vague ("If water is dirty, wash longer").

## 4.2 Probabilistic Reasoning (Reasoning Under Uncertainty)

### 4.2.1 Bayesian Probabilistic Inference
*   **Bayes' Theorem:** Describes how to update the probability of a hypothesis (H) evidence (E) is observed.
*   **Formula:** `P(H|E) = [P(E|H) * P(H)] / P(E)`
    *   `P(H|E)`: Posterior probability (probability of H given E).
    *   `P(H)`: Prior probability (initial probability of H).
    *   `P(E|H)`: Likelihood (probability of evidence E given H is true).
    *   `P(E)`: Marginal likelihood.

### 4.2.2 Representation of Knowledge in Uncertain Domain
*   **Joint Probability Distribution:** A table specifying probabilities for all possible combinations of variable assignments.
*   **Problem:** Exponential growth (2^n) makes full joint distribution intractable. independence assumptions are needed.

### 4.2.3 Bayesian Networks (Belief Networks)
*   **Definition:** A Directed Acyclic Graph (DAG) that represents a set of random variables and their conditional dependencies.
*   **Structure:**
    *   **Nodes:** Random variables.
    *   **Edges:** Direct influence (Parent -> Child).
    *   **CPT (Conditional Probability Table):** Each node has a table quantifying the effect of parents.
*   **Semantics:** A node is conditionally independent of its non-descendants given its parents. This drastically reduces the number of probabilities required.

### 4.2.4 Dempster-Shafer Theory
*   **Purpose:** A general framework for reasoning with uncertainty, allowing for the representation of *ignorance* separate from *uncertainty*.
*   **Mass Function (m):** Assigns a probability mass to subsets of the frame of discernment.
*   **Belief (Bel):** Lower bound of probability (evidence definitely supporting the proposition).
*   **Plausibility (Pl):** Upper bound of probability (evidence not contradicting the proposition).
*   **Interval:** [Bel(A), Pl(A)] represents the uncertainty about A.
