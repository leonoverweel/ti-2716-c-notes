# Information Retrieval Using the Vector Space Model

The **vector space model** is one way to implement the **document ranking** or **retrieval functions** in [information retrieval](information-retrieval.md).

## The Term-Document Matrix

Analogous to the bag-of-words model in text, we have the **term-document matrix** that contains the **frequencies** `f_{t,d}` at which each **term** `t` occurs in each **document** `d`.

* This destroys the *ordering relationships* between words.
* Even without this, it captures the **topic** or **style** of a document.

Such a term-document matrix looks like this, where `f_{t,d}` is some nonnegative integer:

| | **Document 1** | **Document 2** | **...** | **Document n** |
|---|---|---|---|---|
| **Term 1** | `f_{1,1}` | `f{1, 2}` | ... | `f{1, n}` |
| **Term 2** | `f_{2,1}` | `f{2, 2}` | ... | `f{2, n}` |
| **Term 3** | `f_{3,1}` | `f{3, 2}` | ... | `f{3, n}` |
| **...** | ... | ... | ... | ... |
| **Term m** | `f_{m,1}` | `f{m, 2}` | ... | `f{m, n}` |

We represent documents as a set of **indexing terms** that "[capture] the essence of the topic of a document" ([Wikipedia](https://en.wikipedia.org/wiki/Index_term)).

* These terms reside in the **term-document matrix**.
* Often, indexing terms are just words or phrases from the documents.
* Selecting these terms carefully is important, as they have a large impact on the information retrieval system's performance.

## The Vector Space Model

The vector space model is an algebraic model for representing multimedia data as vectors of identifiers, such as index terms ([Wikipedia](https://en.wikipedia.org/wiki/Vector_space_model)).

* Documents are represented as **vectors**, where each dimension of the vector corresponds to an **indexing term**.
* In each dimension, we store the **count**, or **term frequency** `tf`, of how many times that indexing term occurs in the document.
    * We use `tf` because it captures the *representativeness* of a term in the document.
* Essentially, these are the columns of the term-document matrix.

It's then possible to also translate a user's **query** into such a vector, and to **calculate the distance** between each document in the document store ("document representation" in the diagram above). The `n` documents with the smallest distance from the user's query are then the **top-n ranking** / **result list** ("retrieved documents" in the diagram above).

* A popular distance/ similarity measure for the vector space model is [cosine similarity](background.md#cosine-similarity).

## Beyond Simple Term Frequency

There are several techniques beyond just comparing documents by their term frequency vectors, such as:

* Using the **log frequency** instead of plain **count**.
    * It's more important that a term occurs once vs. never, than that it occurs 42 times instead of 41 times.
* Weighing each term by its **inverse document frequency** `idf_t`
    * `idf_t = log(N / df_t)`, where `df_t` is the number of documents that contain the term.
    * Weighing by `idf_t` helps capture what is "unique" about a document compared to other documents, by discriminating against common words like "the" and "a". 
* **Normalizing** the document vectors.
    * This increases robustness against varying lengths of documents.
* Using the **boolean term frequency** instead of plain **count**.
    * `if tf > 0: 1; else: 0`
    * This is an alternative to the log frequency.

As usual, the system goals determine which of these techniques are appropriate to use.

---

[ [Home](README.md) ]
