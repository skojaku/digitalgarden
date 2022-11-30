---
{"dg-publish":true,"permalink":"/productivity/automation/python-tips/","dgPassFrontmatter":true}
---


# Python tips
updated: 2022-09-28
#tools/python

## Initializing list 

What's wrong with this initialization of list?

```python
array = [{}] * 3

for i in range(3):
	array[i][f"{i}"] = i
	
print(array)
```

Opartor `*`  is useful to specify the size of list filled with a value. But this operaor creates a `view` if the element is mutable, like `dict` and `list`. This means that `array[0]` and `array[1]` are pointers referencing the same object, so that manipulating `array[0]` changes  `array[1]`.

---

## Incrementing numpy array with repeated indices


```python
import numpy as np 
array = np.zeros(5)
indices = np.array([1,1,2,2,3,3,3])
array[indices]+=1 # increment
	
print(array) # [0,1,1,1,0,0] or [0,2,2,3,0,0]?
```

Numpy increment does not double increment the array. 

---

## Uniqify strings

You have a list of person names like this: 
```python
names = ["Elizabeth", "John", "Elizabeth", "Aaron", "John", "John"]
```

Write *one-line code* to assign a unique integer ID for each different person name. You can use numpy or scipy. 

```python 
import numpy as np 
names = ["Elizabeth", "John", "Elizabeth", "Aaron", "John", "John"]
np.unique(names, return_inverse=True)[1]
```

---

## Shuffle Panda's DataFrame

Write a *one line code* to shuffle the rows of pandas's dataframe using pandas. 

```python
df.sample(frac = 1)
```

---
# Slow sampling methods of pandas and numpy

Numpy and pandas offer an easy way to draw a random sample in a set of samples. For instance, 
```python 
numpy.random.choice(data, size = 1)
pandas.DataFrame(data).sample(1)
```
sample one data from `data` (which can be a list or numpy array). 

This is convenient, though, extremely slow, especially when they are executed repeatedly. An easy word around is to sample `index` instead of the data itself:
```python 
index = numpy.random.randint(len(data))
data[index]
```
which is 100x faster (see [here](https://github.com/numpy/numpy/issues/11476))
∏P