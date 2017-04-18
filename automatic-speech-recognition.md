# Automatic Speech Recognition

Automatic speech recognition (ASR) is a form of **sequence recognition**, one of the the common [types of tasks in multimedia analysis and machine learning](introduction.md#types-of-tasks-in-mma-and-ml). It **segments** an audio signal into small parts and **classifies** them to form coherent words and sentences.

ASR uses the **noisy channel model**, which takes the assumption that the **intended** word has been somehow *scrambled* before it arrived at the system. Letters / phones may have been reordered, deleted, added, or replaced with other letters / phones. It's the system's job to *unscramble* the word: to find the **most likely** intended word out of all the possible words that could have been scrambled to form the word received by the system.

This works analogously on the **sentence level**, with scrambled *words*.

A speech recognition system contains several steps/ components:

1. **Feature extraction:** Extract feature vectors from audio segments (e.g. [MFCCs](music-information-retrieval.md#mid-level-feature-representations)).
1. **Acoustic models:** Probabilistically map audio vectors to phones.
1. **Pronunciation dictionary:** Probabilistically map a phone lexicon to words.
1. **Language model:** Determine the most likely sequence of words.

We explore the **acoustic models** and **language model** in more detail.

## Gaussian Classifier as Acoustic Model

In this step, we want to calculate the probability of the **feature vector** of the sound we heard occuring, given that a certain phone ("any distinct speech sound" ([Wikipedia](https://en.wikipedia.org/wiki/Phone_(phonetics)))) was said.

* This answers the question, "If the person said /p/, how likely is it that it would sound like what I just heard?"
* The most popular method to answer this question, which we cover here, is using [Gaussian mixture models](classification.md#genre-classification-using-bag-of-frames).
* Other methods include **neural networks**, **conditional random fields**, and **support vector machines**, which are out of scope for TI2716-C.

Since we use a *multivariate* Gaussian model, instead of a single mean and variance, we have a **vector of means** and a **covariance matrix**. In any dimension, a single Gaussian may not do a good job, so we use a **mixture of Gaussians** with multiple means and variances per dimension.

(The course gets more into the math, which I omit here. See lecture 3.4F.)

## N-Gram Language Model

In this step, we're interested in what word might **come next**: if I just heard the word "the", "horse" is more likely to be next than "a". Indeed, we model the **conditional probability** of a word given the **previous words**. Because we're *assigning a probability to a sentence*, we recognize this as a [language model](unigram-language-model.md#language-models).

There are several approaches to this, such as **counting words**, the **chain rule**, and **hidden markov models**.

### Counting Words

We can simply look at a large **corpus** of text, such as books indexed by Google. To calculate the probability of the word "hair" following the previous words "this is my," for example, we have the following calculation:

    P('hair' | 'this is my') = count('this is my hair') / count('this is my')

Unfortunately, this approach does not yield very good results in the real world, because it often results in `0`s or, worse, divisions by zero.

### Probabilistic Chain Rule

Here, we assume independence and use the probabilistic chain rule `P(A, B) = P(A | B) *  P(B)`. The probability of the word "wigs" following "I don't wear", for example, would be calculated as:

    P('I don't wear wigs') = P('I') * P('don't' | 'I') * P('wear' | 'I don't') * P('wigs' | 'I don't wear')

Unfortunately, we'll never be able to get enough data to calculate these probabilities for many long prefixes.

### N-Gram Model

So, we make the **Markov assumption** that only **`n` previous words matter**, and that the probability in question is independent of the earlier history.

* If we assume only one word matters, we use the **unigram** language model.
* If we assume two words matter, we use the **bigram** language model.
* If we assume three words matter, we use the **trigram** language model.
* Etc. for **n-gram** language models.

The **Maximum Likelihood Estimate** `MLE` for a **unigram** model then becomes:

    P(w_{n} | w_{n-1}) = count(w_{n-1}, w_{n}) / count(w_{n-1})

* This easily extands to `n`-gram models by looking at more than just the `n-1`th previous word.

**N-gram** language models can also be used to *generate* text, by continuously picking the most likely next word. Commercially, this could form the backend to something like the word prediction on your iPhone.

### Smoothing

If a bigram never appears, should it have a probability of zero? No - just because it's not in your training data, doesn't mean it can't exist; it might just be a rare event.

Several techniques exist to counter the errors this might cause: we could simply add `1` to every count. With **Laplace smoothing**, where `N` is the total number of tokens and `V` is the total number of types, the probability would then be:

    P(w_{n} | w_{n-1}) = (count(w_{n-1}, w_{n}) + 1) / (N + V)

In practice, more sophisticated techniques are used, which are out of the scope of TI2716-C.

---

[ [Home](README.md) ]
