# Chapter 1: Introduction — Handwritten Digit Recognition

1. THE PROBLEM: RECOGNIZING HANDWRITTEN DIGITS

Recognizing handwritten digits is a task that comes effortlessly
to human brains but is extremely difficult to program explicitly.

A digit image may be sloppily written and rendered at an extremely
low resolution, such as 28x28 pixels, yet a human brain still
recognizes it effortlessly.

The same digit can look different from one example to the next:

- Different pixels are illuminated
- Different strokes and line styles
- Different orientations and sizes
- Different handwriting styles

Despite these differences, all images of the same digit share
recognizable characteristics.

EXAMPLE:

A handwritten "1" might contain:
- A dominant vertical line
- Few or no crossing lines
- No circular shapes

But pixel values vary widely between different images of "1".

2. WHY EXPLICIT PROGRAMMING FAILS

Writing a program that takes a 28x28 pixel grid as input and
outputs a single digit from 0 through 9 is dauntingly difficult.

- The specific pixel values vary too much between images
- There is no simple rule that covers every variation
- Manually defining every useful feature is impractical

The challenge is that a computer sees individual pixel values
rather than an understanding of visual characteristics like
lines, loops, or edges.

# Chapter 2: Series Preview — What is a Neural Network?

1. PURPOSE OF THE SERIES

This series introduces neural networks assuming no background,
visualizing them not as a buzzword but as a piece of math.

The goal is to understand:

- The structure of a neural network
- What it means when we hear about a network "learning"

This video focuses on structure. The following video tackles
learning.

2. THE TASK: HANDWRITTEN DIGIT RECOGNITION

We will build a neural network that can learn to recognize
handwritten digits.

This is a classic example for introducing neural networks.
At the end of the two videos, resources will be provided for
further learning and for downloading code to experiment with
on your own computer.

3. PLAIN VANILLA NEURAL NETWORKS

There are many variants of neural networks. Recent years have
seen a boom in research toward more powerful variants.

In these two introductory videos, we focus on the simplest,
plain vanilla form with no added frills.

This simplest form is:

- A necessary prerequisite for understanding modern variants
- Still complex enough to wrap our minds around
- Capable of learning to recognize handwritten digits
- Not perfect; it falls short of some hopes we might have

4. INSPIRATION FROM THE BRAIN

Neural networks are inspired by the brain, but they are a
mathematical abstraction, not a biological simulation.

# Chapter 3: What Are Neurons?

1. DEFINITION OF A NEURON

A neuron is simply a thing that holds a number.

Specifically, a neuron holds a number between 0 and 1.

This number is called the neuron's activation.

2. INPUT LAYER NEURONS

The network starts with neurons corresponding to each of the
28x28 pixels of the input image.

Total input neurons:

```
28 x 28 = 784 neurons

```
Each input neuron holds a number representing the grayscale value
of the corresponding pixel:

- 0 = black pixel
- 1 = white pixel
- Values between 0 and 1 = shades of gray

3. ACTIVATION

The activation of a neuron is the number it holds.

Image to keep in mind: each neuron is "lit up" when its
activation is a high number (close to 1).

# Chapter 4: Introducing Layers

1. INPUT LAYER

All 784 pixel neurons make up the first layer of the network,
called the input layer.

2. OUTPUT LAYER

The last layer has 10 neurons, each representing one digit
from 0 through 9.

The activation of each output neuron, a number between 0 and 1,
represents how much the system thinks the image corresponds
with that digit.

3. HIDDEN LAYERS

Between the input and output layers are hidden layers.

In this example network:

- Two hidden layers
- 16 neurons in each hidden layer

The choice of two layers and 16 neurons per layer is somewhat
arbitrary:

- Two layers chosen to motivate the structure being explained
- 16 chosen because it was a nice number to fit on screen

In practice, there is a lot of room to experiment with the
specific structure.

4. HOW LAYERS INTERACT

Activations in one layer determine the activations of the next layer.

The heart of the network as an information-processing mechanism
is exactly how activations from one layer bring about activations
in the next layer.

This is loosely analogous to biological networks of neurons,
where some groups of neurons firing cause certain others to fire.

5. NETWORK OPERATION

If you feed in an image:

1. Light up all 784 neurons of the input layer according to
   each pixel's brightness.

2. That pattern of activations causes a specific pattern in
   the next layer.

3. That pattern causes another pattern in the next layer.

4. This continues until the output layer is reached.

5. The brightest neuron in the output layer is the network's
   choice for what digit the image represents.

The network shown has already been trained to recognize digits.

# Chapter 5: Why Layers?

1. WHY A LAYERED STRUCTURE?

Before diving into the math, it is reasonable to ask why we
should expect a layered structure to behave intelligently.

When humans recognize digits, we piece together components:

- A 9 has a loop up top and a line on the right.
- An 8 has a loop up top and another loop down low.
- A 4 breaks down into three specific lines.

2. IDEALIZED GOAL FOR HIDDEN LAYERS

In a perfect world, each neuron in the second-to-last layer
would correspond to one subcomponent.

For example, any image with a loop up top (like a 9 or an 8)
would cause some specific neuron to have activation close to 1.

The hope is that this neuron responds to any generally loopy
pattern toward the top, not just one specific loop of pixels.

Going from earlier layers to the last layer would then require
learning which combination of subcomponents corresponds to
which digits.

3. KICKING THE PROBLEM DOWN THE ROAD

This just kicks the problem down the road:

- How do you recognize these subcomponents?
- How do you learn what the right subcomponents should be?

These questions are not fully answered yet, but the layered
structure provides a framework.

4. HIERARCHICAL DECOMPOSITION

Recognizing a loop can itself break down into subproblems:

Level 1: Recognize the little edges that make up the loop.
Level 2: Combine edges into loops and lines.
Level 3: Combine loops and lines into digits.

EXAMPLE:

A long line (like in digits 1, 4, or 7) is really just a long edge,
or a pattern of several smaller edges.

Hope for the network:

- Neurons in the second layer correspond to relevant little edges.
- An image lights up neurons associated with 8 to 10 specific edges.
- Those light up neurons for an upper loop and a long vertical line.
- Those light up the neuron for digit 9.

Whether the final network actually does this is another question,
to be revisited after learning how to train the network.

5. BEYOND IMAGE RECOGNITION

Layered abstraction is useful beyond image recognition:

- Parsing speech: raw audio -> distinct sounds -> syllables ->
  words -> phrases -> abstract thoughts

The goal of any layer is to have a mechanism that can combine
pixels into edges, edges into patterns, and patterns into digits.

# Chapter 6: Edge Detection Example

1. THE GOAL

Suppose we want one neuron in the second layer to detect whether
an image has an edge in a specific region.

The question is: what parameters should the network have?

2. WEIGHTS

We assign a weight to each connection between our neuron and the
neurons from the first layer. Weights are just numbers.

We compute a weighted sum of all first-layer activations according
to these weights.

Weights can be visualized as a grid:

- Green pixels = positive weights
- Red pixels = negative weights
- Brightness = loose depiction of the weight's value

3. FOCUSING ON A REGION

If weights for almost all pixels are zero, except for positive
weights in the region we care about, then the weighted sum amounts
to adding up values only in that region.

To pick up on an edge:

- Positive weights on the middle pixels of the region
- Negative weights on surrounding pixels

The sum is largest when middle pixels are bright and surrounding
pixels are darker.

4. SQUISHING WITH THE SIGMOID FUNCTION

A weighted sum can produce any real number, but we want activations
between 0 and 1.

We pump the weighted sum through a function that squishes the
real number line into the range between 0 and 1.

The sigmoid function (logistic curve) does this:

```
Very negative inputs -> close to 0
Positive inputs -> close to 1
Steadily increases around input 0

```
The neuron's activation is basically a measure of how positive
the weighted sum is.

5. BIAS

Maybe we only want the neuron to be active when the sum exceeds
a threshold, such as 10.

We add a number (e.g., -10) to the weighted sum before applying
the sigmoid.

This additional number is called the bias.

- Weights tell you what pixel pattern the neuron picks up on.
- Bias tells you how high the weighted sum must be before the
  neuron becomes meaningfully active.

# Chapter 7: Counting Weights and Biases

1. CONNECTIONS PER NEURON

Every neuron in a layer connects to all neurons from the previous
layer. Each connection has its own weight.

Each neuron also has its own bias.

2. COUNTING FOR ONE HIDDEN LAYER

Hidden layer with 16 neurons, each connected to all 784 input
neurons:

```
784 x 16 weights
+ 16 biases

```
That is just the connections from the first layer to the second.

3. TOTAL PARAMETERS

Connections between all layers have weights and biases.

All said and done, this network has almost exactly 13,000 total
weights and biases.

13,000 knobs and dials that can be tweaked to make the network
behave in different ways.

# Chapter 8: How Learning Relates

1. WHAT LEARNING MEANS

When we talk about learning, we mean getting the computer to find
a valid setting for all of these many numbers so that it actually
solves the problem at hand.

2. THOUGHT EXPERIMENT: HAND-SETTING WEIGHTS

Imagine sitting down and setting all weights and biases by hand,
purposefully tweaking numbers so that:

- The second layer picks up on edges.
- The third layer picks up on patterns.

This is satisfying rather than treating the network as a total
black box.

3. WHY UNDERSTANDING WEIGHTS MATTERS

When the network does not perform as anticipated:

- If you understand what weights and biases mean, you have a
  starting place for experimenting with structural changes.

When the network works but not for expected reasons:

- Digging into what weights and biases are doing challenges
  assumptions and exposes the full space of possible solutions.

# Chapter 9: Notation and Linear Algebra

1. THE NEED FOR COMPACT NOTATION

The actual function for computing activations is cumbersome to
write down. A more notationally compact representation is useful.

2. VECTORS AND MATRICES

Organize all activations from one layer into a column as a vector.

Organize all weights as a matrix, where each row corresponds to
connections between one layer and a particular neuron in the next
layer.

Taking the weighted sum of activations according to weights
corresponds to one term in a matrix-vector product.

3. LINEAR ALGEBRA IN MACHINE LEARNING

Much of machine learning comes down to having a good grasp of
linear algebra.

For visual understanding of matrices and matrix-vector
multiplication, see the linear algebra series (especially chapter 3).

4. BIAS IN VECTOR FORM

Instead of adding bias to each value independently, organize all
biases into a vector and add the entire vector to the matrix-vector
product.

5. FINAL COMPACT EXPRESSION

Wrap a sigmoid around the outside to apply the sigmoid function to
each component of the resulting vector.

Once written as symbols (weight matrix, activation vector, bias
vector), the full transition from one layer to the next becomes an
extremely tight expression.

This makes code simpler and faster because many libraries optimize
matrix multiplication.

# Chapter 10: Recap

1. NEURONS AS FUNCTIONS

Earlier, neurons were described as things that hold numbers.

More accurately, each neuron is a function:

- Takes in the outputs of all neurons in the previous layer.
- Spits out a number between 0 and 1.

2. THE ENTIRE NETWORK AS A FUNCTION

The entire network is just a function:

- Takes in 784 numbers as input.
- Spits out 10 numbers as output.

It is an absurdly complicated function involving:

- 13,000 parameters (weights and biases)
- Iterating many matrix-vector products
- The sigmoid squishification function

3. WHY COMPLEXITY IS REASSURING

If the function were any simpler, what hope would we have that it
could take on the challenge of recognizing digits?

4. THE LEARNING QUESTION

How does the network learn appropriate weights and biases just by
looking at data?

This is covered in the next video.

# Chapter 11: Some Final Words

1. SUBSCRIPTION

A reminder to subscribe to stay notified about new videos.

2. PATREON SUPPORT

Thank you to everyone supporting these videos on Patreon.

3. PROBABILITY SERIES

Progress on the probability series has been slow this summer but
will resume after this project. Patrons can look out for updates.

# Chapter 12: RELU vs Sigmoid

1. SIGMOID

Early networks used sigmoid to squish the weighted sum into the
interval between 0 and 1, motivated by the biological analogy of
neurons being inactive or active.

Sigmoid is considered old school.

2. RELU

Relatively few modern networks use sigmoid anymore.

ReLU (Rectified Linear Unit) is much easier to train.

ReLU takes the max of zero and a value (the weighted sum):

```
max(0, value)

```
Partially motivated by biological analogy:

- If activation passes a threshold -> identity function
- If not -> zero (not activated)

It is a simplification of sigmoid.

3. WHY RELU WORKED

Sigmoids did not help training and were difficult to train at
some point. People tried ReLU, and it happened to work very well
for incredibly deep neural networks.

# Final Review: Key Concepts

Algorithm / Component    Purpose
Neuron                   Holds a number between 0 and 1 (its activation)
Input Layer              784 neurons, one per 28x28 pixel
Output Layer             10 neurons, one per digit 0-9
Hidden Layers            Intermediate layers; learn intermediate representations
Weight                   Number on each connection between neurons
Bias                     Number added to weighted sum before sigmoid
Sigmoid                  Squishes any real number into [0, 1]
ReLU                     max(0, value); easier to train than sigmoid
Weight Matrix            Compact representation of all weights
Activation Vector        Column vector of all activations in a layer
Bias Vector              Vector of all biases added to matrix product

# Important Concepts to Remember

1. Neuron: A unit that holds a number between 0 and 1, called its activation.

2. Activation: The number held by a neuron; high activation means "lit up."

3. Input Layer: 784 neurons corresponding to 28x28 pixel grayscale values.

4. Output Layer: 10 neurons, each representing one digit from 0 through 9.

5. Hidden Layer: A layer between input and output that learns intermediate
   representations.

6. Weight: A number on each connection between neurons, used in weighted sums.

7. Bias: A number added to the weighted sum before applying the activation
   function; controls the threshold for activation.

8. Sigmoid Function: Squishes any real number into the range [0, 1].

9. Weighted Sum: Sum of input activations multiplied by their corresponding
   weights.

10. Layered Structure: Activations in one layer determine activations in the
    next, enabling hierarchical feature detection (edges -> patterns -> digits).

11. ReLU: Rectified Linear Unit; max(0, value); easier to train than sigmoid.

12. Linear Algebra Notation: Weights as matrix, activations and biases as
    vectors; enables compact expression of layer transitions.

13. Parameters: A network with 784-16-16-10 structure has approximately
    13,000 weights and biases.

14. Learning: The process of finding valid settings for all weights and biases
    so the network solves the problem.

15. Function View: The entire network is a function mapping 784 inputs to
    10 outputs.

# The Big Picture

```
                NEURAL NETWORK
                       |
         +-------------+-------------+
         |                           |
   INPUT LAYER                 OUTPUT LAYER
784 neurons (pixels)        10 neurons (digits 0-9)
         |                           |
         v                           v
+--------+--------+           brightest neuron = prediction
|                 |
```
HIDDEN LAYER 1    HIDDEN LAYER 2
16 neurons         16 neurons
Edges, patterns    Combinations of patterns
             |                           |
             +-------------+-------------+
                           |
                  WEIGHTS + BIASES + SIGMOID
                           |
                 13,000 parameters total
                           |
                    LAYER-TO-LAYER TRANSITION

The central idea:

A neural network is a function that transforms 784 pixel values
into 10 digit probabilities through layers of interconnected
neurons, each computing a weighted sum plus bias passed through
an activation function.
