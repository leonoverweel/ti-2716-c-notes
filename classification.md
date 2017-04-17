# Classification

**Classification** is one of the common [types of tasks in multimedia analysis and machine learning](introduction.md#types-of-tasks-in-mma-and-ml). It takes a **data point** as input, and assigns it a **class label** as output.

In this chapter, we look at **music genre classification** using the **bag of frames** approach, and the **language model** as a **naive baysian classifier** for text. 

## Genre Classification Using Bag of Frames

We use a bag of frames approach and first create a model. We collect audio content for each genre, and apply the following steps:

1. Split **labeled** audio content into short **segments** that are assumed to be **stable**.
1. Apply a feature **descriptor** such as an [MFCC](music-information-retrieval.md#mid-level-feature-representations) to each segment to get **feature vectors**.
1. Create a **bag of audio vectors** from the audio descriptors.
    * This is a "bag of" audio vectors because the time information is lost.
1. Using the **means** and **variances** of the positions of these vectors in n-dimensional space, create a **representative multivariate gaussian model** for the genre.
    * Sometimes we also use a **mixed gaussian model** if our data has multiple clusters in some dimensions. (Think of the heights of humans - there will be a peak at the average child's height, average woman's height, and average man's height.)

Once we have trained the model, we can calculate the audio vectors for small segments of a song to classify. For each segment's vector and each genre's gaussian model, we calculate the probability that that gaussian model produced the vector. We aggregate these to see which genre the song belongs to.

## Naive Bayes' Classifier for Text

Using the [unigram language model](unigram-language-model.md#unigram-language-model), we can calculate the probability that some source material "generated" a particular sentence.

An obvious extension to this is, instead of returning a ranked list of possible results, **classifying** the sentence as belonging to the source with the highest probability.

---

[ [Home](README.md) ]
