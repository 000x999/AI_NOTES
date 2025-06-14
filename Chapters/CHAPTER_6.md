# Neural Networks 
## The human brain 
![[neuron_img.PNG]]
- Neurons transmit messages or signals throughout the body's nervous system. 
- A neuron has three main parts: 
	- The dendrites:
		- The dendrites receive incoming signals from other neurons or sensory receptors. 
		  These signals can be in the form of electrical impulses amongst other ways. 
		- Once the dendrites receive these signals, they pass them onto the cell body. 
	- The cell body (The soma)
		- The cell body processes the signals received from the dendrites and decides whether to send a new signal or not. The body is like **a decision making center**. 
	- The axon
		- If the decision to send a signal is made, the signal travels along the axon, which is essentially like a long wire. 
	- These terminals communicate with the dendrites of other neurons through tiny gaps called synapses. 
	- This process repeats, allowing the  signal to pass from one neuron to the next, creating an extensive chain of communication throughout the entire nervous system. 
	- Neurons work together to transmit information which then allows our bodies to move our muscles, perceive our environment, think and perform various bodily actions and functions. 
- The brain has roughly **86 Billion** neurons. 
- Each neuron is connected to thousands of other neurons. 
- The connections are neither fixed nor static, the brain's neural network is continuously changing and being actively rewired throughout our life based on our experiences, learning and development. 
- **NOTE:** Despite the wonders neural networks can achieve, there is absolutely no comparison between the world's most sophisticated computerized neural network and the human brain. 
## Deep learning
##### What is Deep learning
- Deep learning is a broad family of techniques for machine learning in which **hypotheses** take the form of  complex algebraic circuits with tunable connection strengths. 
- The word **"deep"** defers to the fact that the circuits are typically organized into many **layers**, which means that computation paths from inputs to outputs have many steps. 
- Deep learning is currently the most widely used approach for applications such as visual object recognition, machine translation, speech recognition, speech synthesis and image synthesis.
##### Concept of Deep learning 
- The basic idea of deep learning is to train circuits such that the computation paths are long, allowing all the input variables to interact in complex ways. 
- These circuit models turn out to be sufficiently expressive and are able to capture the complexity of real-world data for many important kinds of learning problems. 
### Simple Feedforward Networks 
![[ff_net.PNG]]
- A **Feedforward Network** has connections only in one direction, it forms a **directed acyclic graph** with designated input and output nodes, much like a **Bipartite graph**. 
- Each node computes a function of its inputs and passes the result to its successors in the network. 
- Information flows through the network from the input nodes to the output nodes, there are no loops. 
- A **Recurrent Network or RNN** feeds its intermediate/final inputs back into its own inputs.
#### Feedforward operation and Classification 
- A three layer neural network consists of an input layer, a hidden layer and an output layer. All layers are interconnected by modifiable weights represented by links between layers. 
![[ff3_netg.PNG]]
- $\sigma(20x_1 + 20x_2 - 10)$     represents the value passed to $h_1$ using the first bias value $b = -10$.
- $\sigma(-20x_1 - 20x_2 + 30)$ represents the value passed to $h_2$ using the second bias value $b = 30$. 
- $\sigma(20h_1 + 20h_2 -30)$    represents the final singular output value passed to node $y$ from nodes $h_1$ and $h_2$.
#### Networks as Complex Functions 
- Each node in a network is called a unit. 
- A unit calculates **the weighted sum of the inputs** from predecessor nodes and then applies a nonlinear function to produce its output. 
- $a_j = g_j ( \Sigma_i w_i, a_{i,j}) = g_j (in_j))$ 
  Where, $a_j$ is the output of unit $j$ and $w_{i,j}$ be the weight attached to the link from unit $i$ to unit $j$.
  Where $g_j$ is a nonlinear **activation function** associated with unit $j$ and $in_j$  is the **weighted sum** of the inputs to unit $j$. 
- The fact that the **activation function** is nonlinear is very important. If it were not, any composition of units would still represent a linear function. 
- The nonlinearity is what allows sufficiently large networks of units to represent **any arbitrary functions**. 
- **The universal approximation** theorem states: A network with just two layers of computational units, the first nonlinear and the second linear, can approximate any continuous function to an arbitrary degree of accuracy. 
- The proof works by showing that an exponentially large network can represent exponentially many **"bumps"** of different heights at a different locations in the input space, therefore approximating the desired function. 
- **Sufficiently large networks** can essentially implement a lookup table for continuous functions, just as sufficiently large decision trees implement a lookup table for Boolean functions. 
#### Activation functions 
- Logistic or Sigmoid function: 
	- $\sigma(x) = 1 / (1 + e^{-x})$
- Rectified Linear Unit (ReLU) function: 
	- $ReLU(x) = max(0,x)$
- Softplus function (Smooth version of ReLU): 
	- The derivative of the Softplus function is the Sigmoid function
	- $softplus(x) = \log(1+e^x)$
- Tanh function: 
	- $tanh(x) = \frac{e^{2x} - 1}{e^{2x} + 1}$
	- The range of tanh is (-1, 1). Tanh is a scaled and shifted version of the sigmoid function
	  $tanh(x) = 2\sigma(2x) - 1$
#### Gradients and learning 
- Using the squared loss function, $L_2$
- Predictions, $\hat{y} = h_w(x)$ 
- $Loss(h_w) = L_2(y, h_w(x)) = ||y - h_w(x)||^2 = (y - \hat{y})^2$
- **Back-Propagation:** Is the way that the error at the outputs is passed backwards through the network. 
### Computation Graphs for Deep learning
#### Input encoding 
- Input and output nodes of a computational graph are the ones that connect directly to the input data $x$ and the output data $y$. 
- False is mapped to an input of 0 and true is mapped to an input of 1, or (-1 and 1). 
- Numeric attributes are used as is. 
- Categorical attributes with more than two values are encoded with one-hot encoding, that is: 
	- An attribute with $d$ possible values is represented by $d$ separate input bits. 
	- Corresponding input bits are set to 1 and the others 0. 
#### Hidden layers 
- Intermediate computations before producing the output $y$. 
- Different representations for the input $x$. 
- Each layer transforms the representation produced by the preceding layer to produce a newer representation. 
- In the process of forming all these internal transformations, deep networks often discover meaningful intermediate representations of the data. 
- The hidden layers of neural networks are typically less diverse than the output layers. 
### Convolutional Networks 
- Convolutional neural network (CNN) is a type of neural network that helps computers understand images. 
- A CNN looks at an image in small pieces and finds patterns like edges, shapes and colors and uses them to recognize what's in the image. 
- The more training it gets with various types of images, the better it gets at recognizing new ones. 
#### Tensor operations in CNNs
- Tensors are multi-dimensional data structures. 
	- Tensors are assigned "Ranks", a rank 0 Tensor is simply a scalar value e.g. 7. 
	- A rank 1 Tensor is a vector of certain data type e.g. [ 1,2,3,4,5] 
	- A rank 2 Tensor is a matrix e.g. a 4x4 matrix of a certain data type
	- A rank 3 Tensor is a layering of nested data types e.g. a matrix of matrices or vectors etc. 
	- More dimensions can represent things like batches of images, video frames or time steps, all of those are higher dimensional tensors.  
	- Tensors are usually ran on the GPU or TPUs which make use of their higher capabilities for parallelism. 
- Input images are stored as Tensors (Usually 3D tensors: Height x Width X Color channels)
- All the calculations and pattern-finding done by the CNNs happen on Tensors. 
- The CNN keeps transforming the tensors, detecting patters, compressing the data and learning features until it reaches a final output. 
#### Learning algorithms 
##### Backpropagation 
1.  **Make a guess (Forward pass):** The network takes some input and makes a prediction. 
2. **Check the mistake (loss):** The network then compares the prediction to the correct answer, if it's wrong, it calculates how wrong it was (Cost function), this is called the **loss**. 
3. **Blame the layers (backward pass):** Backpropagation then works backwards through the network to figure out which parts (neurons and weights) were the most responsible for the mistake. 
4. **Fix the weights (update step):** The network will then adjust the weights to make a better prediction next time. 
5. This is done using a method called **gradient descent**. 
##### Computing gradients in computation graphs 
- Drawbacks of backpropagation: Backpropagation requires storing most of the intermediate values that were computed during the forward propagation process in order to calculate the gradients in the backwards pass.
### Generalization
#### Choosing a network architecture 
- Some neural network architectures are explicitly designed to generalize well on particular types of data. 
- When comparing two networks with a similar number of weights, the deeper networks usually yield better generalization performance. 
- Deep learning systems perform better than any other pure machine learning approaches for high dimensional inputs (images, video, speech, signals, etc.)
- Deep learning models lack the **compositional** and **quantificational** expressive power, that is: 
	- They struggle to build structured meanings from parts (compositionality)
	- They lack the ability to reason using rules about quantity or logic (quantification)
- This is why some researchers combine deep learning with symbolic logic to try and get the pattern recognition strength of neural networks and the symbolic rule-based reasoning of AI. 
   ![[generalization.PNG]]