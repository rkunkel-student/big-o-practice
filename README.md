# big-o-practice
Big O Examples

Exercises are written in Python.

<br>

## Example 1

```python
def f(array: List[int]):  
	sum: int = 0  
	product: int = 0  
	for i in range(len(array):  
		sum += array[i]  
	for i in range(len(array):  
		product *= array[i]
```

**Time Complexity**

O(n + n) => O(n)

Although we traverse the list twice, we maintain the dominate term n.

**Space Complexity**

O(3n) => O(n)

Although we keep 3 copies of the list, as we approach infinity 3n approaches n.

<br>

## Example 2