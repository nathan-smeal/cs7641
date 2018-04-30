# Lesson 05: Information Theory

In machine learning context, in general, every input or output vector can be considered as a probability density functions. And thus information theory is a mathematical frame work that allows us to compare these density functions.

* Mutual information: How similar are these vectors?
* Entropy: Does the vector has any information?


## History

Claude Shannon

Maxwell's Deamon

## Entroypy

Example: variable length encoding

$$ENTROPY = \sum P(s)*N(s) = \sum P(s)\text{log}\frac{1}{P(s)} = -\sum P(s)\text{logP}(s)$$

P(s) is probability of the character to occur.

N(S) is the length of the character encoding in bits.

## Information Between two variables

### Joint entropy

It is the randomness contained in two variables together.

$$H(X,Y) = -\sum_{X,Y} P(X,Y) \text{log}P(X,Y)$$

### Conditional entropy

It measures the randomness of one variable given the other variable.

$$\begin{aligned}
H(Y|X) & = -\sum_{X,Y} P(X,Y) \text{log} P(Y|X)\\
& = \sum_X P(X)\;(-\sum_Y P(Y|X) \text{log} P(Y|X))
\end{aligned}$$

If $X$ is independent of $Y$, then:

$$H(Y|X) = H(Y)$$
$$H(X,Y) = H(X) + H(Y)$$

## Mutual information

$H(Y|X)$ will be small whether $X$ tells very little about $Y$ or $H(Y)$ it self is very small.

$$I(X,Y) = H(Y) - H(Y|X)$$

Mutual information measures the reduction of randomness of a variable given knowledge of another variable.

## Kullback-Leibler Divergence (DK Divergence)

Measures the different between any two distributions.

$$D(p||q) = \int p(x) \text{log} \frac{p(x)}{q(x)}$$

Is alway non-zero and zero only when $p=q$. Serves as distance measure but does not obey triangle law. Can substitute the least square measure for fitting.





...
