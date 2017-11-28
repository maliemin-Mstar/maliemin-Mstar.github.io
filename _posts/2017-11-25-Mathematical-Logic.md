---
layout: post
title: Mathematical Logic
---
# What is logic

Logic has been used for thousands of years, from philosophy to mathematics and now to artificial intelligence.
Logic is concerned with the truth and falsity of statements. The logic we will be studying will be answering the question: "when does a statement follow from a set of statements?"

## Note to the reader

I have previously written about logic [here](https://medium.com/brandons-computer-science-notes/knowledge-representation-and-reasoning-c7d441049715) and therefore this article will be relatively short when it comes to explaining *everything* about logic. If you want to understand logic, please read the article I have written on logic. This is just an expansion on what we have learned.

## Digital Logic Circuits
Modern computers use logic gates to operate. This section will explain logic gates.

## Basic Logic Gates

**AND Gate**

The AND gate takes two inputs and if both inputs are true then the resultant is true.
If A and B are true then output true.

![OR gate](https://sub.allaboutcircuits.com/images/04101.png)

**OR Gate**

The OR Gate takes 2 inputs and if one of them is true then the output is true.
A or B would be true if either A or B is true.

![OR Gate](https://sub.allaboutcircuits.com/images/04131.png)

**NOT Gate**

The NOT gate, otherwise known as an inverter, inverts the input.
If True is inputted into the NOT gate, then False will come out of it.

![NOT gate](https://i.ytimg.com/vi/DDecqMo3GDQ/hqdefault.jpg)

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

**Assiocative Law**

a(bc) = ab(c) = abc

**Distributive Law**

a(b+c) = ab + ac

**And rules**

A and 0 = 0
A and 1 = 1
A and A = a
A and not a = 0

**Or rules**

A or 0 = A
A or 1 = 1
A or A = A
A or not A = 1

**Miscelanous rules**

Not Not A = A
A or A and B = A
A or not A and B = A and B
(A or B) (A or C) = A or B and C

**What to do next**
From this point, turn the circuit into a logical expression and simplfy it using the rules above.

If this is confusing still, maybe this video will help:
https://www.youtube.com/watch?v=59BbncMjL8I

