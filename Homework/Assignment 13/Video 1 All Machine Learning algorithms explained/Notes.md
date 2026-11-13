# Chapter 1: Introduction — What is Machine Learning?

1. WHAT IS MACHINE LEARNING?

Machine Learning (ML) is a subfield of Artificial Intelligence (AI)
that focuses on developing algorithms that learn patterns from data.

Definition:
Machine learning is the study of statistical algorithms that can
learn from data and generalize to unseen data, allowing computers
to perform tasks without being explicitly programmed for every task.

Key concepts:
- Data: Information used to train a machine learning model.
- Algorithm: A procedure used to learn patterns from data.
- Model: The result of training an algorithm.
- Training: The process of teaching a model using data.
- Prediction: Using a trained model to make decisions or estimates.
- Generalization: The ability of a model to perform well on new,
  previously unseen data.

Why is machine learning important?
Instead of manually programming every possible rule, we allow
algorithms to discover patterns and relationships in data.

EXAMPLE:
Instead of programming every possible characteristic of spam email,
we train a model using examples of spam and non-spam emails.

The model learns patterns and uses them to classify new emails.

# Chapter 2: the Two Main Types of Machine Learning

Machine learning is generally divided into two major categories:

1. SUPERVISED LEARNING
2. UNSUPERVISED LEARNING

## A. Supervised Learning

Supervised learning uses labeled training data.

This means we already know the correct answers for the examples
used to train the algorithm.

The model learns the relationship between inputs and outputs.

Important terminology:

- Independent Variables: Input variables used to make predictions.
- Features: Another name for independent/input variables.
- Dependent Variable: The variable we want to predict.
- Target: Another name for the dependent/output variable.
- Labels: Known correct answers in the training dataset.
- Training Dataset: Data containing inputs and known outputs.

General structure:

```
INPUT FEATURES  --->  MACHINE LEARNING MODEL  --->  TARGET

```
Example 1: House Price Prediction

Input features:
- Square footage
- Location
- Year constructed
- Number of bedrooms

Target:
- House price

The model learns how the house characteristics relate to price.

Example 2: Animal Classification

Input features:
- Height
- Weight
- Ear size
- Eye color

Target:
- Cat or Dog

The model learns from labeled examples and predicts the class
of a new animal.

## B. Unsupervised Learning

Unsupervised learning uses data without known target labels.

The algorithm attempts to discover patterns, relationships,
or structures within the data without being given the correct
answers beforehand.

Example:
Imagine giving a computer thousands of animal pictures without
telling it which animals are cats or dogs.

The algorithm attempts to group similar pictures together.

Important terminology:

- Clustering: Grouping similar data points.
- Cluster: A group of similar observations.
- Pattern Recognition: Identifying relationships or similarities.
- Unlabeled Data: Data without predefined correct answers.

Example: Email Organization

Suppose we want to organize emails into three categories.

We do not tell the algorithm what the categories should represent.

Instead, it groups emails based on similarities.

Afterward, we inspect the groups and assign meaningful names.

IMPORTANT DIFFERENCE:

Supervised Learning:
- Uses labeled data.
- Knows the target variable.
- Learns to predict known outputs.

Unsupervised Learning:
- Uses unlabeled data.
- Has no predefined target.
- Attempts to discover hidden structures.

# Chapter 3: Regression vs. Classification

Supervised learning has two major problem categories:

1. REGRESSION
2. CLASSIFICATION

## A. Regression

Regression predicts a continuous numerical value.

A continuous variable can take many numerical values within
a range.

Examples:
- Predicting house prices.
- Predicting temperature.
- Predicting a person's weight.
- Predicting annual income.

Example:
Given the size and location of a house, predict its price.

Possible prediction:
$350,000

The output is a numerical value rather than a category.

## B. Classification

Classification predicts a discrete categorical label.

Instead of predicting a numerical measurement, the algorithm
assigns an observation to a category or class.

Examples:
- Spam or Not Spam.
- Cat or Dog.
- Approved or Rejected.
- High Risk or Low Risk.

Classification can be:

Binary Classification:
Two possible classes.

Example:
- Spam
- Not Spam

Multiclass Classification:
More than two possible classes.

Example:
Gmail email categories:
- Primary
- Social
- Promotions
- Updates

IMPORTANT DIFFERENCE:

Regression = Predicts numerical values.
Classification = Predicts categories or labels.

# Chapter 4: Linear Regression

Linear regression is one of the fundamental machine learning
algorithms.

PURPOSE:
Find a mathematical relationship between input variables
and a continuous numerical output.

The algorithm attempts to fit a line to the training data.

SIMPLE LINEAR REGRESSION EQUATION:

```
y = mx + b

```
Where:
- y = Predicted output.
- x = Input variable.
- m = Slope of the line.
- b = Y-intercept.

The goal is to find the line that best represents the
relationship between the input and output variables.

HOW DOES IT WORK?

1. Collect training data.
2. Identify input and output variables.
3. Fit a line to the observations.
4. Calculate prediction errors.
5. Adjust the line to minimize the errors.

LEAST SQUARES:

The transcript explains that linear regression minimizes
the sum of squared distances between actual data points
and the regression line.

The squared error for one observation is:

```
Error = (Actual Value - Predicted Value)^2

```
The total squared error is:

```
SSE = Σ(yᵢ - ŷᵢ)²

```
Where:
- yᵢ = Actual value.
- ŷᵢ = Predicted value.
- SSE = Sum of Squared Errors.

The objective is to minimize SSE.

EXAMPLE: HEIGHT AND SHOE SIZE

Suppose we discover that for every one-unit increase in shoe size,
a person's height increases by an average of two inches.

The model learns this relationship and uses it to estimate
height from shoe size.

MULTIPLE LINEAR REGRESSION:

Linear regression can use multiple input features.

Example:
Predicting height using:
- Shoe size
- Age
- Gender

A general equation is:

```
y = b₀ + b₁x₁ + b₂x₂ + ... + bₙxₙ

```
Where:
- y = Predicted output.
- b₀ = Intercept.
- b₁, b₂, ... = Model coefficients.
- x₁, x₂, ... = Input features.

IMPORTANT:
Many more complex machine learning algorithms, including
neural networks, extend the general idea of learning
relationships between inputs and outputs.

# Chapter 5: Logistic Regression

Logistic regression is a classification algorithm.

Despite having "regression" in its name, it is commonly used
to predict categorical outcomes.

PURPOSE:
Estimate the probability that an observation belongs
to a particular class.

Instead of fitting a straight regression line, logistic
regression uses a SIGMOID FUNCTION.

SIGMOID FUNCTION:

```
σ(z) = 1 / (1 + e⁻ᶻ)

```
The sigmoid function converts an input into a value
between 0 and 1.

These values can be interpreted as probabilities.

Example:
Suppose a model predicts whether an observation belongs
to a particular category.

Predicted probability:

```
P(Class 1) = 0.80

```
This means the model estimates an 80% probability
of belonging to Class 1.

A classification threshold can then be used.

For example:

```
Probability >= 0.50  --->  Class 1
Probability <  0.50  --->  Class 0

```
The threshold can be adjusted depending on the problem.

IMPORTANT:
- Linear Regression predicts numerical values.
- Logistic Regression estimates class probabilities.
- Logistic Regression is used for classification.

# Chapter 6: K-nearest Neighbors (KNN)

K-Nearest Neighbors (KNN) is a simple and intuitive algorithm
that can be used for BOTH regression and classification.

KNN is a NON-PARAMETRIC algorithm.

What does non-parametric mean?

It does not attempt to fit a predefined mathematical equation
with a fixed set of learned model parameters.

Instead, it makes predictions by examining nearby observations.

HOW KNN WORKS:

1. Select a new data point.
2. Calculate its distance from existing training data points.
3. Identify the K closest observations.
4. Use those neighbors to make a prediction.

The letter K represents the number of neighbors considered.

KNN FOR CLASSIFICATION:

The algorithm uses majority voting.

Example:
We want to classify a person based on height and weight.

Set K = 5.

The five nearest observations are:

- Cat
- Dog
- Dog
- Dog
- Cat

Majority:
Dog = 3
Cat = 2

Prediction = Dog

KNN FOR REGRESSION:

The algorithm calculates the average target value
of the K nearest observations.

Example:

Three nearest people have weights:
- 150 lbs
- 160 lbs
- 170 lbs

Prediction:

```
(150 + 160 + 170) / 3 = 160 lbs

```
CHOOSING K:

K is a HYPERPARAMETER.

A hyperparameter is a setting selected before or during
model configuration rather than learned directly as
an ordinary model parameter.

Small K:
- Considers very few neighbors.
- Can fit training data extremely closely.
- Sensitive to noise.
- Can cause OVERFITTING.

Large K:
- Considers many neighbors.
- Produces smoother predictions.
- Can overlook important local patterns.
- Can cause UNDERFITTING.

OVERFITTING:
A model performs very well on training data but poorly
on new, unseen data.

UNDERFITTING:
A model is too simple to capture the important patterns
in the data.

The best K depends on the dataset and problem.

CROSS-VALIDATION:
A technique used to evaluate different hyperparameter
settings and help select an appropriate K.

IMPORTANT:
KNN is based on the idea that observations that are close
together are likely to have similar characteristics.

# Chapter 7: Support Vector Machines (SVM)

Support Vector Machines (SVM) are supervised machine learning
algorithms originally designed for classification.

They can also be used for regression.

PURPOSE:
Find a decision boundary that separates different classes
as effectively as possible.

DECISION BOUNDARY:

A decision boundary separates observations belonging
to different classes.

Example:
Classify animals using:
- Weight
- Nose length

We want to separate cats from elephants.

The SVM algorithm searches for the boundary that separates
the two classes with the LARGEST POSSIBLE MARGIN.

MARGIN:

The margin is the distance between the decision boundary
and the closest observations from each class.

A larger margin generally helps the model generalize better.

SUPPORT VECTORS:

Support vectors are the data points closest to the decision
boundary.

They determine the position and orientation of the margin.

The support vectors are especially important because
they define the decision boundary.

HIGH-DIMENSIONAL DATA:

When a dataset contains many features, the decision boundary
can be called a HYPERPLANE.

A hyperplane is a generalization of a line or plane
used to separate observations in higher-dimensional spaces.

KERNEL FUNCTIONS:

SVM can use kernel functions to identify nonlinear
relationships and create more complex decision boundaries.

The KERNEL TRICK allows an SVM to work with transformed
feature relationships without explicitly calculating
all the transformed dimensions.

Examples of kernel functions:

- Linear Kernel
- Polynomial Kernel
- Radial Basis Function (RBF) Kernel
- Sigmoid Kernel

EXAMPLE OF FEATURE ENGINEERING:

A model might use:
- Weight
- Height

A more complex feature could be:

```
BMI = Weight / Height²

```
This creates an additional feature that may help
separate observations.

The transcript describes this type of process as
IMPLICIT FEATURE ENGINEERING.

IMPORTANT:
SVM attempts to find a decision boundary with a large margin,
using support vectors to define that boundary.

# Chapter 8: Naive Bayes Classifier

Naive Bayes is a classification algorithm based on
BAYES' THEOREM.

It is frequently used for:
- Spam filtering.
- Text classification.
- Document categorization.
- Other text-based classification problems.

BAYES' THEOREM:

```
P(A|B) = [P(B|A) × P(A)] / P(B)

```
Where:
- P(A|B) = Probability of A given B.
- P(B|A) = Probability of B given A.
- P(A) = Prior probability of A.
- P(B) = Probability of B.

HOW NAIVE BAYES WORKS:

Example: Spam Detection

1. Collect spam and non-spam emails.
2. Count the occurrences of different words.
3. Calculate the probability of words appearing
   in spam and non-spam emails.
4. Examine the words in a new email.
5. Use Bayes' theorem to estimate the probability
   that the email belongs to each class.
6. Assign the email to the most likely class.

WHY IS IT CALLED NAIVE?

Naive Bayes makes a simplifying assumption:

It assumes that the features (such as individual words)
are conditionally independent given the class.

In other words, it treats the presence of different words
as independent pieces of evidence once the class is known.

This assumption is often not completely realistic.

However, it makes the algorithm computationally efficient
and useful for many classification problems.

IMPORTANT:
Naive Bayes is particularly useful for text classification
because it can efficiently calculate class probabilities
using word frequencies.

# Chapter 9: Decision Trees

A decision tree is a supervised learning algorithm that
makes predictions using a sequence of decisions.

It can be used for:
- Classification.
- Regression.

A decision tree resembles a flowchart consisting of
questions and possible answers.

HOW IT WORKS:

1. Start with the entire dataset.
2. Select a feature to split the observations.
3. Divide the data based on the selected condition.
4. Continue splitting into smaller groups.
5. Stop when the resulting groups meet the stopping criteria.

IMPORTANT TERMINOLOGY:

Root Node:
The starting point of the tree.

Decision Node:
A point where a question or condition is evaluated.

Branch:
The path resulting from a decision.

Leaf Node:
The final outcome or prediction.

EXAMPLE: HEART ATTACK RISK

A decision tree might ask:

```
Is the patient's age above 50?
         |
   YES / NO
         |
Does the patient have high blood pressure?
         |
   YES / NO
         |
Determine risk category.

```
The actual tree can contain many more conditions.

PURITY:

The goal is to create leaf nodes that are as PURE as possible.

A pure leaf contains observations belonging predominantly
to the same class.

The algorithm tries to select splits that reduce
misclassification and improve the separation of classes.

IMPORTANT:
Decision trees make predictions using understandable
sequences of conditions and decisions.

# Chapter 10: Ensemble Learning

An ENSEMBLE ALGORITHM combines multiple machine learning
models to create a stronger overall model.

Instead of depending on one model, an ensemble uses
multiple models together.

The idea is that combining several models can improve
prediction performance.

The transcript introduces two major ensemble approaches:

1. BAGGING
2. BOOSTING

# Chapter 11: Bagging and Random Forests

BAGGING stands for Bootstrap Aggregating.

It is an ensemble technique that trains multiple models
using different subsets of the training data.

BOOTSTRAP SAMPLING:

Bootstrap sampling creates training samples by randomly
selecting observations from the original dataset,
typically with replacement.

This means an observation may appear multiple times
in a bootstrap sample.

RANDOM FOREST:

A Random Forest is an ensemble algorithm that combines
many decision trees.

HOW IT WORKS:

1. Create different bootstrap samples of the training data.
2. Train a decision tree on each sample.
3. Randomly select subsets of features for the trees.
4. Combine their predictions.

For CLASSIFICATION:
Trees vote on the predicted class.

The class receiving the majority of votes becomes
the final prediction.

For REGRESSION:
The predictions from the individual trees are combined,
typically by averaging.

WHY USE RANDOM FORESTS?

- Combines multiple decision trees.
- Can perform classification and regression.
- Reduces dependence on a single tree.
- Helps reduce overfitting compared with an individual
  unrestricted decision tree.
- Random feature selection helps reduce correlation
  between the individual trees.

IMPORTANT:
Random Forests generally train trees independently
and combine their predictions.

# Chapter 12: Boosting and Strong Learners

BOOSTING is another ensemble learning technique.

Unlike Random Forests, which generally train trees
in parallel, boosting trains models SEQUENTIALLY.

HOW IT WORKS:

1. Train an initial model.
2. Identify errors made by that model.
3. Train another model that focuses on correcting
   previous errors.
4. Repeat the process.
5. Combine the models to produce a stronger predictor.

WEAK LEARNER:

A weak learner is a model that performs only slightly
better than random guessing in a classification setting.

STRONG LEARNER:

A strong learner is a model that achieves better
overall predictive performance.

Boosting combines multiple weak learners into
a stronger overall model.

EXAMPLES OF BOOSTING ALGORITHMS:

- AdaBoost
- Gradient Boosting
- XGBoost

ADVANTAGES:
- Can achieve high predictive accuracy.
- Sequential models learn from previous mistakes.

DISADVANTAGES:
- Training can be slower because models are trained
  sequentially.
- Can be more prone to overfitting if not configured
  properly.

IMPORTANT DIFFERENCE:

Random Forest:
- Uses multiple trees.
- Trees are generally trained independently.
- Combines their predictions through voting or averaging.

Boosting:
- Trains models sequentially.
- Each new model focuses on previous errors.
- Combines the models into a stronger predictor.

# Chapter 13: Neural Networks and Deep Learning

Neural networks are powerful machine learning models
inspired by the way biological nervous systems process
information.

They are particularly useful for learning complex
relationships in large datasets.

The transcript explains neural networks by first
revisiting logistic regression.

EXAMPLE: HANDWRITTEN DIGIT RECOGNITION

Suppose we want a computer to identify handwritten digits
from 0 through 9.

The input consists of pixel intensities from an image.

The target is the digit represented by that image.

THE PROBLEM:

The same digit can look different depending on:
- Who wrote it.
- How large it is.
- Its orientation.
- The handwriting style.
- Which pixels are illuminated.

For example, handwritten versions of the number 1
will not contain exactly the same illuminated pixels.

However, they share recognizable characteristics.

A number 1 might contain:
- A dominant vertical line.
- Few or no crossing lines.
- No circular shapes.

The computer initially receives pixel values rather
than an understanding of these visual characteristics.

FEATURE ENGINEERING:

Feature engineering is the process of creating useful
input variables from existing data.

For example, we could manually calculate:
- Whether a vertical line exists.
- Whether a horizontal line exists.
- Whether circular shapes exist.

These features could help identify digits.

However, manually creating every useful feature
can be difficult.

NEURAL NETWORKS:

Neural networks can automatically learn useful
intermediate features from the input data.

They do this using layers of interconnected computational
units called neurons.

## Perceptrons

A perceptron is a basic computational unit used
in neural networks.

The transcript describes a single-layer perceptron
as a multi-feature regression-style model.

It takes multiple input features and uses them
to produce an output.

A simplified structure:

```
INPUT FEATURES
      |
      v
  PERCEPTRON
      |
      v
    OUTPUT


```
## Hidden Layers

A hidden layer is a layer between the input and output
layers of a neural network.

These layers allow the network to learn intermediate
representations of the input data.

Example: Digit Recognition

Input:
Pixel intensities from an image.

Hidden layer:
Might learn patterns corresponding to lines,
edges, or shapes.

Output:
Predicted digit from 0 through 9.

The important idea is that humans do not need to
explicitly define every hidden feature.

The network learns useful intermediate features
during training.

## Deep Learning

Deep learning refers to neural networks containing
multiple layers.

Instead of using only one hidden layer, we can add
additional hidden layers.

Each layer can learn more complex representations
from the previous layer.

Simplified example:

```
INPUT PIXELS
     |
     v
HIDDEN LAYER 1
Basic patterns and edges
     |
     v
HIDDEN LAYER 2
More complex shapes
     |
     v
HIDDEN LAYER 3
Higher-level patterns
     |
     v
   OUTPUT
Predicted category

```
The actual features learned by the network are not
always directly interpretable.

We evaluate the network based on how well it predicts
the final target.

IMPORTANT:

Machine Learning:
A broad field of algorithms that learn from data.

Neural Networks:
A family of machine learning models using interconnected
computational units and layers.

Deep Learning:
Neural networks with multiple layers that learn
increasingly complex representations.

# Chapter 14: Unsupervised Learning — Revisited

Supervised learning requires a specific target variable.

However, sometimes we do not have a target to predict.

Instead, we want to understand the underlying structure
of the dataset.

This is where unsupervised learning becomes useful.

A major example is CLUSTERING.

Clustering:
The process of grouping observations based on similarity.

Unlike classification, clustering does not require
predefined labels.

# Chapter 15: Clustering and K-means

CLUSTERING VS. CLASSIFICATION

These two concepts are easy to confuse.

CLASSIFICATION:
- Supervised learning.
- Uses known class labels.
- Learns to predict predefined categories.

CLUSTERING:
- Unsupervised learning.
- Does not use predefined labels.
- Attempts to discover groups within the data.

Example:

Classification:
Given labeled pictures of cats and dogs, predict
whether a new picture contains a cat or dog.

Clustering:
Given unlabeled animal pictures, group similar pictures
together without knowing the categories beforehand.

## K-means Clustering

K-means is one of the most common clustering algorithms.

The K represents the number of clusters we want
the algorithm to identify.

HOW K-MEANS WORKS:

1. Choose the number of clusters (K).
2. Randomly initialize K cluster centers.
3. Assign each data point to its nearest cluster center.
4. Recalculate the cluster centers using the assigned
   data points.
5. Reassign data points based on the updated centers.
6. Repeat until the centers stabilize or another
   stopping condition is reached.

CLUSTER CENTROID:

A centroid is the center of a cluster.

The algorithm repeatedly updates the centroids based
on the observations assigned to each cluster.

EXAMPLE:

Suppose we have customer data containing:
- Annual income.
- Spending score.

We choose K = 3.

The algorithm attempts to divide the customers into
three groups based on their similarities.

The resulting clusters might represent:
- Low-spending customers.
- Medium-spending customers.
- High-spending customers.

These interpretations are assigned after examining
the resulting clusters.

CHOOSING K:

Selecting the correct number of clusters can be difficult.

The best K depends on:
- The dataset.
- The problem being studied.
- Domain knowledge.
- Evaluation and experimentation.

OTHER CLUSTERING ALGORITHMS:

1. Hierarchical Clustering
   Builds a hierarchy of clusters.

2. DBSCAN
   Identifies clusters based on data density.

   It can discover clusters with arbitrary shapes
   and does not require specifying the number of
   clusters beforehand.

# Chapter 16: Dimensionality Reduction

Dimensionality reduction is the process of reducing
the number of features (dimensions) in a dataset
while preserving as much useful information as possible.

WHY IS IT IMPORTANT?

Large datasets can contain many features.

Some features may:
- Be strongly correlated.
- Contain redundant information.
- Add unnecessary complexity.
- Introduce noise.

Reducing the number of dimensions can make machine
learning models more efficient and robust.

EXAMPLE: IMAGE RECOGNITION

Suppose we want to recognize an airplane in an image.

Do we need every pixel from a high-resolution image?

Perhaps we can reduce the image resolution and still
retain enough information to recognize the airplane.

This is an example of reducing dimensionality.

BENEFITS:

- Reduces the number of features.
- Can remove redundant information.
- Can improve computational efficiency.
- Can help reduce noise.
- Can be used as a preprocessing step before supervised
  learning.

# Chapter 17: Principal Component Analysis (PCA)

Principal Component Analysis (PCA) is a dimensionality
reduction technique.

PURPOSE:
Find new directions in the data that preserve as much
of the original data's variance as possible.

IMPORTANT TERMINOLOGY:

Variance:
A measure of how spread out the data is.

Correlation:
A measure of how strongly two variables are related.

Principal Component:
A new direction or combination of original features
that captures variation in the data.

EXAMPLE: CLASSIFYING FISH

Suppose we want to predict fish species using:
- Length.
- Height.
- Color.
- Number of teeth.

We examine the relationships between the features.

Suppose height and length are strongly correlated.

Including both might provide redundant information.

PCA can combine information from these features into
a new component representing their shared variation.

This may allow us to reduce the number of features
without losing much useful information.

## How PCA Works

1. Examine the relationships and variation among features.
2. Identify directions in which the data varies the most.
3. Create principal components representing those directions.
4. Rank components according to the amount of variance
   they explain.
5. Retain the most useful components.
6. Exclude components that contribute relatively little
   information.

FIRST PRINCIPAL COMPONENT (PC1):

The direction that captures the greatest amount
of variance in the data.

SECOND PRINCIPAL COMPONENT (PC2):

The direction perpendicular (orthogonal) to PC1
that captures the greatest remaining variance.

Additional components follow the same general idea.

ORTHOGONAL:
Two directions are orthogonal when they are perpendicular
to one another.

EXPLAINED VARIANCE:

Explained variance measures how much of the dataset's
variation is captured by a principal component.

The components can be ranked by explained variance.

Components contributing little variance may be removed.

IMPORTANT:
PCA reduces the number of dimensions while attempting
to preserve the most important variation in the data.

# Final Review: Machine Learning Algorithm Comparison

SUPERVISED LEARNING

Algorithm              Purpose
Linear Regression      Predict continuous numerical values.
Logistic Regression    Predict class probabilities.
KNN                    Predict using nearby observations.
SVM                    Separate classes using a boundary.
Naive Bayes            Classify using Bayes' theorem.
Decision Trees         Predict using decision rules.
Random Forest          Combine multiple decision trees.
Boosting               Sequentially improve weak models.
Neural Networks        Learn complex patterns and features.

UNSUPERVISED LEARNING

Algorithm              Purpose
K-Means                Group data into K clusters.
Hierarchical           Build a hierarchy of clusters.
DBSCAN                 Find density-based clusters.
PCA                    Reduce the number of dimensions.

NOTE:
PCA is a dimensionality reduction technique rather than
a clustering algorithm. It is commonly used as a
preprocessing technique.

# Important Concepts to Remember

1. Machine Learning:
   Learning patterns from data to make predictions
   or discover structure.

2. Supervised Learning:
   Training with labeled data.

3. Unsupervised Learning:
   Finding patterns in unlabeled data.

4. Features:
   Input variables used by the model.

5. Target:
   The variable the model attempts to predict.

6. Regression:
   Predicting continuous numerical values.

7. Classification:
   Predicting discrete categories.

8. Overfitting:
   Performing well on training data but poorly
   on unseen data.

9. Underfitting:
   Failing to learn important patterns because
   the model is too simple.

10. Hyperparameter:
    A configuration setting that controls how
    an algorithm operates.

11. Cross-Validation:
    A technique for evaluating models and selecting
    hyperparameters.

12. Decision Boundary:
    A boundary separating different predicted classes.

13. Support Vectors:
    Data points closest to an SVM decision boundary.

14. Ensemble Learning:
    Combining multiple models to improve predictions.

15. Bagging:
    Training models on different bootstrap samples
    and combining their predictions.

16. Boosting:
    Training models sequentially to correct previous
    model errors.

17. Hidden Layer:
    A neural network layer between input and output.

18. Deep Learning:
    Neural networks with multiple layers.

19. Clustering:
    Grouping similar observations without known labels.

20. Dimensionality Reduction:
    Reducing the number of features while preserving
    useful information.

21. PCA:
    Finding directions that capture the most variance
    in a dataset.

# The Big Picture

```
             MACHINE LEARNING
                    |
         +----------+----------+
         |                     |
   SUPERVISED             UNSUPERVISED
    LEARNING                LEARNING
         |                     |
   +-----+-----+          +----+---------+
   |           |          |              |
```
   REGRESSION  CLASSIFICATION CLUSTERING  DIMENSIONALITY
       |           |          |           REDUCTION
       |           |          |              |
   Linear      Logistic     K-Means         PCA
   Regression  Regression   Hierarchical
               KNN          DBSCAN
               SVM
               Naive Bayes
               Decision Trees
               Random Forest
               Boosting
               Neural Networks

The central idea:

Machine learning algorithms learn patterns from data.

Some algorithms predict numerical values.
Some predict categories.
Some discover groups.
Others reduce the complexity of data.

The correct algorithm depends on the problem,
the type of data, and the result we want to obtain.
