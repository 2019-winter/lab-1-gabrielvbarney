---
jupyter:
  jupytext:
    formats: ipynb,md
    text_representation:
      extension: .md
      format_name: markdown
      format_version: '1.1'
      jupytext_version: 1.2.4
  kernelspec:
    display_name: Python 3
    language: python
    name: python3
---

# Name(s)
# Gabriel Barney


**Instructions:** This is an individual assignment, but you may discuss your code with your neighbors.


# Python and NumPy

While other IDEs exist for Python development and for data science related activities, one of the most popular environments is Jupyter Notebooks.

This lab is not intended to teach you everything you will use in this course. Instead, it is designed to give you exposure to some critical components from NumPy that we will rely upon routinely.

## Exercise 0
Please read and reference the following as your progress through this course. 

* [What is the Jupyter Notebook?](https://nbviewer.jupyter.org/github/jupyter/notebook/blob/master/docs/source/examples/Notebook/What%20is%20the%20Jupyter%20Notebook.ipynb#)
* [Notebook Tutorial](https://www.datacamp.com/community/tutorials/tutorial-jupyter-notebook)
* [Notebook Basics](https://nbviewer.jupyter.org/github/jupyter/notebook/blob/master/docs/source/examples/Notebook/Notebook%20Basics.ipynb)

**In the space provided below, what are three things that still remain unclear or need further explanation?**


- Honestly, the Jupyter Notebook is pretty clear. Rather than having questions on this, I am moreso confused on Pandas. I am going to do more research on it as time goes on to 


## Exercises 1-7
For the following exercises please read the Python appendix in the Marsland textbook and answer problems A.1-A.7 in the space provided below.


## Exercise 1

```python
# YOUR SOLUTION HERE
import numpy as n
a = n.ones((6,4))*2
a
```

## Exercise 2

```python
# YOUR SOLUTION HERE
b = n.ones((6,4))
b[range(4),range(4)] = 3
b
```

## Exercise 3

```python
# YOUR SOLUTION HERE
a*b
#n.dot(a,b)
"""We can multiply each value of matrix a to the value in the
corresponding coordinate of matrix b, but we cannot take the dot
product because the second dimension of matrix a does not match
the first dimension of matrix b."""
```

## Exercise 4

```python
# YOUR SOLUTION HERE
display(n.dot(a.transpose(), b))
display(n.dot(a, b.transpose()))
"""It is because when taking the dot product, order of dimension-
ality is taken into account. By this, I mean that a dot product 
of a 4x6 matrix and a 6x4 matrix yields a matrix that matches the
first dimension of the first matrix, followed by the second dimen-
sion of the second matrix (and vice versa for a dot product of a 
6x4 matrix and a 4x6 matrix)."""
```

## Exercise 5

```python
# YOUR SOLUTION HERE
def _printer():
    print("Hello, World!\n")

_printer()
```

## Exercise 6

```python
# YOUR SOLUTION HERE
def rand_sum_and_mean():
    c = n.random.rand(3, 3)
    d = n.random.rand(3, 3)
    _sum = n.sum(c) + n.sum(d)
    mean = _sum / (len(c) + len(d))
    print("Sum: {0}\nMean: {1}".format(_sum, mean))
    
rand_sum_and_mean()
```

#Exercise 7

```python
# YOUR SOLUTION HERE
def counter(arr):
     num = 0
     n.where(arr == 1, arr, 1)
     for i in arr:
         for j in i:
             if int(j) == 1:
                 num += 1
     return num

arr = [[0, 1, 3, 1], [3, 1, 1, 5]]
# n.where(1, 0, 1)
# y = n.where(2, 0, 1)
counter(arr)

```

## Excercises 8-???
While the Marsland book avoids using another popular package called Pandas, we will use it at times throughout this course. Please read and study [10 minutes to Pandas](https://pandas.pydata.org/pandas-docs/stable/getting_started/10min.html) before proceeding to any of the exercises below.


## Exercise 8
Repeat exercise A.1 from Marsland, but create a Pandas DataFrame instead of a NumPy array.

```python
# YOUR SOLUTION HERE
import pandas as p
import numpy as n
a = p.DataFrame(n.ones((6,4))*2)
a
```

## Exercise 9
Repeat exercise A.2 using a DataFrame instead.

```python
# YOUR SOLUTION HERE
b = n.ones((6, 4))
b = p.DataFrame(b)
b.iloc[range(4), range(4)] = 3
b
```

## Exercise 10
Repeat exercise A.3 using DataFrames instead.

```python
# YOUR SOLUTION HERE
a*b
"""We can multiply each value of matrix a to the value in the
corresponding coordinate of matrix b, but we cannot take the dot
product because the second dimension of matrix a does not match
the first dimension of matrix b."""
```

## Exercise 11
Repeat exercise A.7 using a dataframe.

```python
# YOUR SOLUTION HERE
def counter(b):
     num = 0
     n.where(b == 1, b, 1)
     for i in b:
        if i == 1:
            num += 1
     return num

counter(b)
```

## Exercises 12-14
Now let's look at a real dataset, and talk about ``.loc``. For this exercise, we will use the popular Titanic dataset from Kaggle. Here is some sample code to read it into a dataframe.

```python
titanic_df = p.read_csv(
    "https://raw.githubusercontent.com/dlsun/data-science-book/master/data/titanic.csv"
)
titanic_df
```

Notice how we have nice headers and mixed datatypes? That is one of the reasons we might use Pandas. Please refresh your memory by looking at the 10 minutes to Pandas again, but then answer the following.


## Exercise 12
How do you select the ``name`` column without using .iloc?

```python
## YOUR SOLUTION HERE
titanic_df['name']
```

## Exercise 13
After setting the index to ``sex``, how do you select all passengers that are ``female``? And how many female passengers are there?

```python
## YOUR SOLUTION HERE
is_female = titanic_df['sex'] = 'female'
female_df = titanic_df[is_female]
# There are 10 female passengers
```

## Exercise 14
How do you reset the index?

```python
## YOUR SOLUTION HERE
```

```python
titanic_df.reset_index(drop=True)
```

```python

```
