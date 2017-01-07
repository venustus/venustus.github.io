---
published: false
layout: post
title: Managing your Git workspaces efficiently
author: Venkata Pedapati
tags: 'git, magit, emacs'
date: '2017-01-01T18:50:00.000-08:00'
modified_time: '2017-01-01T18:50:00.000-08:00'
---
![29522714865_33793e3bcd.jpg]({{site.baseurl}}/public/29522714865_33793e3bcd.jpg)

Git has become the default standard for version control for more than a few years now. While there are a few competing version control systems, there is nothing that is as pervasive as Git. I've been using Git both for my personal projects as well as inside my company for managing source code, for over 3 years now.

But Git has lot of commands and even for seasoned users, raw Git commands are an annoyance to remember and time consuming to type every time. I had explored various alternatives, including some GUIs for Git. Here are some of the trivial options I had tried:

* GitHub Desktop for Mac (Free) - https://desktop.github.com - A UI client for GitHub from GitHub.
* Tower ($79) - https://www.git-tower.com/mac/ - Most comprehensive UI toolkit for Git, but expensive.
* SourceTree (Free) - https://www.sourcetreeapp.com

But I felt that none of these addressed one of the fundamental problems I was facing with managing my works spaces. All of them seem to plug-in a user interface on top of Git features, by not focussing on workflows. As a result, these tools, at best, take same amount of time and effort as typing in actual git commands and at worst be a distraction from what we want to do. 

In particular, following are the use cases, which I believe form the crux of managing a git workspace. None of the above three, seemed to have solved all of them effectively.

* Viewing the current state of a repository, staged/unstaged changes, current branch information, other branches available.
* Switching branches easily. 
* Pull-Rebase-Merge-Push - the standard workflow many people follow, for managing their work.
* Interactive rebasing.
* Viewing Git Log.

Apart from these, I had also tried Git clients embedded into my editors. Embedded clients have the advantage that we don't have to switch to a different application, just to perform version control related tasks. In particular, the embedded client that comes with IntelliJ (which is pretty much my default editor for any project these days), is quite powerful. But it makes it incredibly time consuming to switch branches, rebase and viewing Git log, particularly when there are multiple Git repositories involved.

Other than IntelliJ, I am already a regular Emacs user and in fact, I do not have a separate shell open, other than the ones I open from inside Emacs. At any given point, my Emacs session would have at least 10-20 buffers open, with 4-5 of them being shells. 

It was an obvious thing for me then, to look for an Emacs package that allows me to manage Git workspaces. Thats when I came across [Magit](https://magit.vc).

At the core, Magit allows me to perform all the common workflows I described earlier, with just 2-3 keystrokes. For the amount of work it does, compared to the cognitive load it puts on programmer's mind is almost negligible.

In Emacs, you start by navigating to the directory (either by opening a file in the directory or by using the built-in `M-x shell` command) and typing `M-x magit-status`. You are greeted by a simple interface that shows the current status of the repository - current selected branch, any staged or unstaged changes.

Once on the `magit-status` page, you can access almost any standard functionality in git, using at most two key presses. For example:

* Switch branches: `b b <branch-name> RET`.
* Create new branch: `b c <starting-point> RET <branch-name> RET`.
* View git log: `l l`.
* Pull from origin: `F u`.
* If you are on a different branch and you want to rebase on top of master: `r e`.
* Start an interactive rebase session: `r i`.

Just like for Emacs, there is an initial learning curve, but once you get used to the commands, it is so convenient that you would never want to use anything else other than Magit (as long as you use git that is).
