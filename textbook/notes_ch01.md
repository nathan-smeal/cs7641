# Machine Learning
Tom Mitchell @ 1997

## Chapter 1: Introduction

ML is foundationally multi-disciplinary.

### 1.1 Well-posed learning problems
--------------------------------

Definition: A computer program is said to learn from experience E with respect to some class of tasks T and performance measure P, if its performance at tasks in T, as measured by P, improves with experience E.

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

