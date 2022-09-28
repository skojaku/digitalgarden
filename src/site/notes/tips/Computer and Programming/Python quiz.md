---
{"dg-publish":true,"permalink":"/tips/computer-and-programming/python-quiz/","dgHomeLink":true,"dgPassFrontmatter":false}
---


# Python quiz
updated: 2022-09-28


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

