# Problem solving agents
- When the correct action to take is not immediately obvious, agents may need to plan their moves and actions ahead of time. That is, they need to consider a sequence of actions that form a path leading them to a goal state. Such agents are called **problem solving agents**. 
- The computational processes problem solving agents undertake are referred to as **searches**. 
### In depth Example: 
- Our solving agent is in Arad, Romania. 
	- **Goal:** Go to Bucharest. 
	- **Knowns:** Romania's map is known to the agent.
	- **Unknowns:** What to do and which path to take. 
![[search_agent_map.PNG]]
- On holiday in Romania : Currently in Arad. 
- Flight leaves tomorrow from Bucharest. 
```bash
Formulate goal: 
	be in Bucharest
Formulate problem: 
	states: various cities 
	actions: drive between cities
Find a solution: 
	sequence of cities, e.g, Arad, Sibiu, Fagaras, Bucharest <-- Goal destination
```
- An important property to note is that in a **Fully observable, deterministic, known environment**, the solution to any problem is a fixed sequence of actions. Ex: Drive to Sibiu, then Fagaras, then Bucharest. 
- If the model is correct, once the agent finds a solution, it can **ignore its percepts** while executing its action, essentially closing its eyes, so to speak. 
- Many control theorists call this an **open-loop system**: Ignoring the percepts breaks the loop between the agent and its environment.
- If there is a chance the model is incorrect or the environment is nondeterministic, the agent would be safer using a closed-loop approach that monitors the percepts. 
## Search problems
- Formally, a search problem is defined through the following 6 properties: 
	- 1: A set of possible states that the environment can be in. This is called the **state space**. 
	- 2: The **initial state** the agent starts in. 
	- 3: A set of **one or more goal states**: 
		- 3a: One goal state. 
		- 3b: A small set of alternative goal states. 
		- 3c: The goal is defined by a property that applies to many states (Potentially an infinite number of states).
		- Ex: in a vacuum-cleaner world, the goal might be to **have no dirt in any location**, regardless of any other facts about the state. 
		- We can account for all three of these possibilities by specifying an **Is-Goal** method for a problem.
	- 4: **The actions available to the agent**. Given a state $s$, $ACTIONS(s)$ returns a **finite set** of actions that can be executed in $s$. It can be said that each of these actions is applicable in $s$.
		- Ex: $ACTIONS(Arad) = \space \{ToSibiu, ToTimisoara, ToZerind\}$
	- 5: **A transition model**, which describes what each action does. $RESULT(s,a)$ returns the sate that results from doing action $a$ in state $s$. 
		- Ex: $RESULT(Arad, ToZerind) = \space Zerind$
	- 6: **An action cost function**, denoted by $ACTION_COST(s,a,s')$ that gives the numeric cost of applying action $a$ in a state $s$ to reach state $s'$. 
		- A problem solving agent should use a cost function that **reflects its own performance measure**. 
		- Ex: For route-finding agents, the cost of an action might be the length of the route in miles, or it might be the time it takes to complete the action itself. 

- A sequence of actions forms a **path**. 
- A solution is a **path** from the initial state to a **goal state**. 
- We can assume that action costs are **additive**, that is, the total cost of a path is the sum of the individual action costs. 
- An **optimal solution** has the lowest path cost amongst all other solutions. This is to say, the action cost function was **minimized**. 
- The state space can be represented as a **graph** in which the **vertices are states** and the **directed edges are actions**.
- The process of eliminating useless details from a representation is called **abstraction**. 
## Problem types 
- Deterministic, fully observable $\rightarrow$ single-state problem
	- Agents know exactly which state they will be in. The solution is a sequence.

- Non-Observable $\rightarrow$ Conformant problem
	- Agents may have no idea where they are. The solution (if any) is a sequence.

- Nondeterministic and/or partially observable $\rightarrow$ Contingency problem
	- Percepts provide new information about the current state.
	- The solution is a contingency plan or a policy.
	- Searching and execution are often interleaved.
	
- Unknown state space $\rightarrow$ exploration problem("online")
- Ex: 
	![[search_prob_ex.PNG]]
#### Single-State problem formulation
- A problem is defined by four items: 
```c++
initial state = Arad

successor function S(x) = set of action_state pairs
	S(Arad) = {(Arad -> Zerind, Zerind), ...}

goal test can be
	explicit, x = "At Bucharest"
	implicit, NoDirt(x)
	
Path cost(additive)
	Sum of distances, number of actions executed, etc. 
	C(x,a,y) = The step cost (Assumed to be >= 0)

A solution is a sequence of actions
Leading from the initial state to a goal state
```
#### Selecting a state space 
- The real world is absurdly complex $\rightarrow$ The state space must be **abstracted** for problem solving. 
```c++
(Abstract) state = set of real states

(Abstract) action = complex combination of real actions 
	"Arad -> Zerind" represents a complex set of possible routes, detours, etc.
	For guaranteed realizability, any real state "In Arad" must get to "some" real
	state "In Zerind"

(Abstract) solution = set of real paths that are solutions in the real world

Each abstraction should be "easier" than the original problem
```
- Ex - The  vacuum: 
![[search_vacuum.PNG]]
- Ex - The 8 puzzle: 
![[search_8_puzzle.PNG]]
## Tree search algorithms
- A search algorithm takes a search problem as input and returns a solution or an indication of failure. 
- We will consider search algorithms that **superimpose** a **search tree**  over the state space graph, in turn forming various paths from the initial state in hopes of finding a path that reaches the desired goal state. 
- Each node in the search tree will correspond to a state in the state space and the edges in the tree will corrrespond to the actions of the state space. 
- The root of the tree will correspond to the initial state of the problem. 
- It is important to note and understand key distinctions between the state space and the search tree: 
	- The state space describes the (possibly infinite) set of states in the world, and the actions that allow transitions from one state to another. 
	- The search tree describes paths between these states, **extending and reaching towards the goal**.  
	- The search tree may have multiple paths to (and thus, multiple nodes) for any given state, however, each node in the tree has a unique path back to the root, as in all trees.
- Here is the basic idea:  
	- Offline, simulated exploration of the state space done by generating successors of already explored states (expanding states).
- Formalized into pseudo-code: 
```javascript
function Tree_Search(problem, strategy) returns a solution or failure
	initialize the search tree using the initial state of the problem 
	loop do 
		if there are no candidates for expansion then return failure
		choose a leaf node for expansion according the strategy 
		if the node contains a goal state then return the corresponding solution 
		else expand the node and add the resulting nodes to the search tree
	end 
```
![[search_agent_tree.PNG]]
- Discovery sequence: Arad (root)
- Queue: Sibiu, Timisoara, Zerind
- Discovery sequence: Arad (root) $\rightarrow$ Sibiu (FIFO)
- After discovering Sibiu, the path to the goal state is found: 
	- Arad $\rightarrow$ Sibiu $\rightarrow$ Fagaras $\rightarrow$ Bucharest. 