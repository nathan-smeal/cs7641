ML is the ROX
=============


Definition of ML
----------------

Machine learning theory about how well data can be statistically
modeled. Machine learning is practically about building machines which
can learn from data.

There are three types of ML: supervised learning, unsupervised learning,
and reinforcement learning.

Supervised learning
-------------------

Supervised learning gleans "information" from labeled data to label new
unlabeled data. This is simply discrete function approximation.
Supervised learning/function approximation must make assumptions about
the given data to *generalize* to new data.

[Note on] Induction and deduction
---------------------------------

* *Induction* takes specific examples to create a general rule.
* *Inductive bias* is necessary to come up with "useful" generalizations. (set of assumptions that the learner uses to predict outputs given inputs that it has not encountered)
* *Deduction* takes a general rule and applies it in specific cases.

Unsupervised learning
---------------------

Given inputs with no labels, derive some structure using the
relationships between the inputs. Often a summarization of data into
clusters. In practice, unsupervised learning is useful even in
supervised contexts to gain insight into the data.

Reinforcement learning
----------------------

Learning from delayed supervision. For example: playing a [turn-based]
game [with potentially non-deterministic environmental factors] where
you find out whether you have won or lost near the end. Somewhat
difficult.

Comparison of these parts of ML
-------------------------------

All learning is "optimization." SL wants to label data well. RL wants to
score well. UL has scientist-imposed criteria for correctness.

Optimization subset| Typical goals
-|-
SL| Labels Data Well
RL | behavior scores well
UL | Clusters scores well

All of it boils down to DATA, Data, DATA

Often ML developer thinks more about the data rather than the algorithms.