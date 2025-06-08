---
title: Riemann Sum
layout: post
date: 2025-03-10
# image:
#     path: /assets/images/Welcome.png
tags: Integral, Riemann
description: What is a Riemann Sum?
math: true
---

<h1 align="center">What is a Riemann Sum?</h1>

When you hear the word **integral**, think about **area** — specifically, the area under a curve.

But here's the catch: finding the exact area under a squiggly curve isn't always easy. That's where **Riemann Sums** come in.

---

### 🧱 The Idea Behind Riemann Sums

Imagine trying to find the area under a hill using blocks. The more blocks you use, the better the approximation, right?

Riemann Sums do exactly that:  
> They estimate the area under a curve by summing up the areas of rectangles placed under the curve.

---

### 🧮 The Formula

The general form of a Riemann Sum is:

$$
\sum_{i=1}^{n} f(x_i^*) \Delta x
$$

Where:

- \( n \) = number of rectangles
- \( \Delta x \) = width of each rectangle
- \( x_i^* \) = a point in the \( i \)-th subinterval (could be left endpoint, right endpoint, or midpoint)
- \( f(x_i^*) \) = height of the rectangle (based on the function value)

---

### 📌 Left, Right, and Midpoint Riemann Sums

Let’s say we’re estimating the area under \( f(x) \) from \( a \) to \( b \):

- **Left Riemann Sum** uses the **left endpoint** of each interval  
- **Right Riemann Sum** uses the **right endpoint**  
- **Midpoint Riemann Sum** uses the **middle** of each interval  

Example of Left Riemann Sum:

$$
L_n = \sum_{i=0}^{n-1} f(x_i)\Delta x
$$

---

### 🧪 Simple Example

Estimate the area under \( f(x) = x^2 \) from \( x = 1 \) to \( x = 3 \) using 4 rectangles and **Right Riemann Sum**.

1. Interval: \( [1, 3] \), so \( \Delta x = \frac{3 - 1}{4} = 0.5 \)
2. Right endpoints: \( 1.5, 2.0, 2.5, 3.0 \)
3. Function values: \( f(1.5), f(2.0), f(2.5), f(3.0) \)

Now calculate:

$$
R_4 = f(1.5)(0.5) + f(2.0)(0.5) + f(2.5)(0.5) + f(3.0)(0.5) \\
= (2.25 + 4 + 6.25 + 9)(0.5) = 21.5 \cdot 0.5 = 10.75
$$

So the estimated area under \( f(x) = x^2 \) from 1 to 3 is **about 10.75**.

---

### 🎯 Why Riemann Sums Matter

Riemann Sums are the **foundation** of **definite integrals**. The integral is basically:

> What happens to the Riemann Sum when we use **infinitely many tiny rectangles**.

In notation:

$$
\int_a^b f(x)\,dx = \lim_{n \to \infty} \sum_{i=1}^{n} f(x_i^*) \Delta x
$$

---
.
