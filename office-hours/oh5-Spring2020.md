# Notes on recorded Office hours #5

NOTE: `F{number}` is a reference to a piazza post, it shouldn't be required but just listed as a reference for more info.

the goal is that these notes are thorough enough to help in other semesters (AS SUPPLEMENTATION AS THINGS CAN CHANGE!!!)

This is mostly an exercise in recall for myself, the notetaker but make could help as a searchable resource for others.

## Raw notes from recording

- Note this is the first OH after Assignment 1 so should cover a lot for A2
- Weighting between the 2 parts?
  - Won't tell us specifics
  - Part of NN portion is already done
  - Time "as long as you need to"
- F2 -> mlrose-hiive is fine
  - Most of the forks are tweaking grid search
  - Can't be writtne specifically with exploration
- ABAGAIL or mlrose is fine
  - mlrose the reason for some of the forks is subtle bugs
  - mlrose is a little rough 
- How to tweak for GA/MIMIC?  Change hypers so iterations are the same
  - Common pitfall is setting iterations at like 100, and compare.  Some need a lot
  - Try to see whole behavior or each
  - there will be numerous comparisons and metrics to compare alg perf
- Should we be comparing precision, f1 score recall etc?
  - Mostly just relevant to the neural network part
  - hopefully already justified why using that metric in assign 1
- Retrain vs freeze?
  - main point to compare without freeze to see how they converge
    - what learns better faster and more accurately
- F9 ->Mitchel Chapter 7, comparing the computational complexity of some class
  - can you compose it of known complexity?
  - Assuming some representation
  - This is kind of in the weeds, not assignment related
  - Michael in lecture uses hypothesis space which is similar to capital C concept class
    - hypothesis class is what we formulate which is something to encode concept class
    - never actually know C concept class
- mlrose having bad results with 4 peaks mimic
  - how many times are you running it in experiment?
  - need several iterations and average the behavior (trials)
  - not real complicated, these problems have a fixed structure thus mimic should wokr better
  - if mimic is not utilizing these then examine hypers for example
  - might have been an issue with mlrose (maybe should use  abagail because it's more mature
- DON'T JUST DO 1 run
  - make sure properly managing random seed, don't reuse obv
  - do at least 10-20 runs in first attempts
- F13 -> 8 queens or knapsack in mlrose or define our own
  - don't need to define but can, but don't(bad idea imo - NIS)
  - sci-kit does more hyper than mlrose
    - Most things don't penalize but 
    - Do we need to stick to same hypers from first assignment?
      - should keep architecture the same
      - Others don't matter as much, learningn rate is something can tune
- > The sklearn based NN using SGD is performing way better than mlrose based NN using gradient descent for my dataset. 

1> Firstly, is this comparison required for Assignment 2. ? If required,  is it really an apples to apples comparison --> meaning, are the underlying SGD in sklearn and gradient descent in mlrose using the same algorithm and governed by same HPs  2> Also do we need to stick to the same HPs as in first assignment like the number of hidden layers and learning rate for the NN while testing with 3 optimizers from assignment 2, even when we are using mlrose based NN?
  - "1) It's not required. Most students will just transfer the network architecture over or you can make a new baseline in mlrose -- I think the first is easier. There's no need to to compare your A1 NN in scikit-learn to A2 NN in mlrose. I don't think I can comment on implementation-specific questions, it might be due to some subtle difference in your tuning. Note that the mlrose implementation seems a lot more limited in terms of HP tuning.  1) You're keeping the hidden layer the same. The assumption is that your NN is tuned so you're essentially just comparing backprop to the randomized methods for optimizing weights. You can study the effects of learning rate (in the context of mlrose where it's referring to step size). There's no reason to study that for backprop because you've already done that in A1."
- Which lectures on the mid term?  reference appropriate FAQ post
  - Can't say anything else
- Fitness is important, iterations, wall time, hyper tuning for graphs
- again test set should not be used to the end
  - don't pass along all the data for learning curve
  - what does this question have to do with assignment 2
- f21 -> multiple choice etc?  Bunch of different formats
- f22 -> different architectures one very complex one not for A1 NN artch.  Can use diff than best if justified
- assignment 2 prefers bit strings, the helper
  - discrete mehods, bit strings easy to work with
  - see mitchell chapter 9 if want more details
- make sure you don't use 2 problems to highlight the same algortihms   
  - likely lose big chunk of grade because will miss a requirement (hgihlighting each)