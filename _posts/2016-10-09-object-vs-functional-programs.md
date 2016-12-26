---
layout: post
title: How to organize your code - programming paradigms
date: '2016-10-09T18:50:00.000-08:00'
author: Venkat Pedapati
tags: object orientation, functional programming
modified_time: '2016-10-09T18:50:00.000-08:00'
---

Most of the technical interview process in any 
large company today, is unusually biased towards judging Algorithms, 
Data structures and problem solving skills of candidates. While
these are in fact quite critical to software engineering,
I would argue that they are typically over-emphasized and
do not deserve so much attention. After all, 
in all my 9 years of software development experience, 
I can count of fingers, instances when I had to 
really think about the algorithm or a complex data structure 
for solving a problem. Majority of problems we face in 
software engineering are solved by just using basic data structures like lists, maps 
and hash tables effectively. There are certainly some niche 
areas and projects where you might require to use a 
state-of-the-art minimum spanning tree implementation, for example, but these
tend to be exceptions and not the norm. 

A much more important skill, I believe, for practical software engineering
is about building abstractions. If you think about it, any 
kind of high level program you write, is an abstraction 
over assembly instructions. Instead of writing down 3*n separate
instructions for copying an array of n elements to a 
different memory location, you can abstract it out to one call to
memcpy. 

And the importance of abstractions only increases proportionally 
with the complexity of the project. Apart from some 
mission critical applications like those that decide approach vector 
of a rocket, for example, most software projects today, benefit incredibly
from having sufficient amount of abstraction. 

One aspect of building enough abstraction is about defining 
and using complex data structures. Instead of always working
with what a programming language provides you out of box (lists, maps, tables etc.),
you build data structures that represent high level 
concepts in your application. This makes it easier to work 
with them, not only for the programmer writing code, but also
for all the programmers that are ever going to read it later. 

Different programming languages deal with this problem in different
ways and over the years, two high level approaches became much more 
popular than the others. First is the object oriented way of modeling stuff,
pioneered by Java, but has been picked by several other languages 
including Ruby, Scala and partially Python. In object oriented approach, you model your 
data structures to match real world entities in your application. Objects 
encapsulate data and also expose ways for other objects to perform 
operations on the data. In addition to basic abstractions, these languages
often provide more tools like interfaces, inheritance and polymorphism
to enable code reuse across various similar objects.

Objects naturally organize themselves into files, so it is trivial to 
separate code into individual files. Modeling your application as entities operating on data and sending
messages to each other, is quite powerful and for a specific 
type of applications, they reduce complexity and make it easier to maintain code
over time.

But there is another completely orthogonal way of 
modeling abstractions: Using abstract data types and functions. 
This is the approach typically taken by functional programming languages
like ML and Haskell. At a fundamental level, these languages also have 
ADTs, but unlike objects in an object oriented programming languages, ADTs are 
immutable and cannot be operated upon. Instead, you would expose functions
that act on ADTs and that return modified ADTs. Most of the functional programming languages 
treat functions in a first class way - allowing programmers to treat them as 
just any other value, passing them as parameters to other functions and returning
functions etc. (Higher order functions). 

Of course, functions themselves are grouped into modules and you can import and 
invoke functions from other modules. Most functional programming languages tend 
to either completely prohibit (Haskell) or discourage mutations. For example, functions
acting on data structures cannot mutate them - they can only make new copies or return
new data structures. At a high level, this might seem like a huge waste of memory to maintain
all those copies of complex data structures. This is not as big a problem as it seems, because
most of the data structures in functional programming languages are implemented cleverly 
and are called 'persistent data structures'. Instead of making a full copy of the structure 
every time, the copies retain large parts of the structure intact, from the original structure.
This is not a problem because you cannot modify/mutate the data structure at any point in
the program. 

So, when should you choose an object oriented approach vs. functional approach? 

While there is no single property of applications that can clearly point out the way, intuitively,
we can come up with certain guidelines. Any application, eventually, boils down to two aspects: 
things and operations on things. The potential of application to scale across one of these 
two dimensions, gives us some clue about which approach to choose. 

For example, if, in an application, there are lots of different kind of things but very few operations
on each of them and adding more things is more likely in future than adding operations on existing things,
then object oriented way is more suitable for such an application. That is because, in a functional setting, when 
you add a new data type, you would have to change all your existing functions to take care of the new type,
where as in an object oriented setting, you can add the additional functionality in the new type and only 
modify parts where you need the additional functionality (using polymorphism and inheritance). 

On the other hand, if the number of things in an application tend to not grow over the applications' life time,
but the number of operations on existing things might grow, then a functional setting suits best, for the 
opposite reason.

Both approaches are quite powerful and have their own niche areas where they shine. It is upto the programmer
to choose the right kind of abstractions for a given problem.
