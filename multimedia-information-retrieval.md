# Multimedia Information Retrieval

This chapter explores **multimedia information retrieval**, specifically **texture recognition** and **bag of features**.

To move towards multimedia information retrieval, we slightly adapt the definition of [information retrieval](information-retrieval.md): "Multimedia information retrieval is **finding** ~material~ **multimedia** of an **unstructured** nature that satisfies an **information need** from within **large collections**." (IRBook)

We can come across queries of several kinds:

* Textual **keywords** (such as in Google Search or YouTube Search)
* **Query by examples** (such as Goolge Search By Image)
* **Multimodal** queries

## Texture Recognition

Texture is characterized by the repetition of (small) basic elements called **textons**. Much like in the [vector space model](information-retrieval.md#the-vector-space-model) for text documents, we can create a **vector** of **counts** of the occurrences of different textons in an image to characterize it.

We can then use compare the vector representation of that image to the vector representations of the training images to find the closest match and assign the test image to the texture class of that match.

## Bag of Features

Bag of Features is the image equivalent of the **Bag of Words** / [vector space model](information-retrieval.md#the-vector-space-model) approach to text information retrieval. It involves the following steps:

1. Extract features
    * These could be [SIFT](background.md#sift) **descriptors**.
    * We can't "just" put these features into a vector space model: they are too specific, so we have to cluster them first.
1. Learn "visual vocabulary"
    * Here, we cluster SIFT descriptors into "visual words." These essentially form the different **indexing terms**. 
1. Feature quantization using visual vocabulary
    * We now count instances of the **visual words**, or **features** (confusingly, SIFT features are also called features).
1. Represent images by frequencies 
    * We represent the image as a vector of visual word frequencies.

Now, we can easily compute the [similarity or distance](background.md#similarity-and-distance-measures) between a query image's visual word frequency vector and the different vectors in our collection to find the closest match.

---

[ [Home](README.md) ] 
