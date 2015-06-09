#spring 2015


**1**. (20 pts total). We use a "dictionary of sets" to store **equivalences** for the problems below: each value is associated with a **set of all the values** it is equivalent to. For example, let us define an **equivalence of birthdays**. If people named **'a'**, **'b'**, and **'c'** had equivalent birthdays (born on the same day, regardless of the year), and people named 'd', and 'e' had equivalent birthdays, and no one else had the same birthday as 'f', then we could represent this information in the following equivalence dictionary: in it each person's name is a key, and each key is associated with the set of names of people who have the same birthday (are equivalent).
```python
ed = {'a':{'a','b','c'}, 'b':{'a','b','c'}, 'c':{'a','b','c'}, 'd':{'d','e'}, 
'e':{'d','e'}, 'f':{'f'}}
```

**1a**. (4 pts) Define a function equiv that takes three arguments: an equivalence dictionary and two strings (names); itreturns True whenever the two names are equivalent, otherwise False: equiv(ed,’a’,’b’) returns True. 
  
**1b**. (8 pts) Define a function ranking that takes one argument that is a single equivalence dictionary (see above): this function returns a list of only the names (keys) in this dictionary, ordered by decreasing equivalence size, and should omit anyone who is equivalent only to themself; there is no requirement for the order of two names who have the same number equivalences. For the example above, the return list could be ['a','b','c','d','e'] or ['b','a','c','e','d'] but not ['b','a','e','c','d'] because here 'e' comes before 'c' but 'c' is equivalent to 3 others while 'e' is equivalent to only 2 others.

**1c**. (8 pts) Define a function count that takes one argument: an equivalence dictionary; it returns an int: the different number of equivalences. For the equivalence dictionary above, it returns 3 (one equivalence for 'a', 'b', and 'c'; one for 'd' and 'e'; and one for just- 'f'). Be carefully about what can be legally put in Python data structures that you might want to use

--

**2**. (9 pts) In the **Match**? column in the table below, state whether the Regular Expression (RE) pattern string "^(x+[i-n])?(aa)*$"matches each of the following test strings (write True or False): for those with the Match? column showing True, show the groups produced by the match.

| Test        	| Match?     | Match? group 0	| Match? group 1| Match? group 2 	|
| ------------- |:----------:| :----------------|:--------------|:------------------|
| "aa"      	| 			 | 					|				|					|
| "xiaaa"       |		     |   				|				|					|
| "jaaaa"       | 	      	 |    				|				|					|
| "xxj"			|			 |					|				|					|
| "xxjaaaa"		|			 |					|				|					|
| "xxijkaa"		|			 |					|				|					|

**2b**. (3 pts) Write **code** equivalent to the statement **x = re.match(pattern,text)** using the **re.compile function**.


**2c**. (3 pts) Explain when/why is it useful to call the **re.compile** function.

--

**3**.(15 pts) A modular number is written like v mod m, where v < m: if v ≥ m we replace v by v%m (the remainder of v divided by m, guaranteeing v < m). So 13 mod 5 reduces to 3 mod 5 (because 13%5 is 3).
The following class starts to define a Modular from two ints: v(alue) and m(odulus). For example, we can define a = Modular(13,5) which represents 3 mod 5; and b = Modular(1,5) which represents 1 mod 5. In this problem, assume that all modular numbers have a positive value and modulus.
In the class below, write the method called by the repr function and overload the addition operator (so that we can compute a+b and a+2 and 2+a: note that addition is commutative). Adding two modular numbers results in a modular number, but only if the operands have the same modulus: the resulting modular number has that modulus, and its value is the sum off the values of its operands. Adding a modular number and an integer results in a modular number with the modular number’s modulus and a value that is the sum of the modular number’s value and the integer. So a+b is 4 mod 5 and a+2 is 5 mod 5 which __init__ reduces to 0 mod 5.
If we try to add two modular numbers with different moduli (the plural of modulus) raise an **AssertionError** exception; if we try to add a modular number to any other type, raise the **TypeError** exception.

--

**4**. (15 pts) Write a Stock class whose constructor (written below) takes an argument that is a list of dicts . Each dict represents the stock available at one warehouse: it stores keys that are str (item names) whose associated values are int (the number of items in stock in that warehouse: always ≥ 0).
For example, **TJ = Stock( [ dict(apples=2,bananas=3), dict(apples=1,bananas=2,carrots=3) ] )** represents the stock in two warehouses. Warehouses are numbered starting at 1: warehouse 1 stocks 2 apples and 3 bananas; warehouse 2 stocks 1 apples, 2 bananas, and 3 carrots.

  * Define the **\__getitem__** method for Stock so that (given the warehouses above) TJ[1] would return the first dictionary and TJ[2] would returns the second dictionary. Note that when called with any other int values (e.g., TJ[0] or TJ[3]) it returns an empty dictionary; when called with any non-int values (e.g., TJ['a']) it raise the TypeError exception with an appropriate message.

  * Define the **\__call__** method for Stock so that (given the example above) TJ('apples') returns 3: the total number of apples in all the warehouses. Return 0 for any argument that is not a key in any warehouse dictionary(e.g.,TJ('sugar')or TJ(3)).Anitemmaybeinawarehousedictassociatedwith0.

  * Define the **\__contains__** method for Stock so that it returns a boolean value that determines whether or not the second argument is a key in any (one or more) of the warehouse dictionaries, even if associated with 0.

--

**5**. (5 pts) Write the times iterator decorator as a generator: its has two parameters: the first (iterable) and second (counts) are both iterable, with counts guaranteed to produce only non-negative integers; times produces value produced from iterable the number of times specified by the values produced from counts. For example times('abc',[1,3,2]) produces 'a', 'b', 'b', 'b', 'c', and 'c'.
If iterable and counts produce a different number of values, times should stop producing values when either parameter stops. So, times('abcdef',[1,3,2]) produces only 'a', 'b', 'b', 'b', 'c', and 'c' because the second argument has only 3 values (while the first argument has 6).
In your code, use only for loops; you may not call iter in this code. You may call other Python functions.

**5b**. (10 pts) Write the times iterator decorator as above, with one important difference: it stops producing values only when iterable stops; if counts stops producing values, then the values produced by iterable are produced just once. So, times('abcdef',[1,3,2]) now produces 'a', 'b', 'b', 'b', 'c', 'c', 'd', 'e', and 'f' because counts runs out of values to produce when iterable produces 'd', 'e', and 'f' (so each is produced once).
In the code you write, build on your solution above, but here you may call iter: you will need to sense and control a raised StopIteration exception.

--

**6a**. (9 pts) Define a recursive function named join_subst that takes three arguments: a list of str, and two str: it returns a str that is the concatenation of all the strs in the list, but with the second/new str substituted for the first/old str everywhere it appears. So, **join_subst ( ['a','b','a','a','c'], 'a', 'x')** returns **'xbxxc'**, substituting **'x'** for **'a'** and concatenating all these strings together.

**6b**. (6 pts) Define the same join_subst function defined above, but this time in it body use calls to the map and reduce functionals, with the appropriate lambdas.

--

**7**. (12 pts total) Suppose that we defined a Fraction class in which all the arithmetic and relational operators (all the double underscore methods) work correctly if one operand is a Fraction and the other operand is either a Fraction or an int. Also suppose that we have defined f = Fraction(2,3).
Illustrate how Python computes the expression 1 < f by showing the steps it takes: each step is a method call it makes by (a) translating this expression into a method call equivalent, by (b) using the Fundamental Equation of Object Oriented Programming, by (c) simplification, and by (d) failing/succeeding to compute the correct answer.
Hints: Write each method call on a line to the right; I have supplied more than enough lines to illustrate the computation (so you can leave some blank). I used some of the steps mentioned in the previous paragraph multiple times.
