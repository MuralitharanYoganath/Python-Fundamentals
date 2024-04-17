# Advanced Python

## Table of content

- [Introduction Advanced Python](#introduction-advanced-python)

    - [comprehension](#comprehension)
    - [Generator Functions](#generator-functions)
        - [Yield keyword](#yield-keyword)
    - [Decorators](#Decorators)
    - [Context Managers](#context-managers)
    - [Unpacking](#Unpacking)
    - [Namedtuple](#namedtuple)
## Introduction Advanced Python

Advanced Python helps you take your Python skills to the next level with in-depth tutorials on advanced topics like concurrency, metaprogramming, optimization, testing, and deploying production applications. Master advanced Python features and learn professional coding best practices.

### comprehension

Comprehensions are a concise way to create new sequences (such as lists, sets, and dictionaries) from existing sequences. Python 
supports four types of comprehensions:

 - **List comprehensions:** are used to create new lists from existing lists.

 - **Set comprehensions:** are used to create new sets from existing sets.

- **Dictionary comprehensions:** are used to create new dictionaries from existing dictionaries.

- **Generator comprehensions:** are used to create new generators from existing generators.

**Here is an example of a list comprehension:**

```Python
new_list = [x * 2 for x in range(10)]
```
This code creates a `new list` called new_list that contains the squares of the numbers from 0 to 9. The expression `x * 2` is evaluated for each item in the `range(10)` iterable, and the results are added to the new list.

**Here is an example of a set comprehension:**

```Python
new_set = {x for x in range(10) if x % 2 == 0}
```
This code creates a new set called `new_set` that contains the even numbers from 0 to 9. The expression `x % 2 == 0` is evaluated for each item in the `range(10)` iterable, and only the items that evaluate to True are added to the new set.

**Here is an example of a dictionary comprehension:**

```Python
new_dict = {x: x * 2 for x in range(10)}
```

This code creates a new dictionary called `new_dict` that maps the numbers from 0 to 9 to their squares. The expression `x * 2` is evaluated for each item in the `range(10)` iterable, and the results are added to the new dictionary as key-value pairs.

**Here is an example of a generator comprehension:**

```Python
new_generator = (x * 2 for x in range(10))
```
This code creates a new generator called `new_generator` that yields the squares of the numbers from 0 to 9. The expression `x * 2` is evaluated for each item in the `range(10)` iterable, and the results are yielded by the generator.

Comprehensions can be a powerful tool for creating new sequences from existing sequences. They can be used to filter, transform, and map data in a concise and efficient way.

Example Program 
```python
# Python program to demonstrate list comprehension in Python 

# below list contains square of all odd numbers from 
# range 1 to 10 
odd_square = [x ** 2 for x in range(1, 11) if x % 2 == 1] 
print (odd_square) 

# for understanding, above generation is same as, 
odd_square = [] 
for x in range(1, 11): 
	if x % 2 == 1: 
		odd_square.append(x**2) 
print (odd_square) 

# below list contains power of 2 from 1 to 8 
power_of_2 = [2 ** x for x in range(1, 9)] 
print (power_of_2)
#range 1 to 10
lst=[x**2 if x%2==1 else x*2 for x in range(1,11)]
print(lst)

#for understanding ,above "lst" is same as below "lst1"
lst1=[]
for x in range(1,11):
if x%2==1:
	lst1.append(x**2)
else:
	lst1.append(x*2)
print(lst1)
# below list contains prime and non-prime in range 1 to 50 
noprimes = [j for i in range(2, 8) for j in range(i*2, 50, i)] 
primes = [x for x in range(2, 50) if x not in noprimes] 
print (primes) 

# list for lowering the characters 
print ([x.lower() for x in ["A","B","C"]] ) 

# list which extracts number 
string = "my phone number is : 11122 !!"

print("\nExtracted digits") 
numbers = [x for x in string if x.isdigit()] 
print (numbers) 

# A list of list for multiplication table 
a = 5
table = [[a, b, a * b] for b in range(1, 11)] 

print("\nMultiplication Table") 
for i in table: 
	print (i)
```
Output
```python
[1, 9, 25, 49, 81]
[1, 9, 25, 49, 81]
[2, 4, 8, 16, 32, 64, 128, 256]
[2, 3, 5, 7, 11, 13, 17, 19, 23, 29, 31, 37, 41, 43, 47]
['a', 'b', 'c']

Extracted digits
['1', '1', '1', '2', '2']

Multiplication Table
[5, 1, 5]
[5, 2, 10]
[5, 3, 15]
[5, 4, 20]
[5, 5, 25]
[5, 6, 30]
[5, 7, 35]
[5, 8, 40]
[5, 9, 45]
[5, 10, 50]
```
After getting the list, we can get a part of it using python’s slicing operator which has the following syntax: 

    [start : stop : steps]  

    which means that slicing will start from index start
    will go up to stop in step of steps. 
    Default value of start is 0, stop is last index of list
    and for step it is 1 

So [: stop] will slice list from starting till stop index and [start : ] will slice list from start index till end Negative value of steps shows right to left traversal instead of left to right traversal that is why [: : -1] prints list in reverse order.

Example Program
```python
# Let us first create a list to demonstrate slicing 
# lst contains all number from 1 to 10 
lst =list(range(1, 11)) 
print (lst) 
	
# below list has numbers from 2 to 5 
lst1_5 = lst[1 : 5] 
print (lst1_5) 
	
# below list has numbers from 6 to 8 
lst5_8 = lst[5 : 8] 
print (lst5_8) 
	
# below list has numbers from 2 to 10 
lst1_ = lst[1 : ] 
print (lst1_) 
	
# below list has numbers from 1 to 5 
lst_5 = lst[: 5] 
print (lst_5) 
	
# below list has numbers from 2 to 8 in step 2 
lst1_8_2 = lst[1 : 8 : 2] 
print (lst1_8_2) 
	
# below list has numbers from 10 to 1 
lst_rev = lst[ : : -1] 
print (lst_rev) 
	
# below list has numbers from 10 to 6 in step 2 
lst_rev_9_5_2 = lst[9 : 4 : -2] 
print (lst_rev_9_5_2)

``` 
Output
```Python
[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
[2, 3, 4, 5]
[6, 7, 8]
[2, 3, 4, 5, 6, 7, 8, 9, 10]
[1, 2, 3, 4, 5]
[2, 4, 6, 8]
[10, 9, 8, 7, 6, 5, 4, 3, 2, 1]
[10, 8, 6]
```
We can use the filter function to filter a list based on some condition provided as a lambda expression as the first argument and list as the second argument, an example of which is shown below :

Example Program
```Python
import functools 

# filtering odd numbers 
lst = filter(lambda x : x % 2 == 1, range(1, 20)) 
print (list(lst)) 
	
# filtering odd square which are divisible by 5 
lst = filter(lambda x : x % 5 == 0, 
	[x ** 2 for x in range(1, 11) if x % 2 == 1]) 
print (list(lst)) 
	
# filtering negative numbers 
lst = filter((lambda x: x < 0), range(-5,5)) 
print (list(lst)) 
	
# implementing max() function, using 
print (functools.reduce(lambda a,b: a if (a > b) else b, [7, 12, 45, 100, 15]))
```

Output
```Python
[1, 3, 5, 7, 9, 11, 13, 15, 17, 19]
[25]
[-5, -4, -3, -2, -1]
100
```

### Generator Functions

 A Python generator function allows you to declare a function that behaves like an iterator, providing a faster and easier way to create iterators. They can be used on an abstract container of data to turn it into an iterable object like lists, dictionaries and strings.

A generator function in Python is defined like a normal function, but whenever it needs to generate a value, it does so with the `yield keyword` rather than return. If the body of a def contains yield, the function automatically becomes a Python generator function. 

**Create a Generator in Python**

In Python, we can create a generator function by simply using the def keyword and the yield keyword. The generator has the following syntax in Python:

    def function_name():
    yield statement 

Example Program

In this example, we will create a simple generator that will yield three integers. Then we will print these integers by using Python for loop.

```python
# A generator function that yields 1 for first time, 
# 2 second time and 3 third time 
def simpleGeneratorFun(): 
	yield 1			
	yield 2			
	yield 3			

# Driver code to check above generator function 
for value in simpleGeneratorFun(): 
	print(value)
```
Output

```Python
1
2
3
```
**Generator Object**

Python Generator functions return a generator object that is iterable, i.e., can be used as an Iterator. Generator objects are used either by calling the next method of the generator object or using the generator object in a “for in” loop.

Example Program

In this example, we will create a simple generator function in Python to generate objects using the next() function.

```Python
# A Python program to demonstrate use of 
# generator object with next() 

# A generator function 
def simpleGeneratorFun(): 
	yield 1
	yield 2
	yield 3

# x is a generator object 
x = simpleGeneratorFun() 

# Iterating over the generator object using next 

# In Python 3, __next__() 
print(next(x)) 
print(next(x)) 
print(next(x))
```

Output
```Python
1
2
3
```

Example Program

In this example, we will create two generators for Fibonacci Numbers, first a simple generator and second generator using a for loop.

```Python
# A simple generator for Fibonacci Numbers 
def fib(limit): 
	
	# Initialize first two Fibonacci Numbers 
	a, b = 0, 1

	# One by one yield next Fibonacci Number 
	while a < limit: 
		yield a 
		a, b = b, a + b 

# Create a generator object 
x = fib(5) 

# Iterating over the generator object using next 
# In Python 3, __next__() 
print(next(x)) 
print(next(x)) 
print(next(x)) 
print(next(x)) 
print(next(x)) 

# Iterating over the generator object using for 
# in loop. 
print("\nUsing for in loop") 
for i in fib(5): 
	print(i)
```
Output
```Python
0
1
1
2
3

Using for in loop
0
1
1
2
3
```
#### **Python Generator Expression**

In Python, generator expression is another way of writing the generator function. It uses the Python list comprehension technique but instead of storing the elements in a list in memory, it creates generator objects.

#### ***Generator Expression Syntax***
The generator expression in Python has the following Syntax:

    (expression for item in iterable)
    
Example:

In this example, we will create a generator object that will print the multiples of 5 between the range of 0 to 5 which are also divisible by 2.

```Python
# generator expression 
generator_exp = (i * 5 for i in range(5) if i%2==0) 
  
for i in generator_exp: 
    print(i)
```
Output:
```Python 
0
10
20
#### yield keyword 
```

### **Yield keyword** 
yield keyword is used to create a generator function. A type of function that is memory efficient and can be used like an iterator object.

In layman terms, the yield keyword will turn any expression that is given with it into a generator object and return it to the caller. Therefore, you must iterate over the generator object if you wish to obtain the values stored there. we will see the **yield python example.**

**Difference between return and yield Python**

The yield keyword in Python is similar to a return statement used for returning values in Python which returns a generator object to the one who calls the function which contains yield, instead of simply returning a value. The main difference between them is, the return statement terminates the execution of the function. Whereas, the yield statement only pauses the execution of the function. Another difference is return statements are never executed. whereas, yield statements are executed when the function resumes its execution.

**Advantages of yield:**

- Using yield keyword is highly memory efficient, since the execution happens only when the caller iterates over the object.

- As the variables states are saved, we can pause and resume from the same point, thus saving time.

**Disadvantages of yield:** 

- Sometimes it becomes hard to understand the flow of code due to multiple times of value return from the function generator.
- Calling of generator functions must be handled properly, else might cause errors in program.

**Example 1: Generator functions and yield Keyword in Python**

Generator functions behave and look just like normal functions, but with one defining characteristic. Instead of returning data, Python generator functions use the yield keyword. Generators’ main benefit is that they automatically create the functions `__iter__()` and next (). Generators offer a very tidy technique to produce data that is enormous or limitless.

```Python 
def fun_generator():
    yield "Hello world!!"
 
obj = fun_generator()
 
print(type(obj))
 
print(next(obj))
print(next(obj))
```
Output 
```Python 
<class 'generator'>
Hello world!!
```
**Example 2: Generating an Infinite Sequence**

Here, we are generating an infinite sequence of numbers with yield, yield returns the number and increments the num by + 1. 

**Note:** Here we can observe that num+=1 is executed after yield but in the case of a return, no execution takes place after the return keyword.
```Python 
def inf_sequence():
    num = 0
    while True:
        yield num
        num += 1
         
for i in inf_sequence():
    print(i, end=" ")
```
Output:
```Python 
0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 25 
26 27 28 29 30 31 32 33 34 35 36 37 38 39 40 41 42 43 44 45 46 47 48 
49 50 51 52 53 54 55 56 57 58 59 60 61 62 63 64 65 66 67 68 69 70 71 
72 73 74 75 76 77 78 79 80 81 82 83 84 85 86 87 88 89 90 91 92 93 94 95 96.......
```

**Example 3: Demonstrating yield working with a list.**

Here, we are extracting the even number from the list.
```Python 
# generator to print even numbers
def print_even(test_list):
    for i in test_list:
        if i % 2 == 0:
            yield i
 
# initializing list
test_list = [1, 4, 5, 6, 7]
 
# printing initial list
print("The original list is : " + str(test_list))
 
# printing even numbers
print("The even numbers in list are : ", end=" ")
for j in print_even(test_list):
    print(j, end=" ")
```
Output: 
```
The original list is : [1, 4, 5, 6, 7]
The even numbers in list are :  4 6 
```

**Example 4: Use of yield Keyword as Boolean**

The possible practical application is that when handling the last amount of data and searching particulars from it, yield can be used as we don’t need to look up again from start and hence would save time. There can possibly be many applications of yield depending upon the use cases. 
```Python 
# func to count number of given word
def print_even(test_string):
    for i in test_string:
        if i == "geeks":
            yield i
 
 
# initializing string
test_string = " There are many geeks around you, \
              geeks are known for teaching other geeks"
 
# count numbers of geeks used in string
count = 0
print("The number of geeks in string is : ", end="")
test_string = test_string.split()
 
for j in print_even(test_string):
    count = count + 1
 
print(count)
```

Output
```Python 
The number of geeks in string is: 3
```
### Decorators 

Decorators are a very powerful and useful tool in Python since it allows programmers to modify the behaviour of a function or class. Decorators allow us to wrap another function in order to extend the behaviour of the wrapped function, without permanently modifying it. But before diving deep into decorators let us understand some concepts that will come in handy in learning the decorators.

**Properties of first class functions:**

- A function is an instance of the Object type.
- You can store the function in a variable.
- You can pass the function as a parameter to another function.
- You can return the function from a function.
- You can store them in data structures such as hash tables, lists,...

**Example 1: Treating the functions as objects.** 
```Python
# Python program to illustrate functions 
# can be treated as objects 
def shout(text): 
	return text.upper() 

print(shout('Hello')) 

yell = shout 

print(yell('Hello')) 
```
Output

```Python
HELLO
HELLO
```

**Example 2: Passing the function as an argument**

```Python
# Python program to illustrate functions 
# can be passed as arguments to other functions 
def shout(text): 
	return text.upper() 

def whisper(text): 
	return text.lower() 

def greet(func): 
	# storing the function in a variable 
	greeting = func("""Hi, I am created by a function passed as an argument.""") 
	print (greeting) 

greet(shout) 
greet(whisper) 
```
Output
```Python
HI, I AM CREATED BY A FUNCTION PASSED AS AN ARGUMENT.
hi, i am created by a function passed as an argument.
```
**Example 3: Returning functions from another function.**

```Python
# Python program to illustrate functions 
# Functions can return another function 

def create_adder(x): 
	def adder(y): 
		return x+y 

	return adder 

add_15 = create_adder(15) 

print(add_15(10)) 
```
Output
```Python
25
```

In the above example, we have created a function inside of another function and then have returned the function created inside.
The above three examples depict the important concepts that are needed to understand decorators. After going through them let us now dive deep into decorators.

##### Decorators
As stated above the decorators are used to modify the behaviour of function or class. In Decorators, functions are taken as the argument into another function and then called inside the wrapper function.

Syntax for Decorator: 
```Python
    @gfg_decorator
    def hello_decorator():
        print("Gfg")

    '''Above code is equivalent to -

    def hello_decorator():
        print("Gfg")
        
    hello_decorator = gfg_decorator(hello_decorator)'''
```
In the above code, gfg_decorator is a callable function, that will add some code on the top of some another callable function, hello_decorator function and return the wrapper function.

**Decorator can modify the behaviour:**

```Python
# defining a decorator
def hello_decorator(func):
 
    # inner1 is a Wrapper function in 
    # which the argument is called
     
    # inner function can access the outer local
    # functions like in this case "func"
    def inner1():
        print("Hello, this is before function execution")
 
        # calling the actual function now
        # inside the wrapper function.
        func()
 
        print("This is after function execution")
         
    return inner1
 
 
# defining a function, to be called inside wrapper
def function_to_be_used():
    print("This is inside the function !!")
 
 
# passing 'function_to_be_used' inside the
# decorator to control its behaviour
function_to_be_used = hello_decorator(function_to_be_used)
 
 
# calling the function
function_to_be_used()
```
Output: 
```Python
Hello, this is before function execution
This is inside the function !!
This is after function execution
```
Let’s see the behaviour of the above code and how it runs step by step when the “function_to_be_used” is called.

![Images](./Images/decorators1.png)

![Images](./Images/decorators2.png)

Let’s jump to another example where we can easily find out the execution time of a function using a decorator.

```Python
# importing libraries
import time
import math

# decorator to calculate duration
# taken by any function.
def calculate_time(func):
	
	# added arguments inside the inner1,
	# if function takes any arguments,
	# can be added like this.
	def inner1(*args, **kwargs):

		# storing time before function execution
		begin = time.time()
		
		func(*args, **kwargs)

		# storing time after function execution
		end = time.time()
		print("Total time taken in : ", func.__name__, end - begin)

	return inner1



# this can be added to any function present,
# in this case to calculate a factorial
@calculate_time
def factorial(num):

	# sleep 2 seconds because it takes very less time
	# so that you can see the actual difference
	time.sleep(2)
	print(math.factorial(num))

# calling the function.
factorial(10)
```
Output
```Python
3628800
Total time taken in :  factorial 2.0061802864074707
```
##### **Chaining Decorators**
In simpler terms chaining decorators means decorating a function with multiple decorators.

Example: 

```Python
# code for testing decorator chaining 
def decor1(func): 
    def inner(): 
        x = func() 
        return x * x 
    return inner 
 
def decor(func): 
    def inner(): 
        x = func() 
        return 2 * x 
    return inner 
 
@decor1
@decor
def num(): 
    return 10
 
@decor
@decor1
def num2():
    return 10
   
print(num()) 
print(num2())
```
Output
```python
400
200
```
The above example is similar to calling the function as –

```
    decor1(decor(num))
    decor(decor1(num2))
```

### Context Managers 

A context manager in Python is an object that defines a runtime context. The with statement is used to temporarily enter that context and then automatically exit it when the block of code inside the statement has finished executing.

Context managers are useful for ensuring that resources are properly cleaned up, even if an exception is raised. For example, a context manager can be used to open a file, and then ensure that the file is closed even if an exception is raised inside the with statement.

To create a context manager, you need to define a class with two methods: __enter__() and __exit__(). The __enter__() method is called when the with statement enters the context, and the __exit__() method is called when the with statement exits the context.

**Here is an example of a simple context manager:**

```Python
class FileManager:
    def __init__(self, filename):
        self.filename = filename
        self.file = None

    def __enter__(self):
        self.file = open(self.filename, "r")
        return self.file

    def __exit__(self, exc_type, exc_value, exc_traceback):
        self.file.close()

with FileManager("myfile.txt") as f:
    # Do something with the file
    pass
```
In this example, the FileManager class defines a context manager for opening a file. The __enter__() method opens the file and returns it to the with statement. The __exit__() method closes the file.

When the with statement enters the context, the __enter__() method is called and the file is opened. The with statement then executes the block of code inside the statement. When the block of code finishes executing, the __exit__() method is called and the file is closed.

Context managers can be used to manage any kind of resource, not just files. For example, you could use a context manager to open a database connection, or to start a network connection.

Context managers are a powerful tool that can help you to write cleaner and more reliable code.

### Unpacking

Unpacking in Python is a feature that allows you to assign multiple values to multiple variables at once. This can be done using the asterisk () and double asterisk (*) operators.

The asterisk (*) operator is used to unpack sequences, such as lists and tuples. For example, the following code unpacks the list `[1, 2, 3]` into the variables `a`, `b`, and `c`:

```python
a, b, c = [1, 2, 3]
```
The double asterisk (**) operator is used to unpack dictionaries. For example, the following code unpacks the dictionary `{'a': 1, 'b': 2, 'c': 3}` into the variables `a`, `b`, and `c`:

```python
a, b, c = {'a': 1, 'b': 2, 'c': 3}
```
Unpacking can be used to make code more concise and readable. For example, the following code unpacks the list `[1, 2, 3]` and then prints the values of `a`, `b`, and `c`:

```Python
a, b, c = [1, 2, 3]
print(a)
print(b)
print(c)
```
Output
```Python
1
2
3
```
**This code is equivalent to the following code:**
```Python
a = [1, 2, 3][0]
b = [1, 2, 3][1]
c = [1, 2, 3][2]
print(a)
print(b)
print(c)
```
**However, the first code is more concise and readable.**

Unpacking can also be used to assign multiple values to a single variable. For example, the following code unpacks the list `[1, 2, 3]` and assigns the values to the variable `values`:
```Python
values = [1, 2, 3]
```
**This code is equivalent to the following code:**
```Python
values = []
values.append([1, 2, 3][0])
values.append([1, 2, 3][1])
values.append([1, 2, 3][2])
```
**However, the first code is more concise and readable.**

Unpacking is a powerful feature that can be used to make code more concise and readable. It is a good idea to learn how to use unpacking to improve your Python code.

### Namedtuple

Python supports a type of container dictionary called “namedtuple()” present in the module “collections“. In this article, we are going to see how to Create a NameTuple and operations on NamedTuple.


**Python NamedTuple Syntax**
```Python
    namedtuple(typename, field_names)

    typename – The name of the namedtuple.
    field_names – The list of attributes stored in the namedtuple.
```
**Example: Code implementation of NamedTuple is shown in Python.**
```Python
# Python code to demonstrate namedtuple()
from collections import namedtuple

# Declaring namedtuple()
Student = namedtuple('Student', ['name', 'age', 'DOB'])

# Adding values
S = Student('Nandini', '19', '2541997')

# Access using index
print("The Student age using index is : ", end="")
print(S[1])

# Access using name
print("The Student name using keyname is : ", end="")
print(S.name)
```
Output
```python
The Student age using index is : 19
The Student name using keyname is : Nandini
```
**Operations on NamedTuple**

Below are the following operations that can done by using namedtuple():

- Create a NameTuple
- Access Operations
- Conversion Operations
- Additional Operations

**Create a NameTuple in Python**

This creates a new namedtuple class using the namedtuple() function from the collections module. The first argument is the name of the new class, and the second argument is a list of field names.

```Python
from collections import namedtuple

Point = namedtuple('Point', ['x', 'y'])
p = Point(x=1, y=2)
print(p.x, p.y) 
```
Output

```Python
1 2
```

**Access Operations**

Namedtuples in Python provide convenient ways to access their fields. Below are some access operations provided in Python for NamedTuple:

Access by index
Access by keyname
Access Using getattr()
Access By Index
The attribute values of namedtuple() are ordered and can be accessed using the index number unlike dictionaries which are not accessible by index. In this example, we are accessing the student’s by using index.


# importing "collections" for namedtuple()
import collections

# Declaring namedtuple()
Student = collections.namedtuple('Student', ['name', 'age', 'DOB'])

# Adding values
S = Student('Nandini', '19', '2541997')

# Access using index
print("The Student age using index is : ", end="")
print(S[1])

Output
The Student age using index is : 19
Access by keyname
Access by keyname is also allowed as in dictionaries. In this example, we are using keyname to access the student’s name.


# importing "collections" for namedtuple()
import collections

# Declaring namedtuple()
Student = collections.namedtuple('Student', ['name', 'age', 'DOB'])

# Adding values
S = Student('Nandini', '19', '2541997')

# Access using name
print("The Student name using keyname is : ", end="")
print(S.name)

Output
The Student name using keyname is : Nandini
Access Using getattr()
This is yet another way to access the value by giving namedtuple and key value as its argument. In this example, we are using getattr() to access the student’s id in the given namedtuple.


# importing "collections" for namedtuple()
import collections

# Declaring namedtuple()
Student = collections.namedtuple('Student', ['name', 'age', 'DOB'])

# Adding values
S = Student('Nandini', '19', '2541997')

# Access using getattr()
print("The Student DOB using getattr() is : ", end="")
print(getattr(S, 'DOB'))

Output
The Student DOB using getattr() is : 2541997
Conversion Operations
Namedtuples provide a few useful conversion operations to work with other data types in Python. Below are the following conversion operations that is provided for namedtuples in Python:

Using _make()
Using _asdict()
Using “**” (double star) operator
Conversion Using _make()
This function is used to return a namedtuple() from the iterable passed as argument. In this example, we are using _make() to convert the list “li” into namedtuple.


# importing "collections" for namedtuple()
import collections

# Declaring namedtuple()
Student = collections.namedtuple('Student',
                                 ['name', 'age', 'DOB'])

# Adding values
S = Student('Nandini', '19', '2541997')

# initializing iterable
li = ['Manjeet', '19', '411997']

di = {'name': "Nikhil", 'age': 19, 'DOB': '1391997'}

# using _make() to return namedtuple()
print("The namedtuple instance using iterable is  : ")
print(Student._make(li))

Output
The namedtuple instance using iterable is  : 
Student(name='Manjeet', age='19', DOB='411997')
Conversion Operation Using _asdict()
This function returns the OrderedDict() as constructed from the mapped values of namedtuple(). In this example, we are using _asdict() to convert the input list into namedtuple instance.


import collections
# Declaring namedtuple()
Student = collections.namedtuple('Student',
                                 ['name', 'age', 'DOB'])

# Adding values
S = Student('Nandini', '19', '2541997')

# initializing iterable
li = ['Manjeet', '19', '411997']

# initializing dict
di = {'name': "Nikhil", 'age': 19, 'DOB': '1391997'}

# using _asdict() to return an OrderedDict()
print("The OrderedDict instance using namedtuple is  : ")
print(S._asdict())

Output
The OrderedDict instance using namedtuple is  : 
OrderedDict([('name', 'Nandini'), ('age', '19'), ('DOB', '2541997')])
Using “**” (double star) operator
This function is used to convert a dictionary into the namedtuple(). In this example, we are using “**” to convert the input list into namedtuple.


import collections

# Declaring namedtuple()
Student = collections.namedtuple('Student',
                                 ['name', 'age', 'DOB'])

# Adding values
S = Student('Nandini', '19', '2541997')

# initializing iterable
li = ['Manjeet', '19', '411997']

# initializing dict
di = {'name': "Nikhil", 'age': 19, 'DOB': '1391997'}

# using ** operator to return namedtuple from dictionary
print("The namedtuple instance from dict is  : ")
print(Student(**di))

Output
The namedtuple instance from dict is  : 
Student(name='Nikhil', age=19, DOB='1391997')
Additional Operations 
There are some additional operations that are provided in Python for NamedTuples:

_fields
_replace()
__new__()
__getnewargs__()
_fields
This data attribute is used to get all the keynames of the namespace declared. In this example, we are using _fields to get all the keynames of the namespace declared.


import collections
Student = collections.namedtuple('Student', ['name', 'age', 'DOB'])

# Adding values
S = Student('Nandini', '19', '2541997')

# using _fields to display all the keynames of namedtuple()
print("All the fields of students are : ")
print(S._fields)

Output
All the fields of students are : 
('name', 'age', 'DOB')
_replace()
_replace() is like str.replace() but targets named fields( does not modify the original values). In this example, we are using _replace() to replace a name from “Nandini” to “Manjeet”.


import collections

# Declaring namedtuple()
Student = collections.namedtuple('Student', 
                           ['name', 'age', 'DOB'])

# Adding values
S = Student('Nandini', '19', '2541997')

# ._replace returns a new namedtuple, 
# it does not modify the original
print("returns a new namedtuple : ")
print(S._replace(name='Manjeet'))

Output
returns a new namedtuple : 
Student(name='Manjeet', age='19', DOB='2541997')
__new__()
This function returns a new instance of the Student class, by taking the values that we want to assign to the keys in the named tuple. In this example, we are using __new__() to return a new instance of the Student class.


import collections

# Declaring namedtuple()
Student = collections.namedtuple('Student', ['name', 'age', 'DOB'])

# Adding values
S = Student('Nandini', '19', '2541997')

# Student.__new__ returns a new instance of Student(name,age,DOB)
print(Student.__new__(Student,'Himesh','19','26082003'))

Output
Student(name='Himesh', age='19', DOB='26082003')
__getnewargs__()
This function returns the named tuple as a plain tuple. In this example, we are doing the same by using __getnewargs__().


import collections

# Declaring namedtuple()
Student = collections.namedtuple('Student', ['name', 'age', 'DOB'])

# Adding values
S = Student('Nandini', '19', '2541997')

H=Student('Himesh','19','26082003')
# .__getnewargs__ returns the named tuple as a plain tuple
print(H.__getnewargs__())

Output
('Himesh', '19', '26082003')

### Cool Down




