---
math: true
title: Geometric series
description: This is a post about the geometric series and an interesting application of it.
date: 2022-02-04 17:30:13 +0100
draft: false
tags: [math]
---

I was doing a little work on the geometric series in class today, and then found a nice application for it in math club. The post summarizes it. 

In math class I dealt with the two formulas 
$$\sum_{k=0}^{n}r^k=\frac{1-r^{n+1}}{1-r}$$ und $$\sum_{k=0}^{\infty}r^k=\frac{1}{1-r},|r|<1.$$ The first can be proved by induction. The inductionstep looks like this. $$\sum_{k=0}^{n+1}r^k=\sum_{k=0}^{n}r^k + r^{n+1}=\frac{1-r^{n+1}}{1-r} + r^{n+1} = \frac{1-r^{n+1} + (1-q)r^{n+1}}{1-r} = \frac{1-r^{n+1} + r^{n+1} - r^{n+2}}{1-r} $$
$$= \frac{1 - r^{n+2}}{1-r}.$$

The second formula can then be proven with the first one like this. 
$$\sum_{k=0}^{\infty}r^k=\lim_{n\rightarrow \infty}\sum_{k=0}^{n}r^k = \lim_{n\rightarrow \infty} \frac{1-r^{n+1}}{1-r} = \frac{1-\lim_{n\rightarrow \infty} r^{n+1}}{1-r} \overset{|r|<1}{=} \frac{1}{1-r}$$

# Application

The formula that was covered in Math Club was the following $$\sum_{k=1}^{N}\sin(x + \frac{2k}{N}\pi)=0$$ 
We approached the proof first from an induction way of thinking, but that didn't really work out. I then came up with a way of proving it using the formula that I had proven in math class. For that, you have to transform the equation a bit.

$$\sum_{k=1}^{N}\sin(x + \frac{2k}{N}\pi) = \sum_{k=1}^{N} \frac{1}{2i}(e^{ix + 2k/N\pi i} - e^{-ix - 2k/N\pi i})$$ 
$$= \frac{1}{2i}(\sum_{k=1}^{N} e^{ix}\sum_{k=1}^{N} e^{2k/N\pi i} - \sum_{k=1}^{N} e^{-ix}\sum_{k=1}^{N} e^{-2k/N\pi i})$$

Now you really only have to prove that

$$\sum_{k=1}^{N} e^{2k/N\pi i}=0$$ und $$\sum_{k=1}^{N} e^{-2k/N\pi i}=0$$

Here you can use the geometric series, because

$$\sum_{k=1}^{N} e^{2k/N\pi i} = \sum_{k=0}^{N-1} (e^{2/N\pi i})^k = \frac{1-(e^{2/N\pi i})^N}{1-e^{2/N\pi i}} = \frac{1-(e^{2N/N\pi i})}{1-e^{2/N\pi i}} = \frac{1-(e^{2N/N\pi i})}{1-e^{2/N\pi i}}=\frac{1-1}{1-e^{2/N\pi i}}$$
$$=\frac{0}{1-e^{2/N\pi i}} = 0$$ 

and the formel is proven.
