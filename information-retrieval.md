# Information Retrieval 

"Information retrieval is **finding** material of an **unstructured** nature that satisfies an **information need** from within **large collections**." (IRBook)

* Such large collections include the world wide web, a personal hard drive, academic publications, etc.
* The user input, an **information need** is inside her head; she translates it to a **query** (in the form of text, a photograph, a drawing, or some other media); the system must then find the most relevant documents to return to her.
* The challenge of retrieval is to design and implement a relevance score that reflects a user's judgments of relevance.

Although they are often used interchangably, there is a difference between **retrieval** and **ranking** (slides):
* **Ranking:** Given a **test item**, return an list of similar items from a background collection ordered according to similarity score. (See [introduction](introduction.md#ranking).)
* **Retrieval:** Given a **query** that represents a **user information need**, return a list of relevant items ordered according to relevance score. 

A typical information retrieval system is structured as follows:

![Information retrieval system](http://article.sapub.org/image/10.5923.j.se.20120202.04_001.gif)

(Image source: [Scientific and Acedemic Publishing](http://article.sapub.org/image/10.5923.j.se.20120202.04_001.gif))

The **retrieval functions** (or **document ranking**) are responsible for finding documents in the **document collection** that most closely match our **query**. It can be implemented using several techniques, such as the [vector space model](vector-space-model.md) or the [unigram language model](unigram-language-model.md), depending on the application.

Recall that we can also objectively [evaluate information retrieval systems](evaluation.md#evaluating-information-retrieval-systems).

---

[ [Home](README.md) ]
