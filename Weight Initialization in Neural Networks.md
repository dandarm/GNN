https://towardsdatascience.com/weight-initialization-in-neural-networks-a-journey-from-the-basics-to-kaiming-954fb9b47c79


pesi troppo grandi
![[Pasted image 20221010011536.png]]

pesi troppo piccoli
![[Pasted image 20221010011515.png]]


 the matrix product of our inputs **x** and weight matrix **a** that we initialized from a standard normal distribution will, on average, have a standard deviation very close to the square root of the number of input connections, which in our example is √512.
![[Pasted image 20221010011705.png]]


## Xavier Initialization

![[Pasted image 20221010011908.png]]

When Xavier Glorot and Yoshua Bengio published their landmark paper titled [_Understanding the difficulty of training deep feedforward neural networks_](http://proceedings.mlr.press/v9/glorot10a/glorot10a.pdf), the “commonly used heuristic” to which they compared their experiments was that of initializing weights from a _uniform_ distribution in [-1,1] and then scaling by 1/√_n_.


Xavier initialization sets a layer’s weights to values chosen from a random uniform distribution that’s bounded between![[Pasted image 20221010011951.png]]

where _nᵢ_ is the number of incoming network connections, or “fan-in,” to the layer, and _nᵢ₊₁_ is the number of outgoing network connections from that layer, also known as the “fan-out.”

--------------------
**Xavier Initialization**, or **Glorot Initialization**, is an initialization scheme for neural networks. Biases are initialized be 0 and the weights Wij at each layer are initialized as:

$Wij∼U[-\frac{1}{\sqrt{n}},\frac{1}{\sqrt{n}}]$ 

Where U is a uniform distribution and n is the size of the previous layer (number of columns in W).

--------------------



## Kaiming Initialization
what if we’re using ReLU activation functions? Would it still make sense to want to scale random initial weight values in the same way?
It turns out that when using a ReLU activation, a single layer will, on average have standard deviation that’s very close to the square root of the number of input connections, _divided by the square root of two_, or √512/√2 in our example.


As we showed before, keeping the standard deviation of layers’ activations around 1 will allow us to stack several more layers in a deep neural network without gradients exploding or vanishing.

1.  Create a tensor with the dimensions appropriate for a weight matrix at a given layer, and populate it with numbers randomly chosen from a standard normal distribution.
2.  Multiply each randomly chosen number by _√_2/_√n_ where _n_ is the number of incoming connections coming into a given layer from the previous layer’s output (also known as the “fan-in”).
3.  Bias tensors are initialized to zero.

When using Xavier to initialize weights, activation outputs have almost completely vanished by the 100th layer!



![[Schermata da 2022-10-10 02-27-45.png]]


### pytorch

https://adityassrana.github.io/blog/theory/2020/08/26/Weight-Init.html#Okay,-now-why-can't-we-trust-PyTorch-to-initialize-our-weights-for-us-by-default?

If you cut some of its layers and replace it with your own layers, you need to initialize them again as per recommended methods which is kaiming normal if you're working with ReLU function.

_conv = nn.Conv2d(ni, nf, kernel_size=ks,stride=stride,padding=padding, \*\*kwargs)
nn.init.kaiming_normal_(_conv.weight)

