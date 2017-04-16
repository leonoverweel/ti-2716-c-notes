# Recommender Systems

**Lectures covered:** 3.1T

Recommender systems are a type of **information filtering** system that attempt to predict **user preferences**. Concretely, they aim to predict the rating or score some **user** would give to an **item**. They use this rating to provide the user with some sort of recommendation.

## Typical Tasks of Recommender Systems

The "recommendations" predicted by recommender systems can come in several forms:

* **Rating prediction:** Infer what a user's rating would be for a specific item.
* **Top-N recommendation:** Predict an ordered list of the top items that a user might prefer.
* **Reciprocal recommendation:** Find matches between users based on their expected preference for each other.

Commercially, recommender systems are used in search engines (Google, YouTube), and generally in "you might also like" systems such as suggested follows on Twitter, autoplay on YouTube, similar movies on Netflix, and "frequently bought together" items on Amazon.

To complete these tasks, recommender systems can use the **user-item matrix** to perform **collaborative filtering**, or apply techniques such as content-based prediction or dimensionality reductions. The former are covered below, and the latter two are out of scope for TI2716-C.

## The User-Item Matrix

The user-item matrix plays a central role in recommender systems. It contains the set of ratings `r_{i,j}` that user `i` (from the set of users `U`) has assigned to item `j` (from the set of items `I`).

* Ratings can be...
    * **Explicit**, if the user is purposely giving a rating to an item (such as a movie grade from 1 to 5, a "Like" on Facebook, or a thumbs-up on YouTube), or
    * **Implicit**, if the user's behavior is treated as rating (such as a purchase on Amazon or a click on a Google search results list).
* Since not every user has rated every item, there are lots of empty entries. The matrix can be highly sparse in real life.
* Π (Pi) is the "true" user-item preference matrix, containing the real ratings every user would give every item. It is unknown and unknowable in real-life situations.

A user-item matrix looks like this, where `r_{i,j}` is some rating, usually in the form of a number:

| | **Item 1** | **Item 2** | **...** | **Item n** |
|---|---|---|---|---|
| **User 1** | `r_{1,1}` | `r_{1,2}` | ... | `r_{1,n}` |
| **User 2** | `r_{2,1}` | `r_{2,2}` | ... | `r_{2,n}` |
| **User 3** | `r_{3,1}` | `r_{3,2}` | ... | `r_{3,n}` |
| **...** | ... | ... | ... | ... |
| **User m** | `r_{m,1}` | `r_{m,2}` | ... | `r_{m,n}` |

### Challenges

Some of the challenges in creating a recommender system using a user-item matrix include:

* **Sparsity:** The user-item matrix can be highly sparse, which the system has to take into account.
* **Interpreting the lack of a rating**: Did this user not rate this item because she didn't like it? Does this user only angrily assign low ratings to items he does not like?
* **Cold start:** When the system is first starts up, the user-item matrix is empty and it is difficult to make any initial predictions.
* **Little overlap:** Not all users rate the same items, and there may be little overlap between the items different users rate, especially if there are relatively many items and few users.
* **Noise:** Not all ratings are reliable.

## Collaborative Filtering

Collaborative filtering is a class of methods for making automatic predictions (**filtering**) about the preferences of a user by collecting preferences from many users (**collaborating**). It makes the assumption that if user `A` likes items `X` and `Y`, then user `B`, who also likes item `X`, will probably also like item `Y` ([Wikipedia](https://en.wikipedia.org/wiki/Collaborative_filtering)).

There are two types of collaborative filtering that can be used to make a recommendation for user `i`:
* **User-user collaborative filtering:** Find users similar to user `i` (in terms of how they rate items), and use those users' ratings to make a prediction for user `i`.
* **Item-item collaborative filtering:** Find similarities in items (in terms of which users interact with them), and use those similarities to make a prediction for user `i`.

The former is covered more in-depth in TI2716-C.

### User-User Collaborative Filtering

Using user-user (also known as *memory-based*) collaborative filtering to predict the rating by user `i`'s for item `j` consists of two steps:

1. **Finding the neighborhood:** Find users that have similar past rating behavior to user `i`. These users are called *neighbors*.
1. **Predicting the rating:** Use the neighbors' ratings to predict user `i`'s rating for item `j`.

This prediction can be made using the user-user collaborative filter formula, which takes an average of all the ratings other uses have made for item `j`, weighted by their similarity to user `i` (using [Pearson correlation](background.md#pearson-correlation) or [cosine similarity](background.md#cosine-similarity)). See [Wikipedia's explanation](https://en.wikipedia.org/wiki/Collaborative_filtering#Memory-based).
