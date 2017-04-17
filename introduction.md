# Introduction

**Relevant lectures:** 3.1T, 3.1F

This introduction defines **multimedia**, **multimedia analysis**, and **machine learning**, concepts which are central to TI2716-C.

## Multimedia Analysis (MMA)

Multimedia content **combines** several "forms" of content such as text, audio, images, animation, video, and interactive content.

Multimedia analysis is a type of **data science**: where data science **extracts knowledge** from *data*, multimedia analysis extracts knowledge from *multimedia data*.
* It takes a **top-down** perspective that looks first at the required **inputs** and **outputs** of the system, and chooses what techniques to use accordingly. (This is in contrast with the **bottom-up** perspective of the TI2716-A Signal Processing and TI2716-B Image Processing courses.)
* It involves a certain amount of **uncertainty**: no (multimedia) representation of the real world reflects it perfectly, which we must account for.

## Machine Learning (ML)

Machine learning is the science of getting computers to act without being explicitly programmed ([Andrew Ng](http://online.stanford.edu/course/machine-learning-1)).
* "Learning" means defining a mathematical model of the input that can be used to **make predictions**.
* A system has "learned" if it can make (to some degree accurate) predictions about **data it has not seen before**.

There are three broad categories of machine learning ([Wikipedia](https://en.wikipedia.org/wiki/Machine_learning#Types_of_problems_and_tasks)):
* **Supervised learning:** The system gets example input and output ("labels"), and has to figure out the rules that map inputs to outputs.
* **Unsupervised learning:** The system only gets example input, and has to figure out the structure in the input.
* **Reinforcement learning:** The system interacts with a dynamic environment where it has some goal (e.g. "safely drive from A to B"), and constantly gets feedback from its interaction with the environment.

Supervised and unsupervised learning are both relevant to TI2716-C, whereas reinforcement learning is out of the course's scope.

## Types of Tasks in MMA and ML

We encounter several types of tasks in multimedia analysis and machine learning, such as **information retrieval and filtering**, **segmentation**, **clustering**, **ranking**, **classification**, **regression**, and **sequence recognition**. Many of these are relevant to TI2716-C, and are covered in more detail below.

### Information Retrieval and Filtering

Some people group information retrieval (IR) and information filtering (IF), but they have some distinctions:

| **IR/IF** | **Input** | **Input characteristic** | **Collection** |
|---|---|---|---|
| Information retrieval | Query | Changes often and quickly | Relatively static |
| Information filtering | Profile | Changes infrequently and slowly | Relatively dynamic |

#### Information Retrieval

An information retrieval system is used to obtain multimedia resources relevant to an information need from a collection of multimedia data ([Wikipedia](https://en.wikipedia.org/wiki/Information_retrieval)). 

Information retrieval is covered in the following chapters:

* [Information Retrieval](information-retrieval.md)
* [IR Using the Vector Space Model](vector-space-model.md)
* [IR Using the Unigram Language Model](unigram-language-model.md)
* [Multimedia Information Retrieval](multimedia-information-retrieval.md)
* [Music Information Retrieval](music-information-retrieval.md)

#### Information Filtering

An information filtering system selects a subset of items to show to the user: its goal is to increase the "signal-to-noise" ratio. To do this, the system compares the user's profile some reference characteristics ([Wikipedia](https://en.wikipedia.org/wiki/Information_filtering_system)).

Information filtering is covered in the following chapters:

* [Recommender systems](recommender-systems.md)

### Segmentation

Segmentation is an **unsupervised** technique that assigns similar regions of content to "segments". Examples include:

* **Image segmentation**, where we split an image into segments that could be [individual items](https://www.mathworks.com/content/mathworks/www/en/discovery/image-segmentation/jcr:content/mainParsys/image_2.adapt.full.high.jpg/1469940839538.jpg) (see image), [background vs. foreground](https://www.mathworks.com/matlabcentral/mlc-downloads/downloads/submissions/41967/versions/2/screenshot.jpg), or [different parts of a human body](http://www.morethantechnical.com/wp-content/uploads/2010/05/GMM-GC-segmentation.png), for example.

    ![individual items](https://www.mathworks.com/content/mathworks/www/en/discovery/image-segmentation/jcr:content/mainParsys/image_2.adapt.full.high.jpg/1469940839538.jpg)
* **Text segmentation**, where we split some text into meaningful segments such as words, sentences, or topics.
* **Speech segmentation**, where we split audio up into individual phones, syllables or words.

(Image source: [MathWorks](https://www.mathworks.com/content/mathworks/www/en/discovery/image-segmentation/jcr:content/mainParsys/image_2.adapt.full.high.jpg/1469940839538.jpg))

### Clustering

Clustering is an **unsupervised** technique that assigns similar items into groups based on some [similarity measure](background.md#similarity-and-distance-measures). These items are usually represented as n-dimensional vectors of numbers.

![Clustering](https://home.deib.polimi.it/matteucc/Clustering/tutorial_html/images/clustering.gif)

(Image source: [Politecnico Milano](https://home.deib.polimi.it/matteucc/Clustering/tutorial_html/images/clustering.gif))

### Ranking

Ranking is an **unsupervised** technique (classically) that produces **a list of items** ordered (high to low) by their similarity to a test item. This relevance is calculated using [similarity measures](background.md#similarity-and-distance-measures) between the test item and the items in the collection.

### Classification

Classification is a **supervised** technique (classically) that takes a **data point** as input, and assigns it a **class label** as output. I like to think of classification as answering the question: "To which cluster does this (new) data point belong?"

A **perceptron** is a single-layer neural network that acts as a classifier.

Classification is covered in the following chapters:

* [Classification](classification.md)
* [Evaluating Multimedia Systems](evaluation.md)

### Regression

Regression is a **supervised** technique to relate variables to each other. It is out of scope for TI2716-C.

### Sequence Recognition

Sequence recognition is a **supervised** technique (classically) that performs simultaneous **segmentation** and **classification**. It could, for example, take spoken audio as input and produce a list of spoken words as output. 

---

[ [Home](README.md) ]
