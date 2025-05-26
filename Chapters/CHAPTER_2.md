# Agents and environment 
- Some more useful information on agents can be found in **[[CHAPTER_1#Rational agents]]**
- Agents include humans, robots, softbots, thermostats, etc. Agents aren't only used in the context of AI, agents can be anything that can be viewed as perceiving it's environment. Spatial perception can be done through sensors and acting upon it's surroundings and environment through actuators. 
- More formally, agent definitions include:  
  - Humans, Robots, Softbots, Thermostats, etc.
  - Perceives its environment through sensors or any other mechanical medium. 
- Interacts with its environment through actuators or any other mechanical medium. - The agent function maps from percept histories to actions:  $f: P^* \rightarrow A$
  - The agent program runs directly on physical devices/architectures to produce $f$
# Rationality 
- Some more useful information on **Rationality and Rational thought** can be found in **[[CHAPTER_1#Thinking rationally Laws of Thought]]** 
- Rational agents are ones that do the **right thing**, but what does it mean to do the right thing? Can doing the **right thing** be quantified or made into a set of rules?
- An easier approach to getting agents that act rationally is through evaluating their behaviors based on their set consequences. This brings us to the notion of **desirability**. Desirability can be captured by a performance measure that evaluates any given environmental sequence. 
## Performance measure example: 
- Let's consider the vacuum cleaner example. How do we quantify and measure the agents performance in this scenario? 
- Fixed performance measures evaluate the environment sequences: 
  - The agent is awarded one per square cleaned in time $T \space \rightarrow$ dump and clean. But what happens when both squares in its vicinity are clean?  
  - The agent is awarded one point per clean square per time step, minus one per move, the agent then checks occasionally and cleans if needed. 
  - The agent is penalized for $\space > \space k \space$ dirty squares. 
  - A rational agent will choose whichever action will **maximize** the **expected** value of its overall performance measure **based off of the given percept sequence**. 
- More formally, Rationality depends on four factors: 
  - The performance measure that defines the criteria of success. 
  - The agents prior knowledge of the environment. 
  - The set of actions that the agent is able to perform. 
  - The agents percept sequence to date. 
# PEAS
- The design of rational agents depend on the specified task environment. 
- Each task environment must have clear definitions and specifications. The agents performance in the task environment must be measurable and quantifiable. The environment must be clearly defined and the set of mechanical mediums the agent will use to perceive and interact with its environment must also be clearly defined. 
- More formally, the task environments qualities are defined as follows: 
  - Performance measure.
  - Environment.
  - Actuators.
  - Sensors.
- Consider the example of an automated taxi: 
  - Performance measure: Safety, destinations, profits, legality, comfort, etc. 
  - Environment: Canada/US, streets/freeways, traffic, pedestrians, weather, etc. 
  - Actuators: Steering, accelerator, brake, horn, speakers/display, etc. 
  - Sensors: Video, accelerometers, gauges, engine sensors, keyboard, GPS, etc.
- Consider the example of an Internet shopping agent: 
  - Performance measure: Price, quality, appropriateness, efficiency. etc. 
  - Environment: Current and future WWW sites, vendors, shippers, etc. 
  - Actuators: Display to user, follow URL, fill in form, etc. 
  - Sensors: Video, HTML pages (text, graphics, scripts), etc.
# Environment types 
- There are 17 main environment types: 
  - Fully observable, partially observable, unobservable. 
  - Single-agent, multi-agent. 
  - Deterministic, non-deterministic. 
  - Determinism, stochastic-ism. 
  - Episodic, sequential.
  - Static, dynamic. 
  - Discrete, continuous. 
  - Known, unknown.  
### Fully observable, partially observable, un-observable:
- If the agents sensors continuously provide it access to the **complete state** of the environment, then the task environment is considered fully observable. 
- Conversely, a task environment can be considered partially observable due to noisy or inaccurate reading from the agents sensors or simply because of missing states from the sensor data. 
- If an agent has no sensors the environment is considered to be unobservable. 
### Single-agent, Multi-agent: 
- Example task environments for single and multi-agent environments:
  - A vacuum is a single agent environment
  - Chess is a **competitive multi-agent** environment.
  - A Self-Driving taxi is a multi-agent environment with many agents on the road. The agents are both **partially cooperative** since they actively avoid colliding into each other and **partially competitive** since they compete for the same clients, parking spots, etc. 
### Deterministic, Nondeterministic: 
- A simple explanation of deterministic vs nondeterministic environments is if the next possible state of the environment is determined solely by the current state and any action executed by an agent, then the environment is deterministic, otherwise its nondeterministic. 
### Determinism, Stochastic-ism: 
- Stochastic is largely considered to be a synonym of nondeterminism, however there is a slight distinction between the two terms. A model task environment is said to be **stochastic** if it explicitly deals with probabilities. Nondeterministic is the set of possibilities without room to being quantified. 
### Episodic, Sequential: 
- In an episodic task environment, any agents experience is sub-divided into atomic episodes. In each episode, agents receive a percept and then perform singular actions. 
- The next episode does not depend on the actions taken in previous episodes. An example of this is an agent that has to spot defective parts on an assembly line. 
- In sequential environments, an agents current decision could affect all future decisions. Examples of such situation are but not limited to: Chess, Self-riving taxis 
### Static, Dynamic: 
- If the environment is subject to change or being altered whilst an agent is deliberating, the environment is said to be dynamic, otherwise it is static. However, if the environment itself **Does not** change with the passage of time but the agents performance score does, the environment is said to be **semi-dynamic**. 
### Discrete, Continuous: 
- Discrete and continuous distinctions apply to: 
  - The state of the environment. 
  - The way the passage of time is handled. 
  - The percepts and actions of the agents.
- Ex: Chess has a finite number of distinct states, it also has a discrete set of percepts and actions. 
### Known, Unknown: 
- This environment typeset strictly refers to the **agent's state of knowledge** about the laws of the environment and not about the environment itself. If an environment is unknown to the agent, it will have to learn how it works to be able and eventually make consistently good decisions. Some examples of such situations are: 
	-  A card game where some cards have not yet been turned over $\rightarrow$ This would be a known environment that is partially observable. 
	- A video game is fully observable since we can see the whole screen, however it's an unknown environment until all the game controls have been discovered and memorized.
- The performance measures may themselves be unknown due to several factors such as: 
  - The designer is not sure how to write it down correctly. 
  - The user preferences are not yet known. 
  - Ex: A taxi driver cannot know in advance whether their next passenger will prefer a leisurely or speedy journey, cautious or aggressive driving styles, etc.
- This means that the agent must learn the performance measure itself. 
#### Example environments and their types:

|               | Solitatire | Backgammon | Internet Shopping     | Taxi |
| ------------- | ---------- | ---------- | --------------------- | ---- |
| Observable    | Yes        | Yes        | No                    | No   |
| Deterministic | Yes        | No         | Partly                | No   |
| Episodic      | No         | No         | No                    | No   |
| Static        | Yes        | Semi       | Semi                  | No   |
| Discrete      | Yes        | Yes        | Yes                   | No   |
| Single-Agent  | Yes        | No         | Yes (except auctions) | No   |
- The environment type is largely what determines the agent's overall design. 
- **The real world is partially observable, stochastic, sequential, dynamic, continuous and multi-agent.**

# Agentic architecture and types 
- Refer to [[#Agents and environment]] for more info agents.
- An agent's construction is called the **agent architecture**: $agent \space =  \space architecture \space + \space program$
## Agent types 
- There are four basic types in **order of increasing generality**:
  - Simple reflex agents. 
  - Model-Based reflex agents (With state). 
  - Goal-Based agents. 
  - Utility-Based agents (To make customers happy).
- All of these agent types can be turned into learning agents. 
### Simple reflex agents: 
![[simple_reflex_agent_diagram.png]]
```bash
function Reflex-Vacuum-Agent([location, status]) returns an action
	if status = Dirty then Suck
	else if location = A then return Right
	else if location = B then return Left
```
```clojure
(defun make-reflex-vacuum-agent-program()
	#'(lambda (percept)
		(let (location (first percept)) (status (second percept)))
		(cond ((eq status 'dirty) 'Suck)
			  ((eq location 'A) 'Right)
			  ((eq location 'B) 'Left)))))
```
- One of the best and most effective ways to handle partial observability is for the agent to keep track of the part it is unable to currently see. The agent should also maintain some sort of internal state that largely depends on the percept history and reflects some unobserved aspects of the current state. Ex: When it rains $\rightarrow$ objects look like water drops.
![[reflex_agents_with_state.png]]
### Goal-Based agents: 
![[goal_based_agents.png]]
### Utility-Based agents: 
![[util_based_agents.png]]
### Learning agents: 
![[learning_agents.png]]
