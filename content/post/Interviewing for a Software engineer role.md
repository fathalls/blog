---
date: 2020-01-03
linktitle: Interviewing for a software engineer role
title: Interviewing for a software engineer role
summary: Checklist for interviewing at tech companies.
icon: check-box
draft: false
---
this is what I used while interviewing, I am now a SWE @ Spotify, if you are a minority or a womxn and would like a referral, send me an email at hi @ salwa dot dev.

Two main areas

Behavioural

General questions about CV

Situation based

Technical

## Behavioural

Answering the below questions with the framework Situation-Action-Result helps with behavioural questions preparation.

|Question                                                      |Situation|Action|Result|
|--------------------------------------------------------------|---------|------|------|
|Solve problems                                                |         |      |      |
|Face a challenge                                              |         |      |      |
|Make decisions                                                |         |      |      |
|Disagree with others                                          |         |      |      |
|Persuade others                                               |         |      |      |
|Do more than expected                                         |         |      |      |
|Learn something new                                           |         |      |      |
|Help others                                                   |         |      |      |
|Consider the needs of and/or help a customer or dependent team|         |      |      |
|Dive deep into something complex or unknown                   |         |      |      |
|Be inventive                                                  |         |      |      |
|Act quickly                                                   |         |      |      |

[Link to Notion template.](https://www.notion.so/c33c4b18ef9642a6be620a6b2a2c685e)

## Technical

The technical interviews are roughly split into two areas: data structures & algorithms and system design.

### DS & Algorithms

#### LinkedList

- [ ]  Detect cycle - remove cycle (use two pointers technique)
- [ ]  Reverse - Reverse in-place

#### Hash Tables

- [ ]  Implement of HashMap & HashSet

#### Queue & Stack

- [ ]  Implement queue & stack using LinkedList

#### Heap

- [ ]  Implement heap
- [ ]  practice by implementing priority queue

#### N-ary trees and Trie

- [ ]  N-ary tree and Trie implementation (list of children for N-ary tree and an array of the number of alphabet or ASCII characters for Trie)
- [ ]  Insert - delete - lookup implementation for Tree and Trie
- [ ]  Check substring or sub palindrome problems
- [ ]  Implement auto-complete system

#### Binary trees and BST

- [ ]  Implement DS - insert - deletion - lookup - isValid BST
- [ ]  How to balance BT

#### Graphs

- [ ]  Graph implementation  (Matrix, List, Objects & pointers)
- [ ]  DFS (stack) & BFS (queue)
- [ ]  Dijkstra algorithm
- [ ]  A* search
- [ ]  Hamiltonian Cycle
- [ ]  Travelling salesman problem
- [ ]  practice calculating the complexities of above algorithms

#### Sorting

- [ ]  Implement bubble, selection, quick and merge sorts

#### Dynamic programming

- [ ]  Implement Fibonacci in three ways for practice: Iterative, recursive and with dynamic programming

#### Greedy algorithms

- [ ]  Look-up a definition
- [ ]  Practice a problem

#### Bit manip

- [ ]  Play around with the # operations

#### OO Design

- [ ]  Design an elevator
- [ ]  Design a parking lot
- [ ]  Design LRU cache

#### NP-Complete problems

- [ ]  Travelling salesman
- [ ]  Hamiltonian cycle
- [ ]  knacksack problem

## System Design

I follow the steps below to design a system, remember, always start small and simple, and let your interviewer know of your plan:

1. Define the scope of the exercise; this can be done by writing down the use-cases
2. Come up with a simple design - not including any scalability concerns
3. Tweak the design from 2. to support scalability, keep in mind these factors: Availability - Performance - Reliability.

Some useful articles to get started:

[A lecture on scalability](https://www.interviewbit.com/tutorial/scalability-lecture/)

[Useful questions & answers for networking](https://www.softwaretestinghelp.com/networking-interview-questions-2/) 

[Scalability for dummies series](https://www.lecloud.net/tagged/scalability)

[Microservices explained by Martin Fowler](https://martinfowler.com/articles/microservices.html)

[Principles of Web Distributed Systems Design](http://www.aosabook.org/en/distsys.html)

[Microservices series explained by Chris Richardson](https://www.nginx.com/blog/introduction-to-microservices/)

[Some known unit for back-of-the-envelope estimations: Numbers everyone should know](http://highscalability.com/numbers-everyone-should-know)

[How to rock your system design interview by Palantir](http://www.palantir.com/2011/10/how-to-rock-a-systems-design-interview/)

[Case study: Instagram's design](http://highscalability.com/blog/2012/4/9/the-instagram-architecture-facebook-bought-for-a-cool-billio.html)