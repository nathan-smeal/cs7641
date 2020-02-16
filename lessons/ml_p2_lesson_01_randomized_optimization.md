# Lesson 01: Randomized Optimization

## Randomized Optimization

**Optimization**:

* input space $X$
* objective function: $F: X \Rightarrow \mathbb{R}$
* Goal: find $x^*\in X$, s.t. $F(x^*)=\underset{x\in X}{max}F(x)$.

Find the best: $x^*$ is not necessarily the best, but close the best.

Something near argmax, as in close to the best.

Examples:

* Neural network: adjust the parameters to minimize the error.
* Root finding
* route finding
* factory, chemical, process control
* Anything with parameters where some are better than others and can have a fitness problem
* Decision trees (whole structure)
* Everything we did in the first third of the class

## Optimization approaches

* Generate and test: small input space, complex functions
* Calculus: function has solvable derivative
* Newton's method: function has derivative, iteratively improve, single optimum.

What if the above assumptions do not hold? -> no gradient things point the way to go. =>

big input space, complex function, no derivative (or hard to find)

 **Randomized Optimization**

## Hill Climbing

Algorithm:
> * Guess $x \in X$.
> * Repeat:
>   + let $n^*=\underset{n\in N(x)}{argmax} f(x)$.
>   + if $f(n^*) \geq f(x)$: $x = n^*$
>   + else: stop

Note: $N(x)$ returns the neighbors of $x$ in $X$.

This algorithm  can easily get stuck at local optima.

### Random Restart Hill Climbing

Once local optima is reached, try again starting from a randomly chosen $x$.

Advantages:

* multiple tries to find a good starting place.
* Not much more expensive (constant factor)

The restarts should have a systematic way to cover the entrie search space.

But there exist cases where the search space is very awful and very hard to find the global optima.

## Simulated Annealing

Don't always improve (exploit), sometimes you need to search (explore).

### Annealing algorithm

For a finite set of iterations:
* sample new point $x_t$ from $N(x)$
* Jump to new sample with probability given by an acceptance function $P(x, x_t, T)$.
* Decrease the temperature $T$.

$$
P(x, x_t, T) =
     \begin{cases}
       1, & \text{ if } f(x_t) \geq f(x)\\
       e^{\frac{f(x_t) - f(x)}{T}}, & otherwise
     \end{cases}
$$

Note:

* T > 0
* When $f(x_t) << f(x)$, the probability will be very close to zero, and that step won't be likely to be taken.
* Small step down ($|f(x_t) - f(x)|$ is small), then the probability is high and likely to happen.
* High temperature will casue the probability to go up.

### Properties of SA

* $T \rightarrow 0$, like hill climbing
* $T \rightarrow \infty$, like random walk
* decrease T slowly
* Probability about the final ending point ($Z_T$ is some normalization factor):

$$Pr(\text{end at } x) = \frac{e^{f(x)/T}}{Z_T}$$

* This is Boltzmann distribution
  + The point with higher value will have higher probability to be reached.
  + As temperature goes down, it will head to the max.

## Genetic Algorithm

Analog to biology evolution.

* Population of individuals
* Mutation - local search: $N(x)$
* Crossover - Population holds information. Combine the attributes of two individuals and hopefully get a new one.
* Generations - iterations of improvement.

**Note**:  Population is like parallel random restarts; except for crossover.  Somehow these parallel random searches are bleeding info back and forth.  Conveys info like genes.

### GA sekleton

> * $P_0$ = initial population of size K
> * Repeat until converged:
>   + compute fitness of all $x \in P_t$.
>   + Select the "most fit" individuals. (top half, weighted prob)
>   + Pair up the individuals, replacing the "least fit" individuals via mutation/crossover.

If select individuals at random, but bias towards most fit, then it's like `SA` if set a temperature selection.  It's a form of explore and exploit with how it is weighted in selecting the individuals for pairing.

### Crossover Example

name | 1| 2 |3|4|5|6|7|8
-|-|-|-|-|-|-|-|-
charles | 0|1|1|0|1|1|0|0
sheila  |1|1|0|1|0|1|1|1
offspring next|*|*|*|B|B|*|*|*
joni    |0|1|1|0|0|1|1|1
cody    |1|1|0|1|1|1|0|0

B = border for flipping position

**one-point crossover**: choose one of the positions, divide them into 2 parts, and flip-flop.

Bias (assumptions on search space):

* locality of the attributes (bits in this example)
  * assumes pieces are right
* subspaces that are optimizable independently

**uniform crossover**: randomize each attribute. (like genes)

* subspaces that are optimizable independently but no locality

## Summary:

The methods above doesn't keep track of what they have been traversed and the probability distribution.  Charles mentions how this sometimes assumes structure of data but doesn't attemplt to exploit it with modeling or probabilities.(Hint:  MIMIC)

To remember the history and distribution:
* Taboo search: avoid the region where has been evaluated.

## MIMIC












...
