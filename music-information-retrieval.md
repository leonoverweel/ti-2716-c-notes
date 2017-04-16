# Music Information Retrieval

**Relevant Lectures:** 3.2T (guest lecture by [Cynthia Liem](http://mmc.tudelft.nl/users/cynthia-liem))

This chapter introduces information retrieval through the lens of its application to music. We first look at **audio music processing**, then at some **case studies**, and finally note that music can also be a **multimedia** experience.

## Audio Music Processing

This chapter focuses on **content-based music processing** based on audio signals, and does not consider advanced music theory or symbolic representations of music.

### Spectrograms

"A spectrogram is a visual representation of the spectrum of frequencies in a sound or other signal as they vary with time" ([Wikipedia](https://en.wikipedia.org/wiki/Spectrogram)). It looks like this:

![Spectrogram](https://upload.wikimedia.org/wikipedia/commons/c/c5/Spectrogram-19thC.png)

(Image source: [WikiMedia Commons](https://upload.wikimedia.org/wikipedia/commons/c/c5/Spectrogram-19thC.png))

### Music Fundamentals

#### Acoustic Concepts

* **Pitch** is "the quality that makes it possible to judge **sounds as 'higher' and 'lower'** in the sense associated with music" ([Wikipedia](https://en.wikipedia.org/wiki/Pitch_(music))).
    * An **overtone** is "a 'partial wave' that can be either a harmonic other than the fundamental, or an inharmonic partial. A harmonic frequency is an integer multiple of the fundamental frequency" ([Wikipedia](https://en.wikipedia.org/wiki/Overtone#Musical_usage_term)).
* **Timbre** is "the perceived sound quality of a musical note, sound, or tone that **distinguishes different types of sound production**, such as choir voices and musical instruments, such as string instruments, wind instruments, and percussion instruments" ([Wikipedia](https://en.wikipedia.org/wiki/Timbre)).
* **Loudness** is "the characteristic of a sound that [correlates to the sound's] physical strength (amplitude)" ([Wikipedia](https://en.wikipedia.org/wiki/Loudness)).
    * Loudness is often said to be subjective, and dependent on pitch. [ISO 226:2003](https://en.wikipedia.org/wiki/Equal-loudness_contour) shows red "equal loudness" bands: sounds at different points on these lines sound as if they're equally loud, even though some are physically much more powerful:
    
        ![ISO 226:2003](https://upload.wikimedia.org/wikipedia/commons/thumb/4/47/Lindos1.svg/400px-Lindos1.svg.png)

#### Temporal Concepts

* **Rhytm** generally means a "movement marked by the regulated succession of strong and weak elements, or of opposite or different conditions" ([Wikipedia](https://en.wikipedia.org/wiki/Rhythm)).
* **Tempo** is "the speed or pace of a given piece or subsection thereof, how fast or slow" ([Wikipedia](https://en.wikipedia.org/wiki/Tempo)).
* **Beat** is "the basic unit of time, [or] the pulse (regularly repeating event)" ([Wikipedia](https://en.wikipedia.org/wiki/Beat_(music))).

#### Higher-Level Concepts

* A **melody** is "a linear succession of musical tones that the listener perceives as a single entity" ([Wikipedia](https://en.wikipedia.org/wiki/Melody)).
* **Harmony** "considers the process by which the composition of individual sounds, or superpositions of sounds, is analyzed by hearing. Usually, this means simultaneously occurring frequencies, pitches (tones, notes), or chords" ([Wikipedia](https://en.wikipedia.org/wiki/Harmony)).
* **Structure** "can be found at the level of part of a work, the entire work, or a group of works. Elements of music such as pitch, duration and timbre combine into small elements like motifs and phrases, and these in turn combine in larger structures" ([Wikipedia](https://en.wikipedia.org/wiki/Structure#Musical)).

### Mid-Level Feature Representations

* A set of **Mel-Frequency Cepstral Coefficients**, or **MFCCs**, is a *descriptor* of a short piece of audio.
    * "In sound processing, the mel-frequency cepstrum (MFC) is a representation of the short-term power spectrum of a sound, based on a linear cosine transform of a log power spectrum on a nonlinear mel scale of frequency" ([Wikipedia](https://en.wikipedia.org/wiki/Mel-frequency_cepstrum)).
* A **chroma** refers to the "color" of a sound, and maps it to one of the twelve different pitch classes.
    * Unlike MFCCs, chromas are timbre-independent.

### Structure Analysis

An **onset** refers to the "attack" of a sound. Tracking these over time produces **inter-onset intervals** (**IOIs**), which can be used to perform **autocorrelation** on a piece of audio to measure its self-similarity.

* Autocorrolation is similar to crosscorrelation, except that the vector is correlated with *itself*.

## Case Studies

Many tasks in music information retrieval involve finding music that is, to some degree, similar to the input piece. Note that all of the following are clearly information *retrieval* tasks, since they take a **query** as input against the (relatively) **static collection** of all music in the world, and produce a **(ranked) list** of matching pieces of music.

| **Retrieval Target** | **Shared Aspect** | **Matching Specificity** | **Case Study** |
|---|---|---|---|
| (Compressed/ enhanced) digital copies | Performance instance | Exact | [Fingerprinting](#fingerprinting) |
| *Semantic gap* | *Semantic gap* | *Semantic gap* | *Semantic gap* |
| Cover songs | Underlying musical work | Approximate | [Cover Song Retrieval](#cover-song-retrieval) |
| Similar songs | Performer/ composer | Global characteristics | |
| Similar songs | Genre | Global characteristics | [Genre Classification](#genre-classification) |

The *semantic gap* indicates that, at this point, the retrieval task becomes more subjective, and therefore also more difficult.

### Fingerprinting

Audio fingerprinting involves finding **exact matches of songs** based on short samples (commercially: think Shazam and SoundHound) in a way that is **robust to noise** and **fast**.

The basic concept of fingerprinting is to create a database of small, easily searchable representations of data points (in this application, songs). When a new song fragment comes in, the system takes its fingerprint and compares it to the rest of the database to see if there's a match.

At the core of this is finding a robust fingerprinting technique. One such technique is the [Philips fingerprinting algorithm (.pdf)](http://www.ismir2002.ismir.net/proceedings/02-FP04-2.pdf).

### Cover Song Retrieval

Cover songs may differ from their originals in tempo and tembre. There are several techniques to counter this, such as looking at minimum edit distances using dynamic programming.

### Genre Classification

Genre classification uses a bag-of-frames approach similar to the bag-of-words approach in image processing.

## Music & Multimedia

Music can also be a multimedia experience. Sadly, the (very cool) examples shown in the lecture do not translate well to a markdown file.
