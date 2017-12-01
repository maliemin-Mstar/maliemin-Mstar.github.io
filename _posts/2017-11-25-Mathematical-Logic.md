---
layout: post
title: Mathematical Logic
---
# What is logic

Logic has been used for thousands of years, from philosophy to mathematics and now to artificial intelligence.
Logic is concerned with the truth and falsity of statements. The logic we will be studying will be answering the question: "when does a statement follow from a set of statements?"

## Note to the reader

I have previously written about logic [here](https://medium.com/brandons-computer-science-notes/knowledge-representation-and-reasoning-c7d441049715) and therefore this article will be relatively short when it comes to explaining *everything* about logic. If you want to understand logic, please read the article I have written on logic. This is just an expansion on what we have learned.

## Propositional logic
Propositions can only be true or false.

## Intrepetations
An intrepretation assigns to a propositional statement a truth value of True or False.
True or False can be represented as 0 and 1 respectively.

## Propositional symbols

There are about 500,000 ways to represent logic symbols so here are the most common ways

## Not

**Symbol in logic**

¬ or ! or ~

**Symbol in Electronics**

![Not gate](https://www.electronicshub.org/wp-content/uploads/2015/06/13.jpg)

**What does it do**

Inverts what is ever inputted into it.

**Truth Table**

A | Not A
--- | ---
0 | = 1
1 | = 0

## Conjunction or and

**Symbol in logic**

^ or AND or ,

**Symbol in Electronics**

![And gate](https://www.electronicshub.org/wp-content/uploads/2015/08/1..AND-Symbol.jpg)

**What it does**

Takes >1 inputs and if both inputs are true, outputs true. 

**Truth table**

A | B | A and B
--- | --- | ---
1 | 1 | = 1
1 | 0 | = 0
0 | 1 | = 0
0 | 0 | = 0


## Disjunction, "or"

**Symbol in Logic**

V, or, "OR"

**Symbol in Electronics**

![OR gate](https://www.electronicshub.org/wp-content/uploads/2015/06/or-gate-logic-symbol.jpg)

**What it does**

Takes > 1 inputs, if any of the inputs are true than the output is true.

**Truth Table**

A | B | A or B
--- | --- | ---
1 | 1 | = 1
0 | 1 | = 1
1 | 0 | = 1
0 | 0 | = 0


## Equivilance

**Symbol in Logic**
<=> or ≡

**Symbol in Electronics**
None, this is a concept not a gate.

**What it does**
A and B must take the same truth value

**Truth Table**

A | B | A <=> B
--- | --- | ---
1 | 1 | = 1
0 | 1 | = 0
1 | 0 | = 0
0 | 0 | = 1

## Implication

**Symbol in Logic**
=> or "if a then b"

**Symbol in Electronics**
None

**What it does**
If A is true then so is B

**Truth Table**

A | B | A => B
--- | --- | ---
1 | 1 | = 0
1 | 0 | = 0
0 | 0 | = 1
1 | 0 | = 1

## Truth under an interpretation

Given an interpretation, I, we can compute the truth value of any formula P under I. That is, given a version of the formula we can computer the truth value.

if I(P) = 1 then we say that P is true under interpretation I.
if I(P) = 0 then we say that P is false under interpretation I.

## Logical Puzzles

This section may help the reader in understanding logical puzzles.

An island has two kinds of inhabitants, knights, who always tell the truth, and knaves, who always lie.
You go to the island and meet A and B.
A says that "B is a knight"
B says that "The two of us are opposite types"

What are A and B?

So we have 2 options, p: “A is a knight”; and q: “B is a knight”

We have 2 options because one of them needs to be a knight. Either both A and B are knaves, which makes B a knight as it told a truth so it lied or A is a knight and is telling the truth that B is a knight. 

**Options for person A**
p is true, that is the statement "A is a knight" is true. P => Q
p is false, that is the statement "A is a knight" is false. ¬P => ¬Q

**Options for person B**
q is true then q => ¬p
q is false then ¬q => ¬p

Now we simply need to construct a truth table for these values

p | q | ¬p | ¬q | p => q | ¬p => ¬q | q => ¬p | ¬q => ¬p
--- | --- | --- | --- | --- | --- | --- | ---
0 | 0 | 1 | 1 | 1 | 1 | 0 | 0 | 1


TK to finish TODO: finish

## Semantic Conseqeuence



Symbol in logic

Symbol in electronics

What does it do

Truth Table



Not ¬



## Digital Logic Circuits
Modern computers use logic gates to operate. This section will explain logic gates.

## Basic Logic Gates

**AND Gate**

The AND gate takes two inputs and if both inputs are true then the resultant is true.
If A and B are true then output true.

![OR gate](https://sub.allaboutcircuits.com/images/04101.png)

**Truth Table**
A | B | A and B
--- | --- | ---
1 | 1 | = 1
1 | 0 | = 0
0 | 1 | = 0
0 | 0 | = 0

**OR Gate**

The OR Gate takes 2 inputs and if one of them is true then the output is true.
A or B would be true if either A or B is true.

![OR Gate](https://sub.allaboutcircuits.com/images/04131.png)

**Truth Table**

A | B | A or B
--- | --- | ---
1 | 1 | = 1
1 | 0 | = 1
0 | 1 | = 1
0 | 0 | = 0

**NOT Gate**

The NOT gate, otherwise known as an inverter, inverts the input.
If True is inputted into the NOT gate, then False will come out of it.

![NOT gate](https://i.ytimg.com/vi/DDecqMo3GDQ/hqdefault.jpg)

**Truth Table**

A | Not A
--- | ---
1 | = 0
0 | = 1

## General house keeping rules of making circuits

**Never combine two input wires**

If there are 2 separate inputs, A and B, you cannot combine them into one single wire. 

**A single input wire can be split partway and used as input for two seperate gates**

If you have a single input, A, it can be split into 2 separate wires.

**An output wire can be used as input**

The output of a wire can be used as an input.

**No output of a gate can eventually feed back into that gate**

No gates can loop on themselves.

## Constructing logic circuits from tables

Given a table, such as the one below, how would we construct a logic circuit for it?

![Gates](https://screenshots.firefoxusercontent.com/images/d5eabdec-004b-47bd-a06a-99bf7ec5c6d8.png)

First, work out where it is equal to 1 (true) and then from there formalise it in mathematical logic, from the mathematical logic we can deduce the circuit for it.
Sometimes it is easier to guess directly what logic gates are used.

## Circuit equivalence

two circuits are equivalent if they produce the same output given the same input

## Formula equivalence

2 formula are equivalent if they hold the same truth value under every possible interpretation.

## On Logical Equivalence

The symbol "≡" is used to show an equivalence relation.

**Facts**

≡ is reflexive
≡ is transitive
≡ is symmetric

## Simplfying propositonal formulae

There are some rules we can use to simplfy propositional formulae.

**Communicative Law**

AB = BA, A + B = B + A

Examples:
6 * 2 = 12 and 2 * 6 = 12
3 + 4 = 7 and 4 + 3 = 7

**Assiocative Law**

a(bc) = ab(c) = abc

Examples:
(2 + 4) + 5 = 6 + 5 = 11
2 + (4 + 5) = 2 + 9 = 11

**Distributive Law**

a(b+c) = ab + ac

Example:
3 × (2 + 4) = 3 * 6 = 18
3 × 2 + 3 × 4 = 6 + 12 = 18

**And rules**


A and 0 = 0
A and 1 = 1
A and A = a
A and not a = 0

**Truth Table**
A | B | A and B
--- | --- | ---
1 | 1 | = 1
1 | 0 | = 0
0 | 1 | = 0
0 | 0 | = 0

**Or rules**

A or 0 = A
A or 1 = 1
A or A = A
A or not A = 1

**Truth Table**

A | B | A or B
--- | --- | ---
1 | 1 | = 1
1 | 0 | = 1
0 | 1 | = 1
0 | 0 | = 0

**Not rules**

Sometimes called an inverter

**Miscelanous rules**

Not Not A = A
A or A and B = A
A or not A and B = A and B
(A or B) (A or C) = A or B and C

**What to do next**
From this point, turn the circuit into a logical expression and simplfy it using the rules above.

If this is confusing still, maybe this video will help:
https://www.youtube.com/watch?v=59BbncMjL8I

TK put questions from tutorial here



