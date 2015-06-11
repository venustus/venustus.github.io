---
layout: post
title: Functional implementation of disjoint sets
date: '2015-06-04T18:50:00.000-08:00'
author: Venkat Pedapati
tags: union find, functional programming
modified_time: '2015-06-04T18:50:00.000-08:00'
---

Disjoint Set (or also called as union-find) data structure undoubtedly, is my most favorite data structure till date. It is surprisingly simple
to illustrate and implement, but do not let the looks of it deceive you. It comes in handy in so many 
situations and in some cases, it knocks the problem out of the park. It is very efficient and has close to 
linear running time (in fact so close that you can consider it linear for all practical purposes).

Here is a how the data structure looks like:

![Initial State](/public/disjoint-sets-init.png)

Initially a disjoint set consists of n distinct sets of items each with just one item.
The data structure supports two operations:

* <i>Union</i> - Combines two sets into one set. Note that union operation can be applied multiple times, 
to create clusters of items. For example, for the above example, if we invoke the following operations in order:
<pre>
    union(1, 2)
    union(5, 6)
    union(8, 5)
    union(6, 1)
    union(3, 4)
</pre>
We get:

![Final State](/public/disjoint-sets-final.png)

* <i>Find</i> - Finds the set containing a given item and returns it.

Typically, for convenience, we represent sets of items using a representative item called a <i>leader</i>.
When two sets merge using a <i>union</i> operation, the combined set will have a new leader (could be the leader
of either set or some other element in either set).

Disjoint Sets using arrays
==========================

In a naive and straight forward implementation of this data structure, we represent items as numbers from 1 to n
and an array is used to store the identity of the set to which an item belongs. As we discussed, identity of the set
is given by it's leader and leader is one of the items in the set. So, the array just contains it's own indices. Then when
we want to perform <i>union</i> of two sets, we just update the elements of array to the respective new leader.
At the beginning, each element is a leader of it's own singleton set. When we merge two sets, we arbitrarily
pick leader of either set to be the leader of the new merged set.

In this implementation, the <i>find</i> operation is very fast - it takes only constant time since each array 
position directly points to it's leader. However, when performing <i>union</i>, we need to update the 
leader pointers of all the elements in one of the sets being merged. This means, for an initial set containing
n elements a series of m union/find operations can take up to O(mn) time.

However, if we carefully choose which of the two leaders to be the new leader of merged set, we can achieve
a tighter time bound. In particular, we should always choose the leader of bigger of the two sets being merged,
to be the new leader. Because then we would have to update smaller number of leader pointers. If we put 
this optimization in, we get O(m + n log n) time bound on a series of m union/find operations. 

You may be surprised about how we got this seemingly drastic improvement by just a simple choice (at least I was).
Here is a way to think about this. Think about when a leader pointer of a particular set is updated. It is only
updated when the set containing that element, is being merged with another set of same or greater size. So, 
every time a leader pointer for a given element is updated, the size of the merged set doubles. Well, you can 
only double the set log n times before all elements get merged into a single set. So, overall time taken
performing leader pointer updates is at most O(n log n). And of course we may be performing up to m find operations
which shall take O(m) time. So, we get O(m + n log n) for a sequence of m union/find operations.

Disjoint Sets using trees
=========================

Now we look at a completely different way of thinking about this data structure. Instead of storing the 
leader pointer directly with each element, we store a parent pointer. When we merge two sets, we just update 
the leader pointer of one of the leaders to point to the other. We do not change the leader pointers of any 
other element in either set. In this implementation, when we are asked to do the union, we first find leaders of 
the two elements and update the leader pointer of one of them to point to the other. 

Instead of forming bushy and shallow trees like in the previous approach, this approach forms deeper and lopsided
trees, because as we proceed to merge different sets, we are not rewiring leader pointers of the children.

At the outset, this actually looks worse than our previous approach - now we have to spend up to O(n) time
to find the leader of a given element and even worse, we have to spend O(n) time even to do union because
to be able to merge leaders, we should find leaders first and finding leaders is no longer a constant time 
operation.

But wait till you see the next two optimizations we put in. 

Optimization 1: Union by rank
-----------------------------

This is very similar to the optimization we had put in earlier, for array implementation. We note that the trees
get deeper and deeper, if we attach a deeper tree to a shallower tree. This point is better illustrated by a figure:

![Union by rank optimization](/public/disjoint-set-trees/disjoint-set-trees.jpeg)

As you can see, if we choose to make 1 the new leader, we got a shallower tree. Following this intuition,
we devise the rule that we always make the leader of the deepest tree, the new leader of the merged set. That is
we update the parent pointer of the leader of the shallower tree to point to the leader of the deeper tree.

Using an argument that is similar to the previous section, we can derive that if we apply this optimization, 
both union and find operations take O(log n) time in the worst case. So, overall time complexity for a series
of m operations will be capped at O(m log n).

We already seemed to have made this data structure much faster than we started with O(mn). But as the mantra
of a computer scientist reads - never stop seeking more efficient solutions. 

Unexpectedly, there is still some more we can do to make this faster.

Optimization 2: Path Compression
--------------------------------

If you look at the find operation closely, we are traversing up to O(log n) elements to the root of the trees
every time we want to find the leader of an item. This seems wasteful, since once an element is attached to a particular root,
it is never gonna leave that root again. It goes into every set into which the root goes along with all it's ancestors all the way to the root. 
So, when we are traversing the path to the root, there is no point in repeatedly traversing the same path again 
and again. So, we rewire the parent pointers of all the elements along the path to the root (except the root's 
immediate child), to point to the root instead. This technique is illustrated below:

![Path Compression](/public/disjoint-set-trees/path-compression.jpg)

Once we employ this technique, it turns out we will end up getting huge benefits in terms of overall time
complexity and we end up with <i>O(m * Alpha(n))</i> where <i>Alpha(n)</i> is called <i>Inverse Ackermann function</i>.

The inverse ackermann function grows so slowly that this is practically linear time algorithm. I'm not going to 
dive deep into the analysis that proves this upper bound on time complexity. If you are interested, I've given some
references at the end.

Implementation in Scala
=======================

While it is pretty straight forward to spin up a mutable implementation of the data structure, I thought
it will be worthwhile to pursue a purely functional implementation. Here is what I came up with:

<script src="https://gist.github.com/venustus/d2e4a404ce9cf037e4d8.js"></script>

References
==========


1. First two images are borrowed from: https://www.wikiwand.com/en/Disjoint-set_data_structure.
2. Tarjan, Robert Endre (1975). "Efficiency of a Good But Not Linear Set Union Algorithm". Journal of the ACM 22 (2): 215–225. doi:10.1145/321879.321884
3. https://class.coursera.org/algo2-004/lecture

