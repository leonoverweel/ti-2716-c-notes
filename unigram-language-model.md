# Information Retrieval Using the Unigram Language Model

The vector space model is another way to implement the **document ranking** or **retrieval functions** in [information retrieval](information-retrieval.md).

## Language Models

A **language model** assigns a **probability** to a **sentence**. Some of its applications include:

* **Automatic Speech Recognition (ASR):** Which of these possible textual interpretations of the sounds is more likely?
    * "Stand on the folders of clients" vs "Stand on the shoulders of giants" vs "Stan and the boulders of my aunts."
* **Text Input:** Letter-based language models speed up text input with number pad.
    * The algorithm interprets each stroke as the continuation of the most probable letter string.
    * This can also be implemented as dynamic touch target resizing.

A language model always represents some **human language source**, in the form of text produced by a *certain person*, on a *certain topic*, or for a *certain reason*. The model calculates the probability that some string of words was "generated by" this source.

To train a language model, you need to:

1. Choose a **language source**.
    * e.g. Jane Austen.
1. Choose a **training set**.
    * e.g. books by Jane Austen.
1. Determine the **vocabulary**.
    * e.g. all distinct words in the training set.
1. Estimate the necessary **probabilities**.
    * e.g. the count of a word divided by the total word count.

## Unigram Language Model

In a **unigram language model**, we calculate the probability of a sentence by simply multiplying the model's probabilities for the words in the sentence together.

* This is based on [Bayes' rule](background.md#bayes-rule), but we assume our prior for each sentence is equal, so we can simplify to just the multiplication.

We train **one language model** for **each document** in the collection. We can then take the user's **query** and calculate the **probability** that it was generated by each of the models. The `n` documents with the highest probability of having generated the sentence are then the **top-n ranking** / **results list**.

[ [Home](README.md) ]