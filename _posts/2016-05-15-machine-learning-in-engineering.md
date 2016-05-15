---
layout: post
title: Machine Learning for engineers
date: '2016-05-15T18:50:00.000-08:00'
author: Venkat Pedapati
tags: machine learning
modified_time: '2016-05-15T18:50:00.000-08:00'
---

It has been almost 3 years since I did my first course on [Machine Learning on Coursera](https://www.coursera.org/learn/machine-learning). Machine learning has evolved quite a lot in this short amount of time and in particular, there has been renewed interest in it's applications to many engineering problems. 

Machine learning used to be primarily a research topic, but with outstanding work from major technology companies in the field (like Google, Facebook, Microsoft etc.), there are now hundreds of applications where use of machine learning almost blew away the previous state of the art. 

When thinking about machine learning, it is easy to consider only some fancy applications like self-driving cars, computer vision, robotics etc. and ignore the general applicability of the techniques. While the impact of machine learning has certainly been greatest in these exciting fields, it can also do wonders in more mundane every day problems in engineering.

My rule of thumb is: if you find yourself building applications that have large set of rules and the outcome depends on many independent variables and complex interactions between those variables, then you are probably entering into a domain where ML techniques can solve it in a much simpler way for you. Programming complexity of such an application can reduce drastically, once you notice that you are trying to code up all the patterns in data and programming the computer recognize them. 

Instead, you can let the computer learn the patterns in data all by itself, by simply running a machine learning algorithm.

Here are some of the areas, I noticed, where machine learning has been put to excellent use:

* Medical diagnosis - this is an emerging field and use of machine learning has not been practiced much, but it is promising nevertheless.
* Advertising - I myself work in advertising and there are at least few tens of problems which can use sophisticated ML techniques, most important being prediction of click through rates and downstream actions.
* Content dissemination on the Internet - Internet has been exploding with content and ML techniques play a crucial role to bring the whole world of news, infotainment and knowledge to people in a personalized way. For example, algorithmic nature of your Facebook/Twitter feeds is a great example. 
* Predicting climate changes at both large scale and small scale - There are huge amounts of recorded climate data available for mining and analysis today and effective application of ML techniques can yield invaluable predictions.

I'm sure this is just the tip of the iceberg and there are many more applications of ML techniques in every day engineering. But it is disappointing that despite wide spread applicability and proven effectiveness of these techniques, they have not found way into a common engineer's tool box. Most engineers treat this as an advanced research topic that requires lot of theoretical foundations and don't consider learning them while solving every day problems.

This is a major gap that needs to be filled, because this is a misconception. Ultimately, everything in Engineering has enormous amounts of dependency on mathematical and physical foundations. But if we treat engineering on the same lines as the science behind it, we can't even build a small bridge without mastering 3 different scientific fields. 

The point is Engineering does not work that way. Engineers focus on applications and getting things done. So, all we need is sufficient amount of abstraction and effective tools that hide the complexity for us. While the knowledge about underlying principles definitely help, it is not necessary to apply them. In particular, in the last 3-4 years, there have been multitude of high level frameworks and tools that make it much easier for an engineer to have a machine learning application up and running in no time.

Here are some of them I tried myself and found useful:

* [Octave](https://www.gnu.org/software/octave/)/Matlab - Octave is a programming environment that is much closer to the mathematical foundations than other tools. Matlab has to be purchased, unless your organization has licensed it for you. But Octave is free. Both of them are very similar in use and if you know one of them, you are mostly at home with the other. These are good for beginners in ML and for making toy applications. But as soon as you start working on real-world problems, you will need a higher level framework/environment. 
* [Python Scikit](http://scikit-learn.org/stable/) - This is a fantastic library for working on machine learning applications. It has lot of higher level primitives and provide many commonly used algorithms, out-of-box. Of course, you would have to be fluent in Python to use this well, but Python is one of the easiest languages to learn anyway. Another advantage with this is, it is built on top of tools like SciPy and NumPy which are also used by many other visualization and numerical computation libraries in Python and it makes it very interoperable with them.
 * [Tensorflow](https://www.tensorflow.org/) - This library has been released more recently and is by far simplest to learn and master. This one focuses specifically on Deep learning (multi-layered neural networks), which is a very useful technique in large number of fields. A good way to learn using Tensorflow is to follow the [deep learning course on Udacity](https://www.udacity.com/course/deep-learning--ud730).

So, next time you are wondering why your application is in such a messy state with hundreds of hand-coded rules, may be it is time for you to consider a new approach altogether.