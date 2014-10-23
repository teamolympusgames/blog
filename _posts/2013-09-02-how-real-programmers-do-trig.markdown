---
author: wanthonyalford
comments: true
date: 2013-09-02 12:05:51+00:00
layout: post
slug: how-real-programmers-do-trig
title: How Real Programmers Do Trig
wordpress_id: 21
categories:
- Code
---

Hacker News linked this fascinating blog post about the [Sinclair Scientific Calculator](http://files.righto.com/calculator/sinclair_scientific_simulator.html), vintage 1974. Having been an avid user of scientific calculators and also assembly language, I got a big kick out of the clever hacks Sinclair used to implement trig.

Let's say you need to calculate the sine of an angle. How would you do that? Well, you punch the angle into your calculator and press the "sin" button. Ok, but how does the calculator know? When I was in high school, we had to look up the answers in a table in the back of the textbook, and in fact that's a very fast way to implement trig functions in code. There's a downside: it takes a lot of ROM space. Another way is to do it is use a [Taylor series](http://en.wikipedia.org/wiki/Taylor_series); you probably wouldn't need too many terms to get it to pretty good accuracy.

Unfortunately, neither one of these would work for Sinclair. ROM space was pretty much taken up by the code to do basic arithmetic. The processor itself wouldn't even do multiplication, so multiplying numbers was itself a chunk of code. Time to get clever!

The solution was to start with the 2-d unit vector (1,0) and iteratively rotate it by 0.001 radians---by applying a rotation matrix. Normally, you'd define the rotation matrix as ( (cosθ  -sinθ) (sinθ cosθ) ). But here's the clever part: for very small values of θ, cosθ is approximately 1, and sinθ is approximately θ. So for θ=0.001, that matrix is approximately ( (1  -1/1000) (1/1000 1) )_
_

One more thing you should know: the calculator represented numbers in scientific notation. So to divide by a power of 10, you don't actually have to divide; you just subtract from the exponent. So now you can apply this rotation matrix simply by adding and subtracting! How cool is that?
