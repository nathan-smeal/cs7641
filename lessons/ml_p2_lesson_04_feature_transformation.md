# Lesson 04: Feature Transformation

The problem of pre-processing a set of features to create a new (smaller? more compact?) feature set, while retaining as much (relevant? useful?) information as possible.

(Feature selection is a subset of feature transformation, which only takes a *subset* of features.)

$$x\sim \mathbb{F}^n \rightarrow \mathbb{F}^m$$

Where usually $m<n$ and the transformation linear ($P_x^T$)

## Feature Transformation Motivation

**Example: information retrirval from documents.**

Features: words, a lot of words. They are good indicators?

* Polysemy: one word can mean many things. This can cause false positive.
* Synonomy: many words can mean one thing. This can cause false negatice.

So, words are insufficient indicator features.

**Solution**: transformation, from words to new feature space.

## Principal Components Analysis

*From Eigen Problem*

Find the components in features that:

* Maximizes the variance
* Are mutually orthogonal

### Properties

* Global algorithm: all the new features they find have a big global constraint - they are mutually orthogonal.
* Best reconstruction: No information loss in transformation (when keepig all the principal components).
  + It minimizes the L2 error if we pick less principal components.
* Eigenproblem: Eigen values are monotonically non-decreasing and thus the dimensions corresponding to the small eigenvalues can be dropped.
  + It transform to the space where feature selection can work.
  + Eigenvalue 0 -> no variance on that dimension -> irrelevant feature
* It is well-studied -> there are fast algorithms.
* Really help classification? Maybe not, it is like **Filtering** algorithm.

## Independent Components Analysis

* PCA: finding correlations, by maximizing the variance. It gives you the ability to do reconstruction.
* ICA: trying to maximize the independence. Find the **linear transformation** of original feature space to a new space s.t. the new features are **statistically mutually independent**,
  + Knowing the value of one of the new features won't give any prediction another.
  + i.e. mutual information $I(y_i,y_j) = 0$.
  + It will maximize the mutual information $I(X,Y)$.
* ICA also makes assumption that the new features are highly non normally-distributed.

The ICA is trying to from the observables find the independent hidden variables which cause the observables in a linear way.

### Example: Blind source Separation (Cocktail Party Problem)

* Hidden variables: The voices of people talking.
* Observables: The recordings of the microphones.

The microphones' recordings are just the linear combination of the voices.

## PCA vs ICA

### Properties

property                              | PCA | ICA
--------------------------------------|-----|----
mutually orthogonal                   | Y   | N
mutually independent                  | N   | Y
maximal variance                      | Y   | N
maximal mutual information ($I(X,Y)$) | N   | Y
ordered features                      | Y   | N
bag of features                       | Y   | Y

PCA tends to find the components that are uncorrelated, which is not the same as finding the independent components in ICA. But in the particular case where all data is Gaussian, finding uncorrelated turns out to be finding the independent.

PCA tends to find a bunch of orthogonal Gaussians. ICA tries to find the statistically independent random variables. From Central Limit Theorem, sum (linear combination) of independent random variables gives rising to normal distribution in the limit. So ICA should not be maximizing the variances, otherwise the sum will be Gaussians.

So PCA tends to summing up the independent things but ICA tries to teasing apart them. So ICA should not find the components that look like Gaussian.

> Intuitively speaking, the key to estimating the ICA model is nongaussianity.

* Blind Source Separation Problem: ICA almost is designed for this but PCA does bad.
* **Directional**; PCA gives the same answer if the data matrix is rotated 90 degree. But ICA gives a totally different answer. So ICA is highly directional and PCA is much less so.
* Run algorithm on faces:
  + PCA gives: brightness, average face (eigen face). -> tend to find the global features.
  + ICA finds: nose selectors, eyes selectors, mouth selectors, hair selectors. -> tends to find the local features.
* Run algorithm on natural scenes:
  + PCA: brightness, average scenes.
  + ICA: edges (independent fundamental elements)
* Run algorithm on documents:
  + ICA: topics.

## Alternatives

### RCA: Random Components Analysis

Generate random directions and do projection.

It WORKS!

* It reduces the number of dimensions, which helps with the curse of dimensionalities.
* The projection at least captures some of the correlations.
* It is fast/easy/cheap.

### LDA: Linear Descriminant Analysis

Find a projection that descriminate (find a linear transformation) based on the labels.

It's just like the supervised learning.















...
