---
{"dg-publish":true,"permalink":"/tips/computer-and-programming/python-quiz/","dgHomeLink":true,"dgPassFrontmatter":false}
---


# Python quiz
updated: 2022-09-28


# What's wrong 🤔?

## Quiz 1

```python
array = [{}] * 3

for i in range(3):
	array[i][f"{i}"] = i
	
print(array)
```

Opartor `*`  is useful to specify the size of list and filled with a value. But this operaor creates a `view` if the element is mutable, like `dict` and `list`. This means that `array[0]` and `array[1]` are pointers referencing the same object, so that manipulating `array[0]` changes  `array[1]`. 


