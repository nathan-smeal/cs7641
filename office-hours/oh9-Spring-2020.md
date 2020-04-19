# Office hours

* Be smart with figures, combine if needed
  * squeeze them in if possible, use margins smartly
  * [NIS] This probably means combining as many curve graphs as possible
* Don't need learning curves for neural net, talk a little bit about the training
  * more about the training time etc
  * need a reasonable enough hyper tuning
  * Talk about it is probably fine
* Should be able to do anaylsis even if gaussian?
  * Data set may not work well with all, should proibably point out if dataset doesnt matter
* Don't worry about LC if not using assignment
* test/train doesn't matter as much because unlabeled
  * except for neural net
  * if you get to neural net without splitting be careful with leakage(but talk about choice conciously)
  * Should do split first!  That was it's safe to use same set for training and clustering
* Be clear if you transform vs 
* Normalization - depends on data, talk about it either way probably
  * if you don't do you 
  * distance changes
  * normalize loses some information
  * Euclidean with it
* How do we use kurtossi
  * ICA sv PCA -> as you change number of components then the solution will change (ICA)
  * can choose number of components best for ICA
  * mean kurtosis of a component??
  * watch previous office hours for determining ideal
  * looking for an elbow after changing number of components
  * try to keep 75-80% of info but no fixed number, just be careful about throwing away info
  * reference reconstruction error for certain amount of components
* Should we leave scaling in?
  * do the same as assignment 1
  * inputs for neural should be the same
  * Talk about scaling when you talk about the dataset
* If do RCA do several trials to get average
  * anytime you do randomization do trials
* 