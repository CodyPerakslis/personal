---
# Documentation: https://sourcethemes.com/academic/docs/managing-content/

title: "Error Correcting Codes Notes: Gilbert Bound"
subtitle: ""
summary: ""
authors: [admin]
tags: [math,math5251,algebra]
categories: [class]
date: 2020-02-12T15:40:17-06:00
lastmod: 2020-02-12T15:40:17-06:00
featured: false
draft: false
math: true

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
# Focal points: Smart, Center, TopLeft, Top, TopRight, Left, Right, BottomLeft, Bottom, BottomRight.
image:
  caption: ""
  focal_point: ""
  preview_only: false

# Projects (optional).
#   Associate this post with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `projects = ["internal-project"]` references `content/project/deep-learning/index.md`.
#   Otherwise, set `projects = []`.
projects: []
---
{{% toc %}}
## Review
$Q^n$. $|Q|=q$. $C \subseteq Q^n$. $d_H(x,y).$

$$d_{\min}(C) = \min_{x,y \in C, x \neq y} d_H(x,y)$$

$wt(x)$ = # non-zeros in x.

$S_r(x) = \\{ y \in Q^n \mid d_H(x,y) \le r \\}$
$$|S_r(x)| = \sum_{i=0}^r \begin{pmatrix}n\\\i\end{pmatrix}(q-1)^i$$

## BSC
BSC(p)$_{0 < p < \frac{1}{2}}$. $R$ is an alphabet.  
Capacity $C = 1 - H_2(p)$ since binary. By the noisy coding theorem, you will only get about $C$ bits out of an encoding.  

Minimum distance = maximum likelihood.

### Singleton Bound
$|C| \le q^{n-d+1}$
### Hamming Bound
$|C| \le \frac{q^n}{\sum_{j=0}^e \begin{pmatrix}n\\\j\end{pmatrix} (q-1)^j}$ where $e = \lfloor \frac{1}{2}(d_{\min} - 1) \rfloor$

In ch. 13 of the book.

## Gilbert Bound
$Q^n$. $d$ as the designed minimum distance.  
Construct code $C$ with $d_{\min}(C) \ge d$.  
Take $x_1$ arbitrary.

Suppose $x_1, , x_k \in C$, $d_H(x_i,x_j)\ge d$ for $i \neq j$.  
Consider spheres $S_{d-1}(x_i)_{1 \le i \le k}$.  

$\exists y \notin \cup_{i=1}^k S_{d-1}(x_i)$  
$=>d(y,x_i) \ge d$  
=> can incldue y in code, $y = x_{k+1}$.  
Can do this as long as $\cup_{i=1}^k S_{d-1}(x_i) \not\subseteq Q^n$.  
True if $k |S_{d-1}(x_1)| < q^n \rightarrow$ can enlarge code. $k$ is the size of the codeword.

There exists code $$|C| \ge \frac{q^n}{\sum_{j=0}^{d-1} \begin{pmatrix}n\\\j\end{pmatrix} (q-1)^j}$$

{{% alert note %}}
Apply to **Linear Codes**. Linear Codes have the property that the code itself is a linear subspace. They will be covered more in the class.
{{% /alert %}}

## Error Correcting Measures
Want large minimum distance relative to length of code to fix errors. Want to keep expansion to a mininum, while still getting the robustness.  
rate $r = \frac{\log_q |C|}{n}$, $\delta = \frac{d_{\min}(C)}{n}$.
{{% alert note %}}
A code with $d = d_{\min}(C)$ can detect $d-1$ errors. Can correct $\lfloor \frac{1}{2}(d_{\min} - 1) \rfloor$ errors. Considering $d$ and $n$ very large.  
BSC(p): $pn$ errors.  
If $pn < \frac{1}{2}d(1 - \epsilon)$, then you almost surely have fewer than half $d$ errors, and you can correct.
{{% /alert %}}
$Q^k \rightarrow C \subseteq Q^n$, size of code $q^k$.  

Let $q = 2$. Delta between 0 and 1.  
**Singleton:** $\frac{\log_q |C|}{n} \le \frac{n-d+1}{n} = 1 - \frac{d}{n} + \frac{1}{n} \approx 1 - \delta$
{{% alert note %}}
$n! \approx \begin{pmatrix}n\\\e\end{pmatrix}^n$  
$\begin{pmatrix}n\\\k\end{pmatrix} \approx 2^{nH_2(\frac{k}{n})}$  
$\sum \begin{pmatrix}n\\\k\end{pmatrix} \approx 2^{nH_2(\frac{k}{n})}, k \le \frac{n}{2}$.  
Double squiggle for some handwaving.
{{% /alert %}}
**Hamming**: $|C| \le \frac{2^n}{2^{nH_2(\frac{d}{2n})}} \approx 2^{n(1-H_2(\frac{1}{2}\delta))}$

$|C| \ge \frac{2^n}{\begin{pmatrix}n\\\d\end{pmatrix}} \approx 2^{n(1-H_2(\delta))}$

**Gilbert**: Exists code with $|C| \ge 2^{n(1-H_2(\delta))}$, $\delta \le \frac{1}{2}$

{{< figure library="true" src="ecc-2020-02-12.png" title="Approximate rates of bounds" lightbox="true" >}}

Best codes between Gilbert (green) and Hamming (red). Y-axis is delta, X-axis is rate.

For $q = 2, \delta = \frac{1}{10}$.  
S: $r \le 0.9$  
H: $r \le 0.73$  
G: $r \ge 0.53$

[Justesen Code](https://en.wikipedia.org/wiki/Justesen_code)
$r \approx 0.1$ Constant rate, but too low rates.  

Some codes give up on minimum distance for better results. Noisy coding theorem can achieve capacity by using codewords at random. Very bad, since two words can be encoded the same way.  

## Basic Arithmetic
$\mathbb{Z} = \\{0, \pm 1, \pm 2, ...\\}$.  
$d \neq 0$, $d | n \leftrightarrow \exists k \in \mathbb{Z}$ s.t. $n = dk$  
Example: $3 | 0, \pm 3, \pm 6, \pm 9, ...$  

$d|n, n|h \rightarrow d|h$  
$d|m,d|n$: $d$ is the common divisor.  
### GCD
There exists a greatest common divisor $d = gcd(m,n)$ if $|m|+|n| \neq 0$, and any common divisor $e$ satisfies $e|d$.  
**Proof**: Let $d$ be the smallest positive integer $xm + yn$.
Suppose $d|m,d|n$. Enough to show $d|m$ since symmetric.  
Suppose not: then $m = qd+r$, $0 < r < d$.  
$r = m - qd = m - q(xm+yn) = (1-qx)m - qyn$  
$r > 0, r < d, r$ is a linear combination of $m$ and $n$, so $d$ was not the smallest linear combination, which is a contradiction. Therefore $d$ did divide.
