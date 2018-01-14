# Machine Learning
Tom Mitchell @ 1997

## Chapter 1: Introduction

ML is foundationally multi-disciplinary.

### 1.1 Well-posed learning problems
--------------------------------

__*Definition*__: A computer program is said to learn from experience E with respect to some class of tasks T and performance measure P, if its performance at tasks in T, as measured by P, improves with experience E.

To have a well-defined learning problem, we must identity three features: 
1. the class of tasks,
1. the measure of performance to be improved, and 
1. the source of experience.

Example:
A checkers learning problem:
1. Task T: playing checkers
1. Performance measure P: percent of games won against opponents
1. Training experience E: playing practice games against itself

Given a machine, let $P(T, E)$ be the performance of that machine at task $T$ given experience $E$. If $P(T, E') > P(T, E)$, then the machine has **learned** more from experience $E'$ than experience $E$.

An alternative interpretation.

If $E' > E$ implies $P(T, E') > P(T, E)$, then the machine has **learned**.

### 1.2 Designing a Learning System

Design a checkers program.

#### 1.2.1 Choosing the Training Experience

(Data is King in ML.) Training requires lots of thought because whatever we use to build our model determines the outcomes.  Do we train with generated data that may not map against real world situations? Does generated data expose the system to a broader more generic experience than narrow real world situations?

Building from existing checkers games by experts helps with one case. Building the system to play itself builds for a larger data set.

Learning algorithms acquire only some approximation of the ideal final target function. Because of this the process of learning the target function is often called *function approximation*.

*nonoperational* versus *operational* definitions of learning algorithm **V** depend on the computable efficiency of the function. Something is considered *nonoperational* if it cannot be efficiently computed in a reasonable time. An *operational* definition will include approximations to reduce the computing time.

#### 1.23 Choosing a Representation for the Target Function

Representations of the state of the system can be extremely accurate or summarized for efficiency based on the learning algorithm V.

Example 1:
A full board state of all pieces and their current status as endangered, safe, neutral, attacking would be extremely memory intensive and computationally expensive to get the status values.

Example 2:
A linear combination of the following board features computed once:
1. x1: the number of black pieces on the board
1. x2: the number of red pieces on the board
1. x3: the number of black kings on the board
1. x4: the number of red kings on the board
1. x5: the number of black pieces threatened by red (i.e., which can be captured on red's next turn)
1. x6: the number of red pieces threatened by black

From the simplified example 2, we can build a function to weight the V(color) value for best situation as the current board stands and evaluate for better or worse outcomes.

#### 1.2.4 Choosing a Function Approximation Algorithm

Intermediate board steps towards a defined outcome of winning are not guaranteed to be the best situation per step. But those steps most advantageous are likely to lead to better outcomes.

Rule for estimating training values:  Vtrain(b) <- V(Successor(b))

Vtrain(b) is equal to the next successive move Vtrain(b) state. This means that the estimation depends on the outcome of the next move status. This method converges towards a perfect estimate of Vtrain().

Adjusting the weights of the best situation based on a best fit for the observed data can be done with LMS (least mean squares). This balances the weight of the features that matter.

#### 1.2.5 The Final Design

Many machine learning systems can generalized to four generic modules: performance system, critic, generalizer, and experiment generator.

1. **Performance System** (PS) solves the given performance task using the learning function V. It takes a current game state and produces a new history game state.
1. **Critic** takes the PS output of a proposed game state as input and produces multiple output of training examples of the target function. It evaluates using the Vtrain() function.
1. **Generalizer** takes the multiple Vtrain() examples and uses a weighted method to evaluate for future best outcomes.
1. **Experiment Generator** takes as input the current learned function and outputs a new game state. A sophisticated generator would produce more than one state to explore a larger space. This one is simplistic with one state.

This problem could have been solved with numerous other methods. This is only one method among many to be discussed later.

### 1.3 Perspectives and Issues in Machine Learning

Machine learning involves searching a very large space of possible solutions to a problem and determining the one that bests fits the observed data along with any prior knowledge held by the learner. In the formal analysis, understanding the prior statement as related to the size of the solution space to be searched, the size of the available training examples, and the confidence we have in the general case against our training data will all be helpful to understanding limitations and pitfalls to our final solutions.

Some open questions:
1. 

