## Source

CACM

http://dl.acm.org/citation.cfm?id=2347755

## Problem

Developing successful machine learning applications requires a substantial amount of “black art” that is hard to find in textbooks. This article summarizes twelve key lessons that machine learning researchers and practitioners have learned.

## Motivations

LEARNING = REPRESENTATION + EVALUATION + OPTIMIZATION

## Solution

1. GENERALIZATION

To keep training data and test data separate. Cross-validation: dividing data into many folds, picking up one and testing the rest, averaging to get the final score.

2. DATA ALONE IS NOT ENOUGH

Learning is more like farming, which lets nature do most of the work. Farmers combine seeds with nutrients to grow crops. Learners combine knowledge with data to grow programs.

3. OVERFITTING HAS MANY FACES

Bias is a learner’s tendency to consistently learn the same wrong thing. Variance is the tendency to learn random things irrespective of the real signal. We can use cross-validation, regularization--penalize classifiers with more structures, and statistical test like chi-square

4. INTUITION FAILS IN HIGH DIMENSIONS

The similarity-based reasoning that machine learning algorithms depend on (explicitly or implicitly) breaks down in high dimensions.

5. THEORETICAL GUARANTEES ARE NOT WHAT THEY SEEM

This is because the bounds obtained in this way are usually extremely loose.

6. MORE DATA BEATS A CLEVERER ALGORITHM

As a rule, it pays to try the simplest learners first. Learners can be divided into two major types: those whose representation has a fixed size, like linear classifiers, and those whose representation can grow with the data, like decision trees.

7. LEARN MANY MODELS, NOT JUST ONE

Ensembles:

- bagging, generate random variations of the training set by resampling.

- boosting, training examples have weights, and these are varied so that each new classifier focuses on the examples the previous ones tended to get wrong.

- stacking, the outputs of individual classifiers become the inputs of a “higher-level” learner that figures out how best to combine them.

8. SIMPLICITY DOES NOT IMPLY ACCURACY

We saw one counter-example in the previous section: model ensembles. The generalization error of a boosted ensemble continues to improve by adding classifiers even after the training error has reached zero.

9. REPRESENTABLE DOES NOT IMPLY LEARNABLE

Therefore the key question is not “Can it be represented?”, to which the answer is often trivial, but “Can it be learned?” And it pays to try different learners (and possibly combine them).

10. CORRELATION DOES NOT IMPLY CAUSATION

The practical points for machine learners are two. First, whether or not we call them “causal,” we would like to predict the effects of our actions, not just correlations between observable variables. Second, if you can obtain experimental data (for example by randomly assigning visitors to different versions of a Web site), then by all means do so.