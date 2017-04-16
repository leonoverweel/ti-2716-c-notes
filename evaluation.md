# Evaluating Multimedia Systems

Before diving into the specifics of different types of multimedia systems, we must first know how to evaluate them. This chapter covers **hold out evaluation**, **cross-validation**, and several **evaluation metrics** such as **accuracy**, **precision** and **recall**.

We evaluate multimedia systems to **objectively** determine how well they perform - "just playing" with a system (and its parameters) isn't good enough.
* Evaluation makes it possible to **compare** how a new algorithm performs compared to other algorithms - it is the only way to know whether the new algorithm is *state of the art*.

## Evaluating Supervised MMA Tasks

In many **supervised** multimedia analysis and machine learning tasks, such as [classification](introduction.md#classification), there is a **training** step. 
* In this *training* step, the system is fed some example **inputs** with **output labels**.
* The *evaluation* step then often involves a set of **test cases** and the corresponding **ground truth**.

These two settings (*training* and *evaluation*) are analogous, and require the same data: labeled inputs. It's also very important that the training and evaluation sets are representative of each other, to avoid creating a system that is not optimized for the data it's going to be evaluated on.

So the "trick" to evaluating multimedia systems in a supervised setting is in deciding how to split the underlying dataset.

### Hold-Out Evaluation

Hold-out evaluation involves training your system on one part of the data and evaluating it on another part.

1. *Randomly* divide the data set into a mutually exclusive **training set** and a **testing set**.
    * The fraction of data in the training set is called the **training factor**. A training factor of `0.8` (common) means 80% of the data is in the training set.
    * Never look at the testing set before it's time to evaluate
1. Train the system using the **training set**.
1. Run the **testing set** through the system and calculate an **evaluation metric** on the results.

### Cross-Validation

Repeat steps 1 - 3 for hold-out evaluation several times, and average the values for the evaluation metric to get the final evaluation.

### Evaluation Metrics

Most evaluation metrics are calculated from how much of the **testing data labels** fall into the following categories:

* **True positive (TP)**: The item was labeled `X`, and the ground truth for the item was also `X`.
* **False positive (FP)**: The item was labeled `X`, but the ground truth for the item was something other than `X`.
* **True negative (TN)**: The item was *not* labeled `X`, and the ground truth for the item was also not `X`.
* **False negative (FN)**: The item was *not* labeled `X`, but the ground truth for the item *was* `X`.

We can then calculate any of the following metrics:

* **Accuracy:** `accuracy = (TP + TN) / (TP + FP + TN + FN)` 
    * "How often is the classifier correct?"
* **Precision:** `precision = (TP) / (TP + FP)`
    * "What fraction of the instances retrieved by the classifier are relevant?"
* **Recall:** `recall = (TP) / (TP + FN)`
    * "What fraction of the relevant instances did the classifier retrieve?"

It is up to the system designer (you!) to decide what metrics are most important to the system. Make sure to decide (and document!) this decision *before* running tests.

## Evaluating Unsupervised MMA Tasks

Evaluating **unsupervised** multimedia analysis tasks, such as a **clustering** or a **segmentation**, are out of scope for TI2716-C.

---

[ [Home](README.md) ]
