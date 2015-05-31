---
layout: post
title: Maintainable web applications
date: '2013-11-10T18:50:00.000-08:00'
author: Venkat Pedapati
tags: 
modified_time: '2013-11-10T19:04:49.293-08:00'
blogger_id: tag:blogger.com,1999:blog-31127640.post-3255412983437503600
blogger_orig_url: http://www.venustus.in/2013/11/maintainable-web-applications.html
---

<div dir="ltr" style="text-align: left;" trbidi="on"><div dir="ltr" style="text-align: left;" trbidi="on">
For the major part of my short career, I've worked on shrink wrapped enterprise products that most of the people in consumer industry wouldn't know about. While I worked on some interesting technical challenges, it was clear to me that I wanted to learn everything there is to know about mainstream web app development for the internet. I've been trying to learn different approaches to web app development all along, but one thing that turned out to be a big obstacle for me is the sheer number of options you have in choosing different technologies and libraries.<br /><br />I remember I was trying to create websites in college by editing HTML and creating frames. That was really hard to do even for creating simplest of websites. Then a second wave of enlightenment came, when I discovered complete server side frameworks like ADF. They do give you a huge productivity boost since they try to abstract everything away behind nice abstractions. You could create complex applications without writing a single line of javascript/HTML. But somehow I realized that at least existing frameworks in this area are not doing it right. Firstly, most of the computation happens on server side resulting in unbearable latencies and terrible responsiveness. A modern web app is a collection of lots of data and several interactive features. These server-side frameworks fail in bringing the interactive nature of desktop applications to web applications.<br /><br />Then came <a href="http://jquery.com/">jQuery</a> and a plethora of javascript frameworks. Initially this seemed like a good idea to develop complex web apps. But as a novice in web app development, I soon got overwhelmed by the complexity involved in creating significant web applications. For smaller applications which do not require lot of code, they seemed fine, but all the DOM manipulation logic gets to you once the code base size crosses some threshold. Further, it is hard to choose from insanely large number of javascript frameworks and soon we'll be dancing in a dependency hell. jQuery is nice, but it doesn't seem like the ideal way to create large web applications. In particular, maintainability is the one that gets hurt the most.<br /><br />Recently, I've been looking at <a href="http://angularjs.org/">AngularJS</a> which seems like taking web app development to the next level. The crucial ingredient for maintainability is separation of concerns. If we want the web application to be very responsive and snappy then a purely thin client architecture is out of question. But if we are doing lot of computation on the client side, we do want to organize it properly so that we can grow the code base organically. What AngularJS provides is an MVC-like architecture on client-side so that your client-side code is as organized as the one on your server side. Although AngularJS does several things differently from lot of client-side frameworks out there, one thing that stands out is the two-way data binding. You just define the model and the DOM gets automatically updated when your model changes and the other way around too - the model gets updated as user provides inputs into the DOM. This can be leveraged to the point that we almost never need to manipulate DOM directly.<br /><br />The ability to define custom directives enables developers to naturally extend HTML to do nice stuff that otherwise requires messy DOM manipulation in jQuery world.<br /><br />I'm working on a small productivity tool using AngularJS and I'll discuss about it in the next post.<br /><br /><br /></div>

<iframe style="width:120px;height:240px;" marginwidth="0" marginheight="0" scrolling="no" frameborder="0" src="//ws-in.amazon-adsystem.com/widgets/q?ServiceVersion=20070822&OneJS=1&Operation=GetAdHtml&MarketPlace=IN&source=ac&ref=tf_til&ad_type=product_link&tracking_id=venustus-21&marketplace=amazon&region=IN&placement=1449344852&asins=1449344852&linkId=URYK4MYX3UXFV7FT&show_border=true&link_opens_in_new_window=true"></iframe>  </div>