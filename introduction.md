# Introduction

This introduction defines **multimedia**, **multimedia analysis**, and **machine learning**, concepts which are central to TI2716-C.

## "Multimedia"

Multimedia content **combines** several "forms" of content such as text, audio, images, animation, video, and interactive content.

## Multimedia Analysis

Multimedia analysis is a type of **data science**: where data science **extracts knowledge** from *data*, multimedia analysis extracts knowledge from *multimedia data*.
* It takes a **top-down** perspective that looks first at the required **inputs** and **outputs** of the system, and chooses what techniques to use accordingly. (This is in contrast with the **bottom-up** perspective of the TI2716-A Signal Processing and TI2716-B Image Processing courses.)
* It involves a certain amount of **uncertainty**: no (multimedia) representation of the real world reflects it perfectly, which we must account for.

## Machine Learning

Machine learning is the science of getting computers to act without being explicitly programmed ([Andrew Ng](http://online.stanford.edu/course/machine-learning-1)).
* "Learning" means defining a mathematical model of the input that can be used to **make predictions**.
* A system has "learned" if it can make (to some degree accurate) predictions about **data it has not seen before**.

There are three broad categories of machine learning ([Wikipedia](https://en.wikipedia.org/wiki/Machine_learning#Types_of_problems_and_tasks)):
* **Supervised learning:** The system gets example input and output ("labels"), and has to figure out the rules that map inputs to outputs.
* **Unsupervised learning:** The system only gets example input, and has to figure out the structure in the input.
* **Reinforcement learning:** The system interacts with a dynamic environment where it has some goal (e.g. "safely drive from A to B"), and constantly gets feedback from its interaction with the environment.

Supervised and unsupervised learning are both relevant to TI2716-C, whereas reinforcement learning is out of the course's scope.
