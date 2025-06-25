# [[CHAPTER_1_INTRODUCTION]]
- What is AI ? 
	- Systems that think like humans 
	- Systems that think rationally 
- Turing test 
	- Can machines behave intelligently ? 
	- Operational test: The imitation game, developed in 1950
- Can machines think ? 
	- NLP 
	- Knowledge representation 
	- Automated reasoning 
	- Machine learning 
- 1960's arrival of Cognitive revolution: 
	- The desire to understand how humans think, to imitate and replicate that through a machine 
- Rational thought is thinking in a normal/prescriptive way rather than in a descriptive way 
- Problems of rational thought: 
	- Not all intelligent behavior is mediated by logical deliberation
	- Purpose of thinking: What thoughts should I have out of all the thoughts I could have ? 
	- Are the premises of thought we have always certain or correct ? 
- Agents are entities that perceive and act, un-prompted out of their own volition. They react to their environment and make logical decisions. 
	- Operate autonomously 
	- Perceive their environment 
	- Persist over time 
	- Adapt to change 
	- Create and pursue goals
- Rational agents strive to gain the best or best possible outcome given their situation
- Benefits of AI: 
	- Eliminating repetitive work
	- Increasing production of goods and services 
	- Accelerating scientific research 
- Risks of AI: 
	- Lethal autonomous weapons 
	- Surveillance and persuasion 
	- Biased decision making 
	- Impact on employment 
	- Safety-Critical applications 
	- Cyber-Sec Threats
- Gorilla problem: Humans are primates with super-intelligence, thus we reign over all other primates. We need to design AI systems that don't end up taking control over us, the way Turing speculated they might. 
# [[CHAPTER_2_ENVIRONMENT]]
- Agents can be humans, robots, thermostats, etc. 
	- Anything that perceives it's environment
- Spatial perception through sensors, actions through actuators
	- Agent function maps from percept histories to actions using $f$ : $P^* \rightarrow A$
	- Agent programs run direction on physical devices to produce $f$
- Rational agents are agents that do the **right thing** 
	- **Desirability** is captures by a performance measure to evaluate an environmental sequence
- Rationality depends on 4 factors: 
	- The performance measure that defines the criteria of success
	-  The agent's prior knowledge of the environment 
	- The set of actions that the agent is able to perform 
	- The agent's percept sequence to date 
- An agents performance in any task must be measurable and quantifiable 
	- The environment must be clearly defined
	- The set of mechanical mediums must be clearly defined
- The task environment qualities: 
	- Performance measure
	- Environment
	- Actuators
	- Sensors
- Environment types: 
	- Fully observable, Partially observable, Un-observable
		- Fully observable if: Provided the complete state of the environment
		- Partially observable if: Missing states from the sensor data or noisy/inaccurate data
		- Un-Observable if: No sensors at all 
	- Single-agent, Multi-agent
		- Single-agent: Vacuum cleaner
		- Multi-agent: Chess (Competitive), Self-Driving taxi (Partially Cooperative/Competitive)
	 - Deterministic, Non-deterministic
		 - Deterministic if: The next possible state of the environment is determined **ONLY** by the current state and any action executed by an agent. 
		 - Non-deterministic if: Anything else
	- Determinism, Stochastic-ism 
		- Stochastic if: Explicitly deals with probabilities
		- Deterministic if: Anything else 
	- Episodic, Sequential
		- Episodic: The agent's experience is sub-divided into smaller atomic episodes. In each episode agents receive a percept and perform a singular action. Subsequent episodes do not depend on the actions taken in previous episodes. 
		- Sequential: Current decisions affect all future decisions  
	- Static, Dynamic
		- Dynamic if: The environment is subject to change whilst an agent is deliberating
		- Static if: Anything else
		- Semi-Dynamic if: The environment itself doesn't change with the passage of time but the agents performance score does
	-  Discrete, Continuous
	- Known, Un-Known
		- Refers to the agent's state of knowledge, the laws of the environment and not the environment itself 
		- Card game: Some cards not turned over $\rightarrow$ Partially observable, known environment 
		- Video game: Fully observable since we can see the whole screen, Un-known environment until all the game controls have been discovered and memorized

|               | Solitatire | Backgammon |   Internet Shopping   | Taxi |
| :-----------: | :--------: | :--------: | :-------------------: | :--: |
|  Observable   |    Yes     |    Yes     |          No           |  No  |
| Deterministic |    Yes     |     No     |        Partly         |  No  |
|   Episodic    |     No     |     No     |          No           |  No  |
|    Static     |    Yes     |    Semi    |         Semi          |  No  |
|   Discrete    |    Yes     |    Yes     |          Yes          |  No  |
| Single-Agent  |    Yes     |     No     | Yes (except auctions) |  No  |
-  The real world is partially observable, stochastic, sequential, dynamic, continuous and multi-agentic 
- An agents construction is called the agent architecture: $agent \space =  \space architecture \space + \space program$
- There are four basic agent types (In order of increasing generality): 
	- Simple Reflex agents 
	- Model-Based reflex agents (with state)
	- Goal-Based agents
	- Utility-Based agents (For customer satisfaction)
	- All these agents can be turned into learning agents
# [[CHAPTER_3_LEARNING]]
- There  are 3 mains forms of learning: 
	- Supervised learning: 
		- Agent will learn a function from observing input-output pairs 
	- Un-supervised learning: 
		- Agent will recognize patterns from the input data without explicit feedback 
	- Reinforcement learning: 
		- Agent will learn through a series of reinforcement routines, using a penalty and reward system. 
- Supervised Learning: 
	- We have a function $h$ called the hypothesis about the agents world, this is supposed to approximate a true function $f$ where from a set of inputs and outputs $N$, $(x_1,y_1),(x_2,y_2), \space...\space(x_N, y_N)$, Generated by an **unknown** function $f$ ,where $y = f(x)$
	- $h$ is draw from the hypothesis space $H$ of possible functions
	- $h$ is a model of the data draw from the model class $H$
	- A consistent hypothesis is when $h(x_i) = y_i$
	- $h$ looks for a **best-fit function**, meaning gives values that are close enough to the outputs of the true function $f$
- Hypothesis space: 
	- Set of possible functions: 3rd degree polynomials,  JS Functions etc. 
	- $y_i$, the output of the original function is typically called the **ground truth** 
	- If we don't know the process that generated the data set, we can perform **exploratory data analysis** using: 
		- Histograms
		- Scatter plots
		- Performance tests on multiple hypothesis spaces 
	 - Bias: The tendency of a predictive hypothesis to deviate from the expected value
	 - Underfitting: The models fails to find any type of pattern in the data
	 - Overfitting: The model pays too much attention to a particular data set, subsequently fails to generalize for different data sets 
	 - Variance: The amount of change in the data set
	 - Bias-Variance tradeoff: More complex, low-bias hypotheses that fit the training data better, or, low-variance hypotheses that generalize better. 
- Probabilities: 
	- Required to determine how probable a hypothesis is of occurring
	- Hypothesis $h^*$ that is most probable is : $h^* = argmax \space P(h|data), \space h \in H$
	- Using Bayes' rule: $h^* = argmax \space P(h|data)P(h)$ 
		-  $P(h)$ is the prior probability of $h$ and $P(data)$ is the posterior probability of $h$
		- Often used to select the most probable hypothesis according to the observed data.
- Decision trees: 
	- Representation of a function that maps a vector of attribute values to a single output value 
	- Decisions are reached through sequential tests from the root node until a leaf node is reached 
	- Internal nodes each correspond to a test value of one of the input attributes
	-  Branches from the nodes are all labeled with all possible attribute values
	-  The leaf nodes specify what must be returned from the functions 
	- Boolean decision tree is equivalent to: $Output\leftrightarrow (Path_1 \lor Path_2 \lor ...)$
```JavaScript
function LEARN_DECISION_TREE(examples, attributes, parent_examples) returns a tree
	if examples is empty then return PLURALITY_VALUE(parent_examples)
	else if all examples have the same class then return the class
	else if attributes is empty then return PLURALITY_VALUE(examples)
	else 
		A = argmax(attributes(a)) IMPORTANCE(a, examples)
		tree = a new decision tree with root test A
		for each value v of A do 
		exs = {e: examples(e) and e.A = v}	
		subtree = LEARN_DECISION_TREE(exs,attributes(A), examples)
		add branch to tree with label (A = v) and subtree subtree
	return tree
```
- `PLURALITY_VALUE` selects the most common output value among a set of examples, breaking ties randomly 
- Finds the smallest tree consistent with the training examples by recursively choosing the most significant attribute as the root of tree or sub-tree 
 - Choosing attribute tests: 
	 - Entropy: The measure of uncertainty of a random variable 
		- The more information : The less entropy
		- Entropy of a random variable: 
			- Random variable $V$ with values $v_k$ having probability $P(v_k)$ 
			- $H(V) = \Sigma_k\space P(v_k) \space log_2 (\frac{1}{P(v_k)}) = - \Sigma_k\space P(v_k) \space log_2(P(v_k))$
			-  Fair coin: $H(Fair) = -(0.5 \space log_2(0.5) + 0.5 \space log_2(0.5)) = 1$
			- Fair 4 sided die: $H(Die4) = - 2*(0.25 \space log_2(0.25) + 0.25 \space log_2(0.25)) = 2$
		- Entropy of a random Boolean variable $B(q)$: 
			- $B(q) = -(q\space log_2( q + (1 - q)\space log_2(1 - q))$
		-  The entropy of an output variable on an entire data set is:  $H(Output) = B(\frac{p}{p+n})$
	- Our objective is to choose the attribute that will maximally reduce the uncertainty: 
		- That attribute will be used as the root node of the decision tree
		- We take an attribute $A$ with $d$ distinct values that divide the training set $E$ into subsets  $E_1, \space ... E_d$
		- Each of these $d$ subsets $E_k$ has some positive $p_k$ examples and some negative $n_k$ ones. 
		- So, for that specific branch, we would need: $B(p_k / (p_k + n_k))$ bits. 
		- A randomly chosen example from a training set  has the $Kth$ value for the attribute $E_k$ with the probability: $(p_k + n_k)/(p + n)$
		- $Remainder(A) = \Sigma_d^{k=1} \space \frac{p_k + n+k}{p+n} \space B(\frac{p+k}{p_k + n_k})$
		- The information gained from the attribute test on $A$ is the expected reduction in entropy: $Gain(A) = B(\frac{p}{p + n}) - \space Remainder(A)$
- Pruning: 
	- Decision tree pruning:
		- Eliminating irrelevant nodes 
		- Eliminating nodes that cause noise in the data set
		- Works by starting with a fully grown decision tree and iteratively removing branches that do not improve its accuracy on a validation data set
			- We stop once a stopping criterion is met 
# [[CHAPTER_4_AGENTS_AND_SEARCH_ALGORITHMS]]
- Problem solving agents: 
	- Agents that consider a sequence of actions that form a path leading them to a goal state 
	- Such agents are used when the correct action to take is not immediately available 
	- Searches are used
- In a fully observable, deterministic, know environment, the solution to any problem is a fixed sequence of actions 
- If the model is correct and the agent finds a solution, it can ignore its percepts while executing its action 
- This is called an open-loop system : Breakage of the loop between the agent and it's environment
- Search problems and their 6 properties: 
	- Has a state space: A set of possible  states the environment can be in 
	- Has an initial state the agent starts in
	- Has a set of one or more goal states: 
		- One goal state
		- A small set of alternative goal states
		- Goal defined by a property that applies to many states
	- Has actions available to the agent: 
		- From a state $s$, `ACTIONS(s)` returns a finite set of actions that can be executed.
	- Has a transition model: 
		- Describes what each action does, `RESULT(s,a)` returns the sate that results from doing action $a$ in state $s$
	- Has an action cost function, `ACTION_COST(s,a,s')` that gives the numeric cost of applying action $a$ in a state $s$ to reach state $s'$.
		- A problem solving agent should use a cost function that reflects its own performance measure
	- A sequence of actions form a path 
	- A solution is a path from the initial state to the goal state
	- Action costs are additive
	- Optimal solutions have the lowest path cost, this is referred to as being minimized
	- State spaces can be represented as graphs: 
		- Vertices are states 
		- Directed edges are actions
	- Eliminating useless details from representations is called abstraction 
- Problem types: 
	- Deterministic and fully observable implies a single state problem
		- Agents know which state they will be in, the solution is a sequence
	- Non-observable implies a conformant problem 
		- Agents may have no idea where they are, the solution is a sequence
	- Non-deterministic/Partially observable implies a contingency problem 
		- Precepts provide new information about the current state
		- Solution is a contingency plan or a policy 
		- Searching and execution are interleaved
	- Single state problems are defined by four items:
		- `INITIAL_STATE = state`
		- `SUCESSOR_FUNCTION( set of action_state pairs ) ` 
		- `GOAL_TEST`
		- `PATH_COST(Type)`
	- Selecting a state space: 
		- The space must be abstracted for problem solving requirements 
		- `(Abstract) State = set of real states`
		- `(Abstract) Action = complex combination of real actions `
		- `(Abstract) Solution = set of real paths that are solutions in the real world`
		- Abstractions should be easier than the real problems 
- Tree search algorithms: 
	- Takes a search problem as input and results a solution or an indication of failure
	- Search algorithms that superimpose a search tree over a state space graph which then form various paths out of the initial state in hopes of finding one that reaches a goal state
	- Each node in the tree corresponds to a state in the state space graph and the edges in the tree correspond to actions of the state space graph 
	- The root of the tree is the initial state of the problem 
	- Key distinctions between state space graphs and search trees:
		- State space graphs describe the set of states in the world and the actions that allow transitions from one state to another
		- Search trees describe paths between these states, extending and reaching towards the goal 
		- Search trees can have many paths for any given state, each node in the tree has a unique path back to the root, as in all trees
	- Basic Idea: Offline, simulated exploration of the state space graph done by generating successors of already explored states (expanding states)
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
- A frontier separates a state space graph into two sections: 
	- An interior section of explored and expanded states
	- An exterior section of states that have not yet been reached
# [[CHAPTER_5_TREE_SEARCH_AND_ALGORITHMS]]
- States vs nodes: 
	- States are representations of physical configurations
	- Nodes are data structures that make up part of a search tree, including:
		- Parents
		- Children
		- Depth
		- Path cost $g(x)$
	- States do not have parents, children, depth or a path cost
	- The `EXPAND` function creates new nodes and fills in their information and fields by using a callback sequence to the `SUCCESSOR` function of the problem. This then creates the new corresponding states for the newly created nodes
		```javascript 
function tree_search(problem, fringe) returns a solution or failure
	 fringe = insert(make_node(initial_state[problem]), fringe)
	 loop do 
		 if fringe.is_empty() then return failure
		 node = remove_front(fringe)
		 if goal_test(problem, state(node)) then return node
		 fringe = insert_all(expand(node, problem), fringe)
```
	```javascript 
function Expand(node, problem) returns a set of nodes
	successors = the empty set
	for each action, result in successor_function(problem, state[node]) do
		s = new node 
		parent_node[s] = node
		action[s] = action 
		state[s] = result 
		path_cose[s] = path_cost[node] + step_cost(node, action, s)
		depth[s] = depth[node] + 1
		successors.add(s)
	return successors
```
- Best first search: 
	- Used to choose which node to expand next from the frontier 
	- Works by picking the node with a minimum value given by some function $f(n)$
	- On each iteration, we chose a new node on the frontier with minimum $f(n)$, we return it if it's a goal state, otherwise we apply `EXPAND()` to generate more child nodes 
	- Each child node is added to the frontier if it hasn't been reached before, or, it's re-added if its now reached with a path cost less than what it was before. 
	- The algorithm returns either an indication of failure or a node that represents a path to a goal
- Search Data Structures: 
	- Require data structures with 4 components:
		- `node.state`: Corresponding state of the node
		- `node.parent`: Corresponding parent of the node
		- `node.action`: The action that was applied to the parent state to generate this node
		- `node.path_cost`: The total cost of the path from the initial state to this node
		 `g(node)` is used for the `path_cost`
	- If we follow the parent pointers back from a node, this allows us to recover the states and actions along the path to that node. Doing this from a goal state gives us the desired solution 
	- For a frontier we use a queue: 
		- `is_empty(frontier)`: Returns true if there are no nodes in the frontier
		- `pop(frontier)`: Pops the top node from the frontier and returns it 
		- `top(frontier)`: Returns the first node from the frontier
		- `add(node, frontier)`: Inserts a node into its proper place in the queue 
	- Three kinds of queues used in search algorithms: 
		- Priority queue: Pops the node with the minimum cost first according to some evaluation function. Used in Best-First Search 
		- FIFO queue: Regular queue, used in BFS
		- LIFO stack: Regular stack, used in DFS
	- All reached states can be stored in a lookup table where each key is a state and each value is the node for that state 
- Redundant paths: 
	- Redundant paths are paths with repeated states, often generated by cycles (loopy paths). 
	- Even though the state space might be finite, this would cause a complete search tree to be infinite due to there being no limit on how many times one can traverse a loop
	- Cycles are special cases of redundant paths
	- Removing redundant paths allows us to complete the search for an optimal path much faster 
	- There are 3 main ways to eliminating redundant paths: 
		- Remember all previously reached states:
			- Remembering all previously reached states is preferable when the table of reached states can fit in memory
		- Don't worry, it won't happen: 
			- In some problems, path redundancy is very rare or simply impossible
			- Graph-Search if it checks for redundant paths and Tree-like search if it doesn't
		- Compromise and only check for cycles but not redundant paths in general:
			- Checking for cycles using the chain of pointers that each node has costs no additional memory. 
			- This is done by following up the chain of parents to see if the state at the end of the path has appeared earlier in the path
			- Some implementations follow all the way up to eliminate all cycles, others follow only a few key links, taking a constant amount of time and eliminating all short cycles 
- Measuring problem-solving performance: 
	- Four main properties: 
		- Completeness: Is the algorithm guaranteed to find a solution when there is one and to correctly report failures when there isn't 
		- Cost optimality: Does it find a solution with the lowest path cost 
		- Time complexity: How long does it take to find a solution, measured in seconds or by the number of states and actions that have been considered
		- Space complexity: How much memory is required to perform the search
- Uniformed search strategies: 
	- A search algorithm has no clue about how close a state is to the goal 
	- There are 5 main strategies: 
		- Breadth-First Search: 
			- Complete: Yes, if $b$ is finite 
			- Space: $O(b^{d+1})$ - Keeps every node in memory.
			- Optimal: Yes, if cost = 1 per step, not optimal in general 
			- Time and space complexities are measured in terms of: 
				- $b$ = Maximum branching factor of the search tree.
				- $d$ = depth of the least cost solution.
				- $m$ = Maximum depth of the state space (may be $\infty$)
			- Mainly used when allocations all have the same cost, regular FIFO queues will be faster than PQ's and will also yield correct node ordering. Old nodes get expanded first and new nodes go to the back of the queue 
			- Reached can be a set of states rather than a mapping from states to nodes, we can also perform an early goal test to check whether a node is a solution as soon as it's generated rather than the late goal Best-First Search uses
			- Always finds a solution with a minimum number of actions, when it generates nodes at depth $d$, it has already generated all other nodes at depth $d -1$, so if a solution wasn't found at a depth other than $d$, this means that whatever solution is found, will be optimal. Optimal when all actions have the same cost, otherwise not. 
		- Uniform-Cost Search (Dijkstra's): 
			- Complete: yes, if step cost $\geq c$
			- Time: Number of nodes with $g \leq$ the cost of the optimal solution, $O(b^{fC^*/d})$ where $C^*$ is the cost of the optimal solution
			- Space: Number of nodes with $g \leq$ the cost of the optimal solution $O(b^{fC^*/d})$
			- Optimal: Yes, Nodes expand in increasing order of $g(n)$
			- Spreads out in waves of uniform-path cost whereas BFS spreads out in waves of uniform depth 
			- Can be implemented as a call to Best-First Search with `path_cost()` as the evaluation function
			- UCS is complete and cost-optimal because the first solution it finds will have a cost at least as low as the cost of any other node in the frontier. It considers all paths systematically in order of increasing cost and never gets caught going down a single infinite path 
		- Depth-First Search: 
			- Tree-like search that doesn't keep a table of reached states 
			- Not cost-optimal, returns the first solution it finds even if it isn't the cheapest 
			- Efficient and complete for finite spaces that are trees
			- In Acyclic state spaces, might expand the same state multiple times via different paths 
			- In Cyclic state spaces, might get stuck in an infinite loop, some implementations of DFS check each new node for cycles
			- In finite state spaces, DFS is not systematic, it can therefore get stuck going down an infinite path even if there are no cycles, thus DFS is incomplete. 
			- Why use DFS: 
				- We mainly use DFS when tree-search is feasible, it has a much smaller memory requirement 
				- A reached table is not necessary, the frontier is very small as well 
			- For a finite tree-shaped state space: 
				- DFS takes time proportional to the number of states: $O(b^m)$
				- Memory complexity of $O(bm)$
				- Where $b$ is the branching factor and $m$ is the maximum depth of the tree
			- Complete: 
				- No: Fails in infinite depth spaces, spaces with loops and needs to be modified to avoid repeated states along paths
				  Complete in finite spaces
			- Time: $O(b^m)$: This is terrible if $m$ is much larger than $b$, if solutions are dense it could be faster than BFS 
			- Space: $O(bm)$: Linear space
			- Optimal: No
		- Depth-Limited Search: 
			- Essentially the same as DFS but with a depth limit $l$
			- To keep DFS from wandering down infinite paths, we use DLS for which we specify a maximum depth the algorithm can explore to
			- Time complexity: $O(b^l)$
			- Space complexity: $O(bl)$
			- A poor choice for $l$ might prevent the algorithm for reaching the solution, thus making it incomplete once again 
			- If we only look a few links up the parent chain, we can catch most cycles at the cost of some computation time, longer cycles will be automatically handled by the depth limit
			- The specific number for the depth limit is known as the diameter of the state space graph 
		- Iterative-Deepening Search: 
			- Solves the problem of picking  a good value for $l$ by trying all possible values for $l$, that is, $l=1, l=2, l=3 ...$ This is done until either a solution is found or the DLS returns the failure value rather than the cutoff value 
			- IDS combines many of the benefits of DFS and DLS. Like DFS, it's memory requirements are models when there is a solution or for finite spaces with no solution. 
			- IDS is optimal for problems where all actions have the same cost and is complete on finite acyclic state spaces or on any finite space when we check nodes for cycles all the way up the path
				```javascript 
				function iterative_deepening_search(problem) return a solution 
					for depth = 0 to INT_MAX do 
						result = depth_limited_search(problem, depth)
						if result != cutoff then return result 
					end 
				```
			 - May seem wasteful due to first level nodes constantly being regenerated, however this doesn't matter much since most of the nodes in state spaces are towards the bottom
			 - Nodes on `depth(d)` are generated once, those one level higher are generated twice and so on, up the children until the root, which are generated $d$ times 
			 - The total number of nodes generated in the worst case is: 
				 - $N(IDS) = \space (d)b^1 + (d - 1)b^2 + (d - 2)b^3 ... + b^d \rightarrow O(b^d)$ 
				 - For example, if $b = 10$ and $d = 5$: 
				  $N(IDS) = 50 + 400 + 3000 + 20000 + 100000 = 123450 \space nodes$
				  $N(BFS) = 10 + 100 + 1000 + 10000 + 100000  = 111110 \space nodes$ 
			 - IDS is preferred when the search state space can't fit in memory and the depth of the solution is unknown 
			 - Complete: yes 
			 - Time: $(d+1)b^0 + db^1 + (d-1)b^2 + ... + b^d = O(b^d)$ : Exponential time.
			 - Space: $O(bd)$: Linear space
			 - Optimal: Yes, if the step cost = 1, it can also be modified to explore uniform-cost tree
		- Bi-directional search: 
			- Simultaneously searches forward from the initial state and backwards from the goal states 
			- Hoping that the two ends will meet, the motivation is that: $b^{\frac{d}{2}} + b^{\frac{d}{2}}$ is much smaller than $b^d$
			- Some conditions must be fulfilled for this to work: 
				- Must keep track of two frontiers
				- Must keep track of two tables of reached states
				- Backwards reasoning 
			- If state $s'$ is a successor of $s$ in the forward direction, we need to know that $s$ is a successor of $s'$ in the backwards direction as well 
![[USA_summary.PNG]]
