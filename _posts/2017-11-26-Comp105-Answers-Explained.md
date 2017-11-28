---
title: "Comp105 Answers Explained"
categories:
  - Comp105
tags:
  - Haskell
  - Functional
---


**Question 1**

Look at the following code:

```Haskell
p n = if n == 0 then 1 else 2 * p(n-1)
```

What is the result of the query p 4?

This is a recursive function, as such it is best for us to walk through it step by step.

```Haskell
2 * (2 * (2 * (2 * (1))))
```

Because of the way the query is set up, it is:

```Haskell
2 * p(n-1)
```

 therefore overtime we times 2 by the result of p(n-1) which will carry on repeating the same function until n == 0 then it will equal to 1. 

This function jut computes 2^n, but it's best to walk through the function yourself.

**Question 2**

What is the most general type annotation for the above code?

We can see the code uses comparison operators, "==". Therefore the type annotation would need the type class Eq and Num since we use the "*" symbol.

An acceptable answer would be

```Haskell 
(Eq a, Num a) => a -> a
```

The ```(Eq a, Num a)``` is a type class and the a's are type variables.

To read more about types, check [here](http://www.learnyouahaskell.com/types-and-typeclasses)

**Question 3**

Look at the following code:

```Haskell
f [] = []
f [x] = [x]
f (x:y:xs) = y : x : f xs
```

What is the result of the query f "abcdef"?

Again, we should run through this code.

```Haskell
Since we know that y and x are the first 2 characters switched we could just do
b : a : f "cdef"
which is
b : a : d : c : f ef
b : a : d : c : f : e
Which is outputted as (thanks to the conns character)
"badcfe"
```

**Question 4**

What is the most general type annotation for f?

Start off by seeing if we need any type classes. Do we compare 2 elements? Do we use addition, multiplication, division or subtraction? No? Then we can make a normal type annotation.

```Haskell
f :: [Char] -> [Char]
```

The above would work, however, it isn't the most _general_ type annotation.

```Haskell
f :: [a] -> [a]
```

And that is the answer.

**Question 5**

What is mutual recursion? Provide an example.

Mutual recursion is when two functions call each other, rather than a single function calling itself. An example would be:

```Haskell
get_evens [] = []
get_evens (x:xs) = x : drop_odds xs

drop_odds [] = []
drop_odds (x:xs) = get_evens xs
```

This is a pair of functions that call eachother. Get_evens returns all the even integers in a list by dropping all the odd ones, and drop_odds drops all the odd numbers by only returning the even numbers

**Question 6** 

What is multiple recursion and give an example?
Multiple recursion is where a function makes more than 1 recursive call in itself.
An example would be the following code to computer the fibbonaci numbers

**Quqestion 7**

A function is considered to be tail recursive if there is nothing left to do once the function has made the recursive call. This is often accomplished by the use of an accumulator in the function arguments. An example would be the following
pair of functions, which compute the factorial

```Haskell
factorial_tail acc 1 = acc
factorial_tail acc n = factorial_tail (acc * n) (n-1)

factorial n = factorial_tail 1 n
 ```



**Question 8**

What is the type of the "." operator?

We know that the "." operator is the function composition operator.
Therefore it combines 2 functions together so...

```(a -> b) -> (c -> b) -> c -> b```

**Question 9**

Consider the following code:

```apply_twice f = f . f```

What does the query apply_twice (+1) 0 do?

It results in 2, as you add +1 to 0 twice.

**Question 10**

What is the type of apply_twice, why?

Apply twice takes a function and applies it twice, so it's first type is

```(a -> a)```

Because its output is fed back into itself as it's input.

Thus the rest of the type declaration is

```Haskell
(a -> a) -> a -> a
```

**Question 11**

What is the type of apply_twice (+1), why?

The type is Num a => a -> a. This is because we are partially applying
apply_twice, by giving it only the first argument. The Num class constraint is
needed, because we are using (+1) as the first argument, and this function has
type Num a => a -> a.

**Question 12**

What are the answers to the following queries?

```Haskell
ghci> map (2^) [1..5]
ghci> map show [1..5]
ghci> map (\x -> show x !! 0) [10..19]
```

Output 1: [2,4,8,16,32]
This is just squaring every number in the range 1..5.

Output 2: ["1","2","3","4","5"]
This just shows the numbers 1 - 5 in character form

Output 3: "1111111111"
The anonymous function pulls out the first character of each
number, which happens to be 1 for every number between 10 and 19.

**Question 13**

What are the answers to the following queries?

```Haskell
ghci> filter even [1..10]
ghci> filter (<5) [1..10]
ghci> filter (\x -> x `mod` 3 == 0 || x `mod` 5 == 0) [1..10]
```

Output 1: [2, 4, 6, 8, 10]

Output 2: [1, 2, 3, 4]

Output 3: [3, 5, 9, 10]
The anonymous function pulls out the numbers that are either
divisible by 3 or by 5.

**Question 14**

What are the answers to the following queries?

```Haskell
ghci> foldr (*) 1 [1,2,3,4]
ghci> foldr (+) 0 [2,4..10]
ghci> foldr (\x acc -> x : acc) [] [1,2,3,4]
ghci> foldr1 (\x acc -> x) [1,2,3,4]
```

Output 1: 24
This just multiplies every number in the list, so it's 1 * 2 * 3 * 4 = 24

Output 2: 30

Output 3: [1, 2, 3, 4]
Foldr takes the list and iterates from the right, applying the element x to the head of the list every time. It may be better to look at it in action

```Haskell
[4] : []
[3] : [4]
[2] : [3, 4]
[1] : [2, 3, 4]
[] : [1, 2, 3, 4]
List is now empty, so output
[1, 2, 3, 4]
```

Note: This would not work with foldl.

Output 4: 1

The function returns the element, x, as the new accumulator. Since foldr1 uses the starting value (in this case, 4) instead of having a manually inputted starting value it just runs through the list from right to left. The last value it touches is 1, therefore the output is 1.

**Question 15**

For each of the queries above, what happens when foldr is replaced with scanr?

Query 1: scanr (*) 1 [1, 2, 3, 4]

In this case, we would just get the list of accumulators. So it would be
[24, 24, 12, 4, 1]
As the program starts with 1, then it does 1 * 4, then 4 * 3, which is 12 and then 12 * 2 which is 24 and then 24 * 1 which is 24 again.

Query 2: scanr (+) 0 [2,4..10]
The list range will output [2, 4, 6, 8, 10]
So scanr will add
0 (as first element is 0 due to it being the accumulator) then
0 + 10 = 10, 10 + 8 = 18, 18 + 6 = 24, 24 + 4 = 28, 28 + 2 = 30.
So the output list is
[30,28,24,18,10,0]

Query 3: scanr (\x acc -> x : acc) [] [1, 2, 3, 4]
[[1,2,3,4],[2,3,4],[3,4],[4],[]]

Query 4: scanr (\x acc -> x) [1,2,3,4]
Output: [1, 2, 3, 4]

**Question 16**

For each of the queries above, what happens when foldr is replaced with foldl? Which of the queries need to be changed and why?

Query 1: foldl (*) 1 [1, 2, 3, 4]

Nothing happens, as the communicative law states that A * B = B * A.

Query 2: foldl (+) 0 [2,4..10]

Again, nothing happens due to the communicative law.

Query 3: foldl (\x acc -> x : acc) [] [1, 2, 3, 4]

The first thing we need to change is the x and acc positions so
foldl (\acc x -> x : acc) [] [1, 2, 3, 4]

Now we just walk through the program

```
[1]
[2, 1]
[3, 2, 1]
[4, 3, 2, 1]
```
Therefore this query now reverses the list

Query 4: foldl (\x acc -> x) [1,2,3,4]

Again, we need to swap x and acc.
foldl (\acc x -> x) [1, 2, 3, 4]

Because it goes from left to right, the last element is then 4.

**Question 17**

What are the types of dropWhile, takeWhile and zipWith?

dropWhile :: (a -> Bool) -> [a] -> [a]

takeWhile :: (a -> Bool) -> [a] -> [a]

zipWith :: (a -> b -> c) -> [a] -> [b] -> [c]

**Question 18**

What does the following query return?  Why?

```Haskell
ghci> (dropWhile (==' ') . dropWhile (/=' ')) "one two three"
```

The second dropwhile removes every character that isn't a space and the first dropwhile removes the space, therefore the result is "two three"

**Question 19**

Consider the following custom type:

```Haskell
data Direction = North | South | East | West deriving (Show, Read, Eq, Ord)
```

What do the four type classes in the deriving clause represent?  Which functions can we now use on the Direction type?

Show - contains all types that can be used as an argument to show
Read - contains all types that can be used as an argument to read
Eq   - contains all types that can be compared with == and /=
Ord  - contains all types that can be compared with <, >, <=, >=.

The above functions can now be used on the type Direction.

**Question 20**

What are the results of the following queries?

```ghci> North < South ```

False, as North comes before South in the list.

```ghci> West < East```

True

```ghci> show North```

Just returns "North" as the default implementation makes it into a string

```ghci> read North :: Direction```

Returns North, the data type.


**Question 21**

Consider the following custom type

```data List a = Empty | Cons a (List a)```

Construct an instance of this type that is equivalent to
[1,2,3]

```Haskell
Cons 1(Cons 2( Cons 3 Empty))
```

John also gives it as

```Haskell
1 `Cons` (2 `Cons` (3 `Cons` Empty))
```

Using infix notation

**Question 22**

Which of these are valid instances of List?

Empty

Empty is a valid instance of List

Cons 1 empty

This is also valid

1 `Cons` (2 `cons empty)

Is also valid and would result in [1, 2]

1 `Cons` (`a` `Cons` Empty)

Is not valid because we are trying to store items of 2 different types and this is not allowed in lists.

**Question 23**

Consider the following code:

```Haskell
data Tree = Leaf | Branch Tree Tree deriving (Show)
g 0 = Leaf
g 1 = Leaf
g n = Branch (g (n-1)) (g (n-2))
depth Leaf = 1
depth (Branch l r) = 1 + max (depth l) (depth r)
```
What is the result of the following query?

```ghci> depth (g 4)```

To solve this I would start by drawing the tree.
So given, let's say, n = 4 we would draw
Branch (Branch (Branch Leaf Leaf) Leaf) (Branch Leaf Leaf)


For this, it is best to look at it from a bottom up point of view.

```Haskell
What is the result of g 2?
g 2 = Branch (g 1) (g 0) = Branch Leaf Leaf
Note: g 0 and g 1 both equal leafs here, as per the base cases.

What is the result of g 3?
It is Branch (g 2) (g 1) and we know that g 2 is equal to Branch Leaf Leaf (as per above) and g 1 is a leaf so it is equal to Branch (Branch Leaf Leaf) Leaf

What is the result of g 4?
It is Branch (g 3) (g 2) and we know that (g 3) = Branch (Branch Leaf Leaf) Leaf and that g 2 is equal to Branch Leaf Leaf so this is equal to Branch (Branch (Branch Leaf Leaf)) (Branch Leaf Leaf)
```

__John's Answer__
>The function g creates the fibonacci tree that we saw in the lectures. Even
>without knowing that, one way to solve the question is to just draw the tree
>created by g, and then execute depth on it.
>
>Actually, depth (g i) will always return i, since the longest branch of the tree
>will always be the branch that follows the g (n-1) recursive call, and this
>branch must have depth i.

**Question 24**

What does the Maybe type do?  Where is it most useful?

This question is simply just understanding types, no useful tricks here other than to learn it.

The Maybe type is used in

```Haskell
Maybe a = Just a | Nothing
```

It is a type used for functions that may fail, typically within IO functions.
If the function can return value x, then it returns Just x, if not then it returns Nothing. 

This is like exceptions in traditional programming, but completely different as exceptions are not functional, although it is still error handling.

**Question 25**

What does the Either type do?  Where is it most useful?

The Either type allows us to output 2 different types in a function, which is not normally allowed.

```Haskell
Either a b = Left a | Right b
```

is the syntax used for the Either type. It can be used, for example, when we want to store two different types in the same list or when we want a function to return two different types.

**Question 26**

What is the IO type? Where is it used?

The IO type is for input and output and it indicates that a function is not purely functional. It is used in the return of all IO (Input / Output) code

**Question 27**

What is the difference between IO code and pure functional code?

Pure function code has no side effects and is deterministic, it does not need error handling because of it being deterministic. An IO function might have side effects and it might return different values for the same input.

**Question 28**

Consider the following code:
```Haskell
action :: IO (Int)
action = do
    x <- return 1
    y <- return 2
    z <- return 3
    return (x + y + z)
```
What is the result of running action?  What is the type of the returned value?

Remember that return makes an IO action out of a pure value.
This is just asking what 1 + 2 + 3 is, which is 6, however since it is an IO action the result is "IO 6". The return type is IO (Int)

**Question 29**

What is the result of the following query?  Why?
```Haskell
ghci> putStrLn (getLine)
```

It errors because the return value of getLine is IO but it must be "unboxed" or made into pure functional instead of IO before it can be passed as input to putStrLn.

**Question 30**

What is the difference between lazy evaluation and strict evaluation?

John put it nicely here:

>In strict evaluation, arguments to a function must be fully evaluated before
>the function itself is evaluated. In lazy evaluation, functions can be applied
>to arguments that are not yet fully evaluated. Lazy evaluation only computes a
>value when it is needed, which sometimes makes evaluation faster. It also allows
>for infinite data objects.

If you're interested in learning more about strict vs lazy evaluation I highly suggest reading this StackOverflow answer https://stackoverflow.com/a/21218505
