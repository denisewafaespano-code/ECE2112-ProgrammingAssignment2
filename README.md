# EXPERIMENT 2: NUMERICAL PYTHON (NUMPY)
**Made by**: Denise Wafa B. Españo
<div style="border-bottom: 2px solid gray; margin-bottom: 10px;"></div>

The content of this repository contains Programming Assignment 2 for our course "Advanced Programming and Algorithms". This Project covers three Python problems related to Numerical Python (NumPy).

**Objectives**
At the end of this assignment, the goal is to be able to successfully create and reshape NumPy arrays, perform vectorized numerical operations, compute arrays, use Boolean conditions, and save arrays to `.npy` files. 

## A. REPRODUCIBLE NORMALIZATION PROBLEM
<div style="border-bottom: 2px solid gray; margin-bottom: 10px;"></div>

**Instruction:**    
Create a reproducible random 5 x 5 integer array, calculate its mean and standard deviation, and apply these values to normalize the entire array.

The following functions and methods were used in this problem:

To begin, a random seed was set with `np.random.seed(2112)` to ensure the same random values are produced every time the code is executed.

Following this, `np.random.randit()` was utilized to create the array itself. This function generates random integers within a specified range and arranges them according to the given dimensions. 

>*Example*: `np.random.randint(0, 10, size=(2,2))` creates a simple 2 x 2 grid with random numbers from 0 to 9.


```python
np.random.seed(2112)
X = np.random.randint (10, 101, size=(5,5))
```

In order to normalize the array, standard statistical functions were required
* `np.mean()` - computes the arithmetic mean  ($\overline{x}$) of all 25 elements in the grid.
* `np.std`- computes the population standard deviation $\sigma$ of the array
These variables were applied directly to the array `X`.

```python
mean = np.mean(X)
std = np.std(X)
X_normalized = (X - mean / std)
```
Combining them all, including required print statements and the `np.save()` function to export the `.npy` file, the final code is as follows:

```python
import numpy as np
np.random.seed(2112)
X = np.random.randint (10, 101, size=(5,5))

mean = np.mean(X)
std = np.std(X)
X_normalized = (X - mean / std)

print("Mean of X:", mean)
print("Std of x:",std)

np.save('x_normalized.npy', X_normalized)
```
## B. CUBES DIVISIBLE BY 4 PROBLEM
<div style="border-bottom: 2px solid gray; margin-bottom: 10px;"></div>

**Instruction:**

Create an array of the first 100 positive integers, cube every element, reshape the result into a 10 x 10 array, and use the Boolean condition to extract only the values that are divisible by 4.

The following instructions and methods were used in this problem:

The `np.arange()` function creates a sequence of integers (from 1 to 100), which is then immediately cubed using the exponentiation operator `(**3)`. Instead of leaving it as a flat list, the `reshape(10, 10)` method is used at the end to reshape the array into a 10 x 10 grid.

```python
C = (np.arange(1,,101) **3).reshape(10,10)
```

To filter this created array, a Boolean mask is utilized. By applying the modulo operator `(% 4 == 0)`, the code checks every single element to see if it is perfectly divisible by 4, extracting only those that return a `True` value.
>*Example*: `8 % 4 == 0` evaluates to `True` (remainder is zero), so the number 8 is kept. Conversely, `27 % 4 == 0` evaluates to `False`, so 27 is discarded. 

```python
div_by_4 = C[C % 4 == 0]
```

Combining all, alongside the required checks for the array's shape and size, the final code for this problem is as follows:

```python
C = (np.arange(1,101) ** 3).reshape(10,10)
div_by_4 = C[C % 4 == 0]

print("Shape of C:", C.shape)
print("\nArray div_by_4:\n", div_by_4)
print("\nNumber of selected elements:", div_by_4.size)
np.save('div_by_4.npy', div_by_4)
```

## C. ABOVE-MEAN SQAURES PROBLEM
<div style="border-bottom: 2px solid gray; margin-bottom: 10px;"></div>

**Instructions:**

Create a 6 x 6 array containing the squares of the first 36 positive integers, compute the overall mean of these elements, and extract only the values that are strictly greater than this computed mean.

The following functions and methods were used in this problem:

Similar to the previous problem, a sequence of numbers needed to be generated, manipulated mathematically, and arranged into a grid.

```python
S = (np.arange(1,37) **2).reshape(6,6)
```
* `np.arange(1,37)` - generates the first 36 positive integers.
* `**2` - squares each of these integers immediately
* `.reshape(6,6)` - organizes the 36 sqaured values into a structures 6 x 6 matrix in row-major order.

To sort through the array, a target number had to be determined first. The `np.mean()` function was used to calculate the exact average of all 36 elements inside our matrix.

```python
S_mean = np.mean(S)
```
With the mean calculated, a comparison operator was used to evaluate through the matrix. The condition `S > S_mean` creates a filter that evaluates every element, returning only the specific values that are strictly greater than the calculated average:

```python
above_mean = S[S > S_mean]
```

Combining all, printing the outputs, and saving the final filtered array, the complete code is as follows:

```python
S = (np.arange(1,37) ** 2).reshape(6,6)
S_mean = np.mean(S)
above_mean = S[S > S_mean]

print("Array S:\n", S)
print("\nS_mean:", S_mean)
print("\nArray above_mean:\n", above_mean)
print("\nNumber of selected elements:", above_mean.size)

np.save('above_mean.npy', above_mean)
```


<div style="border-bottom: 1px solid gray; margin-bottom: 5px;"></div>

Thank you for reading!

To see the main Python program for Programming Assignment 1, click this \and download. Open on Jupyter Notebook, then run all cells. 

**READ ME file Version History:**

August 31, 2026 - Initial README output uploaded.

















