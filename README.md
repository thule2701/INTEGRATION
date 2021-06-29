# NUMERICAL INTEGRATION
## Integrate the equation of sin x from 0 to pi

```python
# Numerical Integration
# Author: Tran-Anh-Thu,Le (26864)
# Rhein-Waal University of Applied Science

# importing the modules
from scipy import random
import numpy as np
import matplotlib.pyplot as plt

# limits of integration
a = 0
b = np.pi # gets the value of pi
N = 1000

# function to calculate the sin of a particular
# value of x
def f(x):
	return np.sin(x)

# list to store all the values for plotting
plt_vals = []

# we iterate through all the values to generate
# multiple results and show whose intensity is
# the most.
for i in range(N):

	#array of zeros of length N
	ar = np.zeros(N)

	# iterating over each Value of ar and filling it
	# with a randome value between the limits a and b
	for i in range (len(ar)):
		ar[i] = random.uniform(a,b)

	# variable to store sum of the functions of different
	# values of x
	integral = 0.0

	# iterates and sums up values of different functions
	# of x
	for i in ar:
		integral += f(i)

	# we get the answer by the formula derived abobe
	ans = (b-a)/float(N)*integral

	# appends the solution to a list for plotting the graph
	plt_vals.append(ans)

# details of the plot to be generated
# sets the title of the plot
plt.title("Distributions of areas calculated")

# 3 parameters (array on which histogram needs
plt.hist (plt_vals, bins=30, ec="black")

# to be made, bins, seperators colour between the
# beams)
# sets the label of the x-axis of the plot
plt.xlabel("Areas")
plt.show() # shows the plot
```

## Monte Carlo method
Integrate the equation of x^2 from 0 to 1
```python
# importing the modules
from scipy import random
import numpy as np

# limits of integration
a = 0
b = 1
N = 1000

# array of zeros of length N
ar = np.zeros(N)

# iterating over each Value of ar and filling
# it with a random value between the limits a
# and b
for i in range(len(ar)):
	ar[i] = random.uniform(a, b)

# variable to store sum of the functions of
# different values of x
integral = 0.0

# function to calculate the sin of a particular
# value of x
def f(x):
	return x**2

# iterates and sums up values of different
# functions of x
for i in ar:
	integral += f(i)

# we get the answer by the formula derived adobe
ans = (b-a)/float(N)*integral

# prints the solution
print("The value calculated by monte carlo integration is {}.".format(ans))
```
## Trapezoid Rule
```python
import numpy as np
from scipy.constants import pi
def f(x): return x**3
def f1(x):
return np.exp(-x**2)
def trapezoid(f,a,b,n=100):
x = np.linspace(a,b,n+1)
y = f(x)
h = (b - a)/n
return h/2 * np.sum(y[1:] + y[:-1])
# y[1:]     # right endpoints
# y[:-1]    # left endpoints
print(trapezoid(f,0,5))
print(trapezoid(f1,-10,10)-np.sqrt(pi))
