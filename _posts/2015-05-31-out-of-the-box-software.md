---
layout: post
title: Technology that doesn't work out-of-box
date: '2015-05-31T18:50:00.000-08:00'
author: Venkat Pedapati
tags: technology, passport, western digital
modified_time: '2015-05-31T18:50:00.000-08:00'
---

Last week, I bought a [WD My Passport 1 TB hard disk](http://www.amazon.in/gp/product/B00EYCBFDQ?tag=venustus-21) to let my dad store all the pictures from my brother's 
wedding. There were thousands of pictures, and he was instructed by the guy who covered the wedding on camera 
that such a hard disk would be much easier to handle than a bunch of DVD's (are these still in use?).

This perfectly made sense to me. For my wedding, there were 6 sets of 3 DVD's each (along with a bulky paper album).
And the new laptops do not even have a DVD reader anymore. 

While the shipping was very quick and smooth from [Amazon](http://www.amazon.in?tag=venustus-21), I enthusiastically plugged the same into my Mac with
the intention of copying over a 1000 photos from my 'Photos' app to the external hard disk. I selected all the 
photos I would like to copy and dragged them over to the Finder window containing the hard disk folder.

To my surprise, I couldn't drop it in. When I looked for more details, I figured that by default, the external
hard disk is formatted using NTFS and hence MAC OS X cannot write to this disk. I couldn't even create any folder.
It was surprising because, I already have a Seagate 1TB hard disk and that worked out of box on my Mac.

I looked for some clues and hidden away somewhere in Western Digital knowledge base is [this article](http://wdc.custhelp.com/app/answers/detail/search/1/a_id/3865/c/130/p/195,251) about 
how to make it work on MAC OS X. It contains 10 separate steps to follow before I could get it working. 
Essentially it instructed me to format the disk using an Apple friendly file system (which would probably erase
all data on the disk if it had any and further make it unusable on a PC).

This example shows how lazy some companies are in recognizing needs of their customers and how not to design
human-computer interactions. Forget about being customer friendly. This thing doesn't even work out-of-box.

When I opened the box, my father curiously looked for a user manual, but it isn't there. Then we realized these
guys are not shipping user manuals in paper any more. The user manual is on the disk itself. One needs to connect the 
USB cable to the computer, recognize the new disk in either Finder or My Computer, open the user manuals folder,
choose the language and open the PDF file for user manual (and I don't want to think about the case 
if one doesn't have Adobe Reader installed).

Who would keep a user manual for a hard disk, inside the hard disk? I double checked carefully if there are some rough instructions
to connect the hard disk to my computer, in the box, but there were none. If I weren't there, I don't expect my father 
would have been able to figure this out all by himself (should he?).

I keep myself reminding the golden rule for software development - if your software/hardware is usable by the 
dumbest person on earth, then you can claim to be a customer centric company.


