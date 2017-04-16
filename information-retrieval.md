# Information Retrieval 

"Information retrieval is **finding** material of an **unstructured** nature that satisfies an **information need** from within **large collections**." (IRBook)

* Such large collections include the world wide web, a personal hard drive, academic publications, etc.
* The user input, an **information need** is inside her head; she translates it to a **query** (in the form of text, a photograph, a drawing, or some other media); the system must then find the most relevant documents to return to her.

A typical information retrieval system is structured as follows:

![Information retrieval system](http://article.sapub.org/image/10.5923.j.se.20120202.04_001.gif)

(Image source: [Scientific and Acedemic Publishing](http://article.sapub.org/image/10.5923.j.se.20120202.04_001.gif))

## Vector Space Model

### The Term-Document Matrix

Analogous to the bag-of-words model in text, we create the **term-document matrix** that contains the **frequencies** `f_{t,d}` at which each **term** `t` occurs in each **document** `d`.

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

---

[ [Home](README.md) ]
