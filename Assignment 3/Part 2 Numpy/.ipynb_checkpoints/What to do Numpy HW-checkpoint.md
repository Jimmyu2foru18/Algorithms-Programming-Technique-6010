# CEREAL DATA STATISTICAL ANALYSIS — ASSIGNMENT INSTRUCTIONS

## PURPOSE

The goal of this assignment is to use Python, NumPy, and statistics
to investigate a cereal dataset.

You will:

1. Practice NumPy using the provided crash-course notebooks.
2. Load and analyze the cereal CSV file.
3. Answer the required statistical questions.
4. Create your own statistical investigation.
5. Present your investigation for approximately 2–4 minutes.

The final work should be organized and documented so that another
person can understand what you did, why you did it, and what your
results mean.

----------------------------------------------------------------------
## PART 1 — NUMPY PREPARATION
----------------------------------------------------------------------

### Step 1: Review NumPy

First, look through the NumPy Quickstart:

https://numpy.org/devdocs/user/quickstart.html

Then complete the NumPy crash-course notebooks provided by your
professor.

Go through the notebooks IN ORDER.

Complete the exercises at the end of the notebooks.

The goal is to understand:

- NumPy arrays
- Indexing
- Slicing
- Array calculations
- Boolean conditions
- Mean
- Minimum
- Maximum
- Standard deviation
- Variance
- Multidimensional arrays

You do not need to memorize every NumPy function. You should
understand how to use the functions needed for this assignment.

----------------------------------------------------------------------
## PART 2 — LOAD THE CEREAL DATASET
----------------------------------------------------------------------

### Step 2: Import the libraries

Start your notebook with:

import numpy as np
import csv

If you decide to make a graph for your statistical investigation,
also use:

import matplotlib.pyplot as plt


### Step 3: Read the CSV file

Use the method demonstrated by your professor:

with open('cereal.csv', 'r') as f:
	reader = csv.reader(f)
	data = list(reader)

data_array = np.array(data)

Display the data:

data_array

Check the number of rows:

len(data_array)


### Documentation

After loading the dataset, write a Markdown explanation such as:

"The cereal dataset was loaded from a CSV file and converted into a
NumPy array. The dataset contains nutritional information for
different cereals, including calories, protein, fat, fiber,
carbohydrates, sugar, potassium, and vitamins."


----------------------------------------------------------------------
## PART 3 — UNDERSTAND THE DATA
----------------------------------------------------------------------

Before performing calculations, identify what each column represents.

The important columns are:

0  = name
1  = mfr
2  = type
3  = calories
4  = protein
5  = fat
6  = sodium
7  = fiber
8  = carbo
9  = sugars
10 = potass
11 = vitamins
12 = shelf
13 = weight
14 = cups
15 = rating

The most important columns for this assignment are:

name
mfr
protein
fat
fiber
carbo
sugars
potass
vitamins


----------------------------------------------------------------------
## PART 4 — CREATE NUMPY ARRAYS
----------------------------------------------------------------------

The CSV data is initially read as strings.

For calculations, numerical columns need to be converted to numbers.

Create arrays for the columns you will analyze:

names = np.array(data_array[1:, 0])

protein = np.array(data_array[1:, 4], dtype=float)
fat = np.array(data_array[1:, 5], dtype=float)
fiber = np.array(data_array[1:, 7], dtype=float)
carbo = np.array(data_array[1:, 8], dtype=float)
sugars = np.array(data_array[1:, 9], dtype=float)
potass = np.array(data_array[1:, 10], dtype=float)
vitamins = np.array(data_array[1:, 11], dtype=float)

The [1:] removes the header row.

The dtype=float converts numerical values from strings into
floating-point numbers.

For example:

"12"

becomes:

12.0


### Documentation

Write:

"The numerical columns were converted from strings into floating-point
NumPy arrays so that mathematical and statistical operations could be
performed on the data."


----------------------------------------------------------------------
## PART 5 — SUGAR ANALYSIS
----------------------------------------------------------------------

### Question 1

Determine:

- Which cereal has the most sugar?
- Which cereal has the least sugar?
- What is the average amount of sugar?
- Which cereals have below-average sugar?


### Step 1: Calculate the average

average_sugar = np.mean(sugars)

print("Average sugar:", average_sugar)


### Step 2: Find the maximum sugar value

max_sugar = np.max(sugars)

print("Maximum sugar:", max_sugar)


### Step 3: Find the minimum sugar value

min_sugar = np.min(sugars)

print("Minimum sugar:", min_sugar)


### Step 4: Find the cereal with the maximum sugar

max_sugar_index = np.argmax(sugars)

print("Cereal with the most sugar:", names[max_sugar_index])
print("Sugar:", sugars[max_sugar_index])


### Step 5: Find the cereal with the minimum sugar

min_sugar_index = np.argmin(sugars)

print("Cereal with the least sugar:", names[min_sugar_index])
print("Sugar:", sugars[min_sugar_index])


### Step 6: Find cereals below average sugar

below_average = sugars < average_sugar

print(names[below_average])


### Better version that shows the sugar values

for name, sugar in zip(names[below_average], sugars[below_average]):
	print(name, sugar)


### Documentation

After your code, write a statement like:

"The average sugar content of the cereals in this dataset is
approximately ___ grams per serving."

"The cereal with the highest sugar content is ___, with ___ grams of
sugar per serving."

"The cereal with the lowest sugar content is ___, with ___ grams of
sugar per serving."

"There are ___ cereals with sugar content below the dataset average."

"The cereals with below-average sugar content are ___."


IMPORTANT:

Do not just write:

"Average = 10."

Instead write:

"The average sugar content is 10 grams per serving."

Always explain what your number represents.


----------------------------------------------------------------------
## PART 6 — POTASSIUM ANALYSIS
----------------------------------------------------------------------

Your professor's assignment says:

"Find out what percent aisle is each cereal in terms of potassium."

The wording appears to contain a typo.

The dataset contains:

- potass
- shelf

The assignment most likely intends a potassium percentile analysis,
but you should verify the exact meaning of this question with your
professor if necessary.

If the intended question is potassium percentile, determine what
percentage of cereals have potassium values less than or equal to
each cereal.

You can calculate this with:

potassium_percentile = np.array([
	np.mean(potass <= value) * 100
	for value in potass
])


Then print the results:

for name, potassium, percentile in zip(
	names,
	potass,
	potassium_percentile
):
	print(f"{name}: {potassium} potassium, {percentile:.2f} percentile")


### Documentation

Write:

"The potassium percentile describes how each cereal's potassium
content compares with the other cereals in the dataset. A higher
percentile means that the cereal has more potassium than a larger
percentage of the cereals in the dataset."


----------------------------------------------------------------------
## PART 7 — FIND CEREALS WITH NO FIBER
----------------------------------------------------------------------

### Question

Which cereals have no fiber?


Use:

no_fiber = fiber == 0

print(names[no_fiber])


### Documentation

Write:

"I used a Boolean condition to identify cereals with exactly zero
grams of fiber. The cereals meeting this condition are: ___."


----------------------------------------------------------------------
## PART 8 — NO FIBER AND ABOVE-AVERAGE SUGAR
----------------------------------------------------------------------

### Question

Which cereals have:

- No fiber
AND
- Above-average sugar?


Use:

condition = (fiber == 0) & (sugars > average_sugar)

print(names[condition])


### Documentation

Explain that BOTH conditions must be true.

Write:

"I searched for cereals that contained zero grams of fiber and had
sugar content greater than the dataset average. The resulting cereals
satisfy both conditions."


IMPORTANT:

Use:

&

for NumPy conditions.

Do not use:

and

when combining NumPy arrays.


----------------------------------------------------------------------
## PART 9 — NO FAT AND BELOW-AVERAGE SUGAR
----------------------------------------------------------------------

### Question

Which cereals have:

- No fat
AND
- Below-average sugar?


Use:

condition = (fat == 0) & (sugars < average_sugar)

print(names[condition])


### Documentation

Write:

"I searched for cereals containing zero grams of fat and less sugar
than the dataset average. The cereals returned by the Boolean filter
satisfy both conditions."


----------------------------------------------------------------------
## PART 10 — CARBOHYDRATE STATISTICS
----------------------------------------------------------------------

### Question

Find:

- Mean carbohydrates
- Standard deviation of carbohydrates
- Variance of carbohydrates


### Mean

mean_carbo = np.mean(carbo)


### Standard deviation

std_carbo = np.std(carbo)


### Variance

var_carbo = np.var(carbo)


### Print the results

print("Mean carbohydrates:", mean_carbo)
print("Standard deviation:", std_carbo)
print("Variance:", var_carbo)


### Documentation

Do NOT simply write:

"Mean = ___
SD = ___
Variance = ___"

Instead explain them.

Write:

"The mean carbohydrate content is approximately ___ grams per
serving. This represents the average carbohydrate content across
the cereals in the dataset."

"The standard deviation is approximately ___. This describes the
amount of variation in carbohydrate content around the mean."

"The variance is approximately ___. Variance measures the squared
variation of carbohydrate values around the mean."


----------------------------------------------------------------------
## PART 11 — CARB-LOADING QUESTION
----------------------------------------------------------------------

### Question

"If you were carb-loading which cereal would you get?"


Find the cereal with the maximum carbohydrate value:

max_carbo_index = np.argmax(carbo)

print("Cereal with the most carbohydrates:",
      names[max_carbo_index])

print("Carbohydrates:",
      carbo[max_carbo_index])


### Documentation

Write:

"If the goal were to maximize carbohydrate intake per serving, the
cereal with the highest carbohydrate content in this dataset would be
___, containing ___ grams of carbohydrates per serving."

Be careful with your wording.

Do not claim:

"This is the healthiest cereal."

The data only tells you which cereal has the most carbohydrates.

----------------------------------------------------------------------
## PART 12 — YOUR OWN STATISTICAL INVESTIGATION
----------------------------------------------------------------------

This is the most important part of the assignment.

You need to create your OWN statistical question using the cereal
dataset.

Your investigation should:

1. Ask a question.
2. Create a hypothesis.
3. Choose appropriate variables.
4. Use a statistical method.
5. Calculate the statistic.
6. Interpret the result.
7. State a conclusion.
8. Ideally include a graph.


----------------------------------------------------------------------
## RECOMMENDED INVESTIGATION
----------------------------------------------------------------------

A simple investigation is:

"Is sugar positively related to carbohydrates in cereal?"


### Research Question

Write:

"Is there a positive linear relationship between sugar and
carbohydrate content in cereal?"


### Hypothesis

Write something like:

"I hypothesize that cereals with higher sugar content will tend to
have higher carbohydrate content."


Remember:

A hypothesis is your prediction BEFORE looking at the result.

Do not change your hypothesis after seeing the data.


----------------------------------------------------------------------
## PART 13 — CALCULATE CORRELATION
----------------------------------------------------------------------

Use NumPy:

correlation = np.corrcoef(sugars, carbo)

print(correlation)


The correlation coefficient can be extracted using:

r = np.corrcoef(sugars, carbo)[0, 1]

print("Correlation coefficient:", r)


The correlation coefficient ranges from:

-1 to +1


A value closer to +1 indicates a stronger positive linear
relationship.

A value closer to 0 indicates a weaker linear relationship.

A value closer to -1 indicates a stronger negative linear
relationship.


IMPORTANT:

Correlation does NOT prove causation.

If sugar and carbohydrates are correlated, you should say:

"The variables are associated."

Do NOT automatically say:

"Sugar causes carbohydrates."

----------------------------------------------------------------------
## PART 14 — MAKE A GRAPH
----------------------------------------------------------------------

Create a scatter plot:

plt.scatter(sugars, carbo)

plt.xlabel("Sugar (grams)")
plt.ylabel("Carbohydrates (grams)")
plt.title("Relationship Between Sugar and Carbohydrates")

plt.show()


The graph helps visually show whether the two variables have a
relationship.


----------------------------------------------------------------------
## PART 15 — WRITE YOUR INVESTIGATION
----------------------------------------------------------------------

Use this exact structure:

# Statistical Investigation

## Research Question

"Is there a positive linear relationship between sugar and
carbohydrate content in cereal?"

## Hypothesis

"I hypothesize that cereals with higher sugar content will tend to
have higher carbohydrate content."

## Variables

Independent/explanatory variable:
Sugar content

Dependent/response variable:
Carbohydrate content

## Method

"I calculated the Pearson correlation coefficient between sugar and
carbohydrate content using NumPy. I also created a scatter plot to
visually examine the relationship between the variables."

## Result

"The calculated correlation coefficient was r = ___."

## Interpretation

"The correlation coefficient indicates a ___ linear relationship
between sugar and carbohydrate content."

Explain what the value means in context.

## Conclusion

"Based on this dataset, the results [support/do not support] my
hypothesis that cereals with higher sugar content tend to have
higher carbohydrate content."

Then add:

"Because this analysis uses observational data, the correlation does
not establish that one variable causes the other."


----------------------------------------------------------------------
## HOW TO WRITE GOOD STATISTICAL STATEMENTS
----------------------------------------------------------------------

Always follow this pattern:

STATISTIC
+
WHAT IT MEANS
+
CONTEXT


BAD:

"Mean = 10.5."


GOOD:

"The mean sugar content of the cereals in the dataset is 10.5 grams
per serving."


BAD:

"Correlation is 0.7."


GOOD:

"The correlation coefficient between sugar and carbohydrates is
r = 0.70, indicating a positive linear relationship between the two
variables."


BAD:

"Cereal X is better."


GOOD:

"Cereal X contains less sugar than the dataset average."


Avoid words such as:

- better
- worse
- healthiest
- best
- terrible
- good

unless the assignment specifically gives you a measurable criterion
for making that judgment.

Instead, describe exactly what the data shows.


----------------------------------------------------------------------
## HOW TO WRITE RESULTS
----------------------------------------------------------------------

Use complete sentences.

For example:

"The average sugar content was ___ grams per serving."

"The maximum sugar value was ___ grams per serving."

"___ had the highest sugar content at ___ grams per serving."

"___ cereals had sugar content below the dataset average."

"The mean carbohydrate content was ___ grams per serving."

"The standard deviation was ___ grams."

"The variance was ___."


----------------------------------------------------------------------
## HOW TO WRITE INTERPRETATIONS
----------------------------------------------------------------------

A result tells the reader WHAT happened.

An interpretation tells the reader WHAT IT MEANS.


RESULT:

"The standard deviation of carbohydrates was 5.2."


INTERPRETATION:

"The standard deviation of 5.2 grams indicates that carbohydrate
values typically vary around the mean by several grams."


RESULT:

"r = 0.65"


INTERPRETATION:

"The correlation coefficient of 0.65 indicates a moderately positive
linear relationship between sugar and carbohydrates."


----------------------------------------------------------------------
## HOW TO WRITE CONCLUSIONS
----------------------------------------------------------------------

Your conclusion should answer your original question.

Use this structure:

"Based on the data, ______."

"Therefore, the results ______ my hypothesis."

"However, this analysis does not prove causation because ______."


Example:

"Based on the cereal dataset, sugar and carbohydrates show a positive
linear relationship. Therefore, the results support my hypothesis
that cereals with higher sugar content tend to have higher
carbohydrate content. However, correlation does not prove that sugar
causes an increase in carbohydrates."


----------------------------------------------------------------------
## PART 16 — PRESENTATION
----------------------------------------------------------------------

Your presentation should be approximately 2–4 minutes.

You do NOT need to explain every line of Python code.

Focus primarily on your statistical investigation.


### Presentation structure

#### 1. Introduction — approximately 30 seconds

Say:

"I analyzed a cereal dataset containing nutritional information for
different cereals. I used Python and NumPy to calculate descriptive
statistics and investigate relationships between nutritional
variables."


#### 2. Briefly mention required analysis — approximately 30–60 seconds

Discuss a few important results:

"The average sugar content was ___ grams."

"The cereal with the highest sugar content was ___."

"The cereal with the lowest sugar content was ___."

"The mean carbohydrate content was ___ grams, with a standard
deviation of ___."


You do not need to read every cereal from every result.


#### 3. Explain your investigation — approximately 1–2 minutes

Say:

"My investigation question was whether sugar and carbohydrates have
a positive linear relationship."

"My hypothesis was that cereals with higher sugar content would tend
to have higher carbohydrate content."

"I calculated the Pearson correlation coefficient."

"The resulting correlation was r = ___."

Explain what the value means.

Show your scatter plot.


#### 4. Conclusion — approximately 30 seconds

Say:

"Based on the results, the data [supports/does not support] my
hypothesis."

"The correlation indicates ___."

"However, correlation does not establish causation."


----------------------------------------------------------------------
## FINAL NOTEBOOK CHECKLIST
----------------------------------------------------------------------

Before submitting, make sure you have:

[ ] NumPy imported

[ ] CSV imported

[ ] cereal.csv successfully loaded

[ ] Dataset converted into a NumPy array

[ ] Numerical columns converted from strings to numbers

[ ] Sugar maximum calculated

[ ] Sugar minimum calculated

[ ] Average sugar calculated

[ ] Below-average sugar cereals identified

[ ] Potassium analysis completed or clarified with professor

[ ] No-fiber cereals identified

[ ] No-fiber + above-average-sugar cereals identified

[ ] No-fat + below-average-sugar cereals identified

[ ] Mean carbohydrates calculated

[ ] Standard deviation calculated

[ ] Variance calculated

[ ] Highest-carbohydrate cereal identified

[ ] Own statistical question created

[ ] Hypothesis written

[ ] Statistical method explained

[ ] Statistic calculated

[ ] Statistic interpreted

[ ] Graph created if appropriate

[ ] Conclusion written

[ ] Results are explained in complete sentences

[ ] Presentation prepared

[ ] Presentation is approximately 2–4 minutes


----------------------------------------------------------------------
## MOST IMPORTANT RULE FOR DOCUMENTATION
----------------------------------------------------------------------

For every major piece of code, follow this pattern:

1. WHAT AM I DOING?
2. CODE
3. WHAT DID I GET?
4. WHAT DOES IT MEAN?


Example:

## Average Sugar

### What am I doing?

"I want to determine the average amount of sugar per serving across
all cereals in the dataset."

### Code

average_sugar = np.mean(sugars)

print("Average sugar:", average_sugar)

### Result

"The average sugar content was ___ grams per serving."

### Interpretation

"This means that the typical cereal in this dataset contains
approximately ___ grams of sugar per serving."


This makes your assignment look like a statistical analysis rather
than just a collection of Python commands.