# Informed (Heuristic) Search Strategies 
- This section shows how an informed search strategy, one that uses domain specific hints about the location of goals, can find solutions more efficiently than an uninformed search strategy. 
- The hints come in the form of a **heuristic function** denoted $h(n)$.
- $h(n) =  \text{estimated cost of the cheapest path from the state at node } n \text{ to the goal}$ 
- For example: In route finding problems, we can estimate the distance from the current state to a goal by computing the **straight-line distance** on the map between two points.
![[map_search.PNG]]
## Greedy search
- **Greedy best-first search** is a form of best-first search that expands the first node with the lowest value, the node that appears the closest to the goal on the grounds that this is a likely lead to a quick solution. This is done through the evaluation function: $f(n) = h(n)$
- The values of $h_{sld}$ cannot be computed from the problem description itself, that is, the `ACTIONS` and `RESULT` functions. 
- It takes a certain amount of **world knowledge** to know that $h_{sld}$  is **correlated** with actual road distances and is a useful **heuristic**. 
```
Evaluation function h(n) (heuristic)
	= estimated cost from n to the closest goal
	E.g., h_sld(n) = straight-line distance from n to Bucharest
Greedy search expands the node that appears to be closest to the goal
```
### Greedy search example execution
![[1.PNG]]

![[2.PNG]]

![[3.PNG]]

![[4.PNG]]

-  For this particular problem, greedy best-first search using $h_{sld}$ finds a solution without ever expanding a node that is not on the solution path. 
- However, the solution found is not cost optimal, the path via Sibiu and Fagaras to Bucharest is 32 miles longer than the path through Rimnicu Vilcea and Pitesti. This is why the algorithm is called **"greedy"**, on each iteration, it tries to get as close to a goal as it can, but greediness can lead to worse results than being careful. 
- Greedy best-first graph search is complete in finite state spaces but not in infinite ones. 
- With a good heuristic function, the complexity can be reduced substantially, on certain problems, it can reach a Time Complexity of $O(bm)$. 
### Properties of greedy search
- **Complete:** No, it can get stuck in loops, e.g. $Iasi \rightarrow Neamt \rightarrow Iasi \rightarrow Neamt \rightarrow ...$
  Complete in finite spaces with repeated-state checking. 
- **Time complexity:** $O(b^m)$, a good heuristic can give dramatic improvements. 
- **Space:** $O(b^m)$, Keeps all nodes in memory. 
- **Optimal:** No. 
## A* Search 
- The most common informed search algorithm is A* search. 
- A **Best-first search** algorithm that uses the evaluation function: $f(n) = g(n) + h(n)$
  Where: 
	- $g(n)$ is the path cost from the initial state to the node $n$ 
	- $h(n)$ is the estimated cost of the shortest path from $n$ to a goal state
	- $f(n) = \text{estimated cost of the best path that continues from } n \text{ to the goal}$
- The main idea behind A* search is to avoid expanding paths that are already expensive. 
- Through the evaluation function $f(n) = g(n) + h(n)$
	- $g(n) = \text{real/actual cost so far to reach }n$
	- $h(n) = \text{estimated cost to a goal state from }n$
	- $f(n) = \text{estimated total cost of a path through }n \text{ to a goal state}$
	- A* uses an **admissible** heuristic. i.e., $h(n) \leq h^*(n)$ where $h^*(n)$ is the true cost from $n$
	  This also requires $h(n) \geq 0$, so $h(G) = 0$ for any goal $G$. 
	- E.g. $h_{sld}(n)$ **never overestimates the actual road distance **
	- **Theorem:** A* search is optimal. 
### A* search example 
![[Images/informed_search/a_star_search/1.PNG]]

![[Images/informed_search/a_star_search/2.PNG]]

![[Images/informed_search/a_star_search/3.PNG]]

![[Images/informed_search/a_star_search/4.PNG]]

![[5.PNG]]

![[6.PNG]]
### Optimality of A*
- Suppose some suboptimal goal $G_2$ has been generated and is in the queue. Let $n$ be an unexpanded node on a shortest path to an optimal goal $G$.
- ![[proof_1.PNG]]
	- $f(G_2) = g(G_2), \text{     Since } h(G_2) = 0$
	- $f(G_2) > g(G), \text{     Since } G_2 \text{ is suboptimal}$
	- $f(G_2) \geq f(n), \text{     Since } h \text{ is admissible}$
	- Since $f(G_2) > f(n)$, A* will never select $G_2$ for expansion. 
- **Lemma:** A* expands nodes in order of increasing $f$ value*. It gradually adds "$f$-contours" of nodes. Contour $i$ has all nodes with $f = f_i$ , where $f_i < f_{i+1}$ . 
- ![[countour.PNG]]
### Properties of A*
- **Complete:** Yes, unless there are infinitely many nodes with $f \leq f(G)$. 
- **Time complexity:** Exponential in relative error in $h \times \text{length of the solution}$. 
- **Space:** Keeps all nodes in memory. 
- **Optimal:** Yes, cannot expand $f_{i+1}$ until $f_i$ is finished. 
	- A* expands all nodes with $f(n) < C*$ 
	- A* expands some nodes with $f(n) = C*$
	- A* does not expand nodes with $f(n) > C*$
## Admissible heuristics 
- There are $9!/2$ reachable states in an 8-puzzle, so a search could easily keep them all in memory. 
- However, for the 15-puzzle, there are $16!/2$ states, over 10 trillion, to search that space, one will require the help of a good and **admissible heuristic function**. 
- There are two commonly used candidates for the 15-puzzle: 
- ![[puzzle.PNG]]
- E.g., for the 8-puzzle: 
	- $h_1(n) = \text{The number of misplaced tiles (blanks included)}$
	- $h_2(n) = \text{Total Manhattan distance}$
	- ![[puzzle_2.PNG]]
	- $H_1$ is an admissible heuristic because any tile that is out of place will require at least one move to get in the right place. 
	- $H_2$ is also admissible because the only thing any move can do is move one tile, one step closer to the goal. 
### Dominance 
- If $h_2(n) \leq h_1(n), \forall \space n \text{ (Both admissible)}$, then $h_2$ **dominates** $h_1$ and is better for search. 
- Typical search costs: 
	- $d = 14$ : 
		- $IDS = 3,473,941  \text{ Nodes}$
		- $A*(h_1) = 539 \text{ Nodes}$
		- $A*(h_2) = 113 \text{ Nodes}$
	- $d = 24$ : 
		- $IDS = 54,000,000,000  \text{ Nodes}$
		- $A*(h_1) = 39,135 \text{ Nodes}$
		- $A*(h_2) = 1,641 \text{ Nodes}$
- Given any admissible heuristics $h_a, h_b$ : 
	- $h(n)  = \max(h_a(n), h_b(n))$, is also admissible and dominates $h_a, h_b$ 
### Relaxed problems
- Admissible heuristics can be derived from the **exact** solution cost of a **relaxed** version of the problem. 
	- If the rules of the 8-puzzle are relaxed so that a tile can move **anywhere**, then $h_1(n)$ gives the shortest solution. 
	- If the rules are relaxed so that a tile can move to **any adjacent square**, then $h_2(n)$ gives the shortest solution.
	- **Key point:**  The optimal solution cost of a relaxed problem is no greater than the optimal solution cost of the real problem. 
## Summary
- A problem consists of five parts: 
	- The initial state
	- A set of actions
	- A transition model describing the results of those actions
	- A set of goal states 
	- An action cost function
- Uninformed search methods have access only to the problem definition. Algorithms build a search tree in attempt to find a solution. 
- Informed search methods have access to a heuristic function $h(n)$ that estimates the cost of a solution from $n$. 