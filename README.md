# big-o-practice
Big O Examples

Exercises are written in Python and C++.  
Page is written in markdown / html.  

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
<details>
<summary>Time Complexity</summary>
<p>

O(n + n) => O(n)

Although we traverse the list twice, we maintain the dominate term n.

</p>
</details>

## Example 2

```python
def f(array: List[int]):
	for i in range(len(array)):
		for j in range(len(array)):
			print("%s, %s".format(array[i], array[j])
```

<details>
<summary>Time Complexity</summary>
<p>

O(n * n) => O(n^2)

We traverse the list for every element in the list

</p>
</details>

## Example 3

```python
def f(array: List[int]):
	for i in range(len(array)):
		for j in range(i + 1, len(array)):
			print("%s, %s".format(array[i], array[j])
```

Similar to Example 2, however, the inner loop begins at "i + 1".

<details>
<summary>Time Complexity</summary>
<p>

O(n * n) => O(n^2)

We still traverse the list for every element in the list, and we know to drop constants. 

</p>
</details>

## Example 4

```python
def f(array1: List[int], array2: List[int]):
	for i in range(len(array1)):
		for j in range(len(array2)):
			if array1[i] < array2[j]:
				print("(%s, %s)".format(array1[i], array2[j]))
```

<details>
<summary>Time Complexity</summary>
<p>

O(1 + n * n + 1) => O(n^2)

**But wait!** What if both arrays were not the same size?

In this case the **Time Complexity would be O(nm)**, the reason being the loop is of n * m, not of n * n. 

</p>
</details>

## Example 5

```python
def f(array1: List[int], array2: List[int]):
	for i in range(len(array1)):
		for j in range(len(array2)):
			for k in range(100000):
				print("(%s, %s)".format(array1[i], array2[j]))
```

<details>
<summary>Time Complexity</summary>
<p>

O(n * m * 100000 + 1) ==> O(nm)

This might be looping to 100000, but this is a constant factor which is dropped during Big O calculations leaving us O(nm).

</p>
</details>

## Example 6

```python
def f(array:List[int]) -> None:
	for i in range(len(array)/2):
		other: int = len(array) - i - 1
		temp: int = array[i]
		array[i] = array[other]
		array[other] = temp
```

<details>
<summary>Time Complexity</summary>
<p>

O(n/2 + C) ==> O(n)

Although we only loop over the set halfway, as we approach infinity the difference between n and n/2 become negligible.

</p>
</details>

## Example 7

Which of the following are equivalent to O(n)? Why?

* O(n + p), where p < n/2
* O(2n)
* O(n + log n)
* O(n + m)

<details>
<summary>Time Complexity</summary>
<p>

With only the presented data use the following:

* Yes, If p < n/2, then n is the dominate term and p can be dropped. 
* Yes, Drop constants so O(2n) is also the same as O(n).
* Yes, n is a larger term then log n, so we drop that term.
* Unknown, There is not enough information to determine the relationship between n and m, both terms must be kept.

</p>
</details>

## Example 8

Given an algorithm that takes in an array of strings, sorted each string and then sorted the full array. What would the runtime be?

<details>
<summary>Time Complexity</summary>
<p>

n * log n * n ==> n^2 log n ==> O(n^2)? *Right?*

**WRONG!** 

This assumes that each string is the same length of the array. To prevent this kind of confusion use different terms and define their meaning before hand.

Let 

* s = string length   
* a = array length  

Sorting each string is O(s log s), but we do this for "a" string which makes this O(a * s log s)

Sorting the array takes O(a log a) -- **WAIT!**

Remember that the comparison is of O(s) for each string, meaning the total time is really O(s * a log a) 

(a * s log s) + (s * a log a) ==> O(a * s (log s + log a))

**Correct Time Complexity**

 O(a * s (log s + log a))

 </p>
</details>


## Example 9

Given a balanced binary search tree,
```python
def f(Node node) {
	if node == null:
		return 0;
	return f(node.left) + node.value + f(node.right)
}
```
<details>
<summary>Time Complexity</summary>
<p>

In this example, we know that our tree has an access time of O(log n), however, this code actually demostrates worst case. We're iterating over every node in the tree, not searching for a given instance for a time complexity of O(n).

Remember the pattern, If the algorithm follows "do this for everytime you do that, multiply them.

Simplifying and dropping non-dominate terms,  
O(log n * log n + n)  ==>  O(2^log n) 

Why does O(2^log n) = O(n)?

    Let P = 2^log n 

         -> log P = log N  
         -> P = N

    Therefore N = 2^log n  

We observe the time complexity of O(n).

</p>
</details>

## Example 10

What is the time complexity for this function?

```python
def f(n: int) -> bool:
	x: int = 2
	while (x*x <= n)
		if n % x == 0:
			return False
        x += 1
	return True
```

We can also look at the step x * x as the square root of n.

```python
def f(n: int) -> bool:
	for x in range(2, sqrt(n))
		if n % x == 0:
			return False
	return True
```

<details>
<summary>Time Complexity</summary>
<p>

This easily shows us our function's Big O is O(&Sqrt;n)

</p>
</details>

## Example 11

This function calculates n!, what is it's time complexity

```python
def f(n: int) -> int:
	if n < 0:
		return -1
	elif n == 0:
		return 0
	else:
		return n * factorial(n - 1)
```

<details>
<summary>Time Complexity</summary>
<p>

Given n = 3

    f(3) -> 3 * f(2)
         -> 3 * 2 * f(1)
         -> 3 * 2 * 1 * f(0)
         -> 3 * 2 * 1 * 0

We observe our runtime follows the recursive pattern of n + 1 giving us O(n) after dropping the constant.

</p>
</details>


## Example 12

```python
def permutation(string: str, prefix: str) -> None:
	if len(string) == 0:
		print(prefix)
	else:
		for i in range(len(string)):
			rem: str = string[0:i] + string[i + 1]
			permutation(rem, prefix + string[i]) 
```

<details>
<summary>Time Complexity</summary>
<p>

Let 

* string = "string"
* prefix = "rin"

    f("string", "rin") -> 5 * (4 * (3 * (2 * (1 * (0)))))  
  
In other words, O(n!).

However, we are doing this for the length of our string giving us O(n * n!) as the upper bound.

We can get the total time of this function by remembering the comparison is O(n) for a total time of O(n^2 * n!).

</p>
</details>

## Example 13 

```python
def fib(n: int) -> int:
	if n <= 0:
		return 0
	elif n == 0:
		return 1
	else:
		return fib(n - 1) + fib(n - 2)
```
<details>
<summary>Time Complexity</summary>
<p>

Remembering the pattern O(branches^depth) we know the answer is O(2^n).

</p>
</details>

## Example 14 

```python
def allfib(n: int) -> None:
	for i in range(n):
		print(i + ": " + fib(i))

def fib(n: int) -> int:
	if n <= 0:
		return 0
	elif n == 0:
		return 1
	return fib(n - 1) + fin(n - 2)
```
<details>
<summary>Time Complexity</summary>
<p>

It appears we have the same pattern O(2^n), but consider the function calling fib, this gives us O(n * 2^n). 

*Right*?

**WRONG**.. Well, kind of. 

Consider the following:

| term | output    |
| ---- | --------- |
| f(1) | 2^1 steps |
| f(2) | 2^2 steps | 
| f(3) | 2^3 steps |
| f(4) | 2^4 steps | 

f(n) = 2^n  

Remember as n * 2^n approaches infinity it is the same as 2^n + 1 which simplifies to 2^n. 

Always explain your though process and don't just announce the answer. 

</p>
</details>

## Example 15

In this example, the previous results are cached and if a term has already been computed it returns that. 

```python
def allfib(n: int) -> None:
	memo: List[int] = [0 for i in range(n)]
	for i in range(n):
		print("%d: %d".format(i, fib(i, memo)))

def fib(n: int, memo: List[int]) -> int:
	if n <= 0:
		return 0
	elif n == 0:
		return 1
	elif memo[n] > 0:
		return memo[n]

	memo[n] = fib(n - 1, memo) + fib(n - 2, memo)
	return memo[n]
```
<details>
<summary>Time Complexity</summary>
<p>

Given n = 3

    allfib(3) -> fib(0, [])      -> 1 // O(1) result
              -> fib(1, [])      -> 1 // new result cached

              	-> fib(0, []) + fib(-1, []) // 1 + 0

              -> fib(2, [1])     -> 2 // new result cached

              	-> fib(1, [1]) + fib(0, [1]) // 1 + 1

              -> fib(3, [1, 2])  -> 3 // new result cached
              	
              	-> fib(2, [1, 2]) + fib(1, [1, 2]) // 1 + 2

We see that we are only calculating n results as our lookup becomes O(1). Also consider the time it takes to create the reference list O(n).

O(n + n) simplifies to O(n).

Note that this technique is called "memoization" and is used very commonly to optimized exponential time recursive algorithms.

</p>
</details>

## Example 16

```python
def powerOf2(n: int) -> int:
	if n < 1:
		return 0
	elif n == 1
		print(n)
		return 1
	else:
		prev: int = powerOf2(n / 2)
		curr: int = prev * 2
		print(curr)
		return curr
```
<details>
<summary>Time Complexity</summary>
<p>

Given n = 4

    powerOf2(4) -> powerOf2(2)
    			-> powerOf(1)
    			-> 1

This would print: 1, 2, 4

What would the runtime be of say, 50?

Example: 1, 3, 6, 12, 25, 50

This pattern of reduction, n/2 can be expressed as log n giving is Big O(log n).

</p>
</details>

## Additional Problems

Review the examples above and their patterns before continuing.


<details>
<summary>Exercise 1</summary>
<p>
	
What is the runtime of the following code?
```c++
int product(int a, int b) {
	int sum = 0;
	for (int i = 0; i < b; i++) {
		sum += a;
	}
	return sum;
}
```

<details>
<summary>Answer</summary>
<p>

Let

* a = 1
* b = 5

We iterate b times adding a to a variable that is returned.

Time Complexity: O(n)

</p>
</details>	


</p>
</details>


<details>
<summary>Exercise 2</summary>
<p>

This function computes a^b 	
What is the runtime of the following code?
```c++
int power(int a, int b) {
	if (b < 0) {
		return 0; // error
	}
	else if (b == 0) {
		return 1;
	}
	else {
		return a * power(a, b - 1);
	}
}
```

<details>
<summary>Answer</summary>
<p>

Let

* a = 2
* b = 4

f(2, 4) -> 2 * (2, 3)
		-> 2 * 2 * (2, 2)
		-> 2 * 2 * 2 * (2, 1)
		-> 2 * 2 * 2 * 2 * (2, 0)
		-> 2 * 2 * 2 * 2 * 1

we iterate b + 1 times returning a * result of next iteration

Time Complexity: O(n)

</p>
</details>	


</p>
</details>


<details>
<summary>Exercise 3</summary>
<p>

This function computes a % b
What is the runtime of the following code?
```c++
int mod (int a, int b) {
    if (b <= 0) {
        return -1;
    }
    int div = a / b;
    return a - div * b;
}
```

<details>
<summary>Answer</summary>
<p>

Let

* a = 2
* b = 5

f(2, 5) -> 2 - (2 / 5) * 5

Time Complexity: O(1)

</p>
</details>	


</p>
</details>



<details>
<summary>Exercise 4</summary>
<p>

This function performs integer division, assume both a and b are positive integers.
What is the runtime of the following code?
```c++
int div(int a, int b) {
	int count = 0;
	int sum = b;
	while (sum <= a) {
		sum += b;
		count++;
	}
	return count;
}
```

<details>
<summary>Answer</summary>
<p>

Let 

* a = 9
* b = 5

Expected Result: 1

    f(9, 5) -> while(sum:5 <= a)
			    -> sum = 10
			    -> count = 1
			-> return 1

O(a / b) The reason for this is neither a nor b are related, but dependent on each other.

</p>
</details>	


</p>
</details>
