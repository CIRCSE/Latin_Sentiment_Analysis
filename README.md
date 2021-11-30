# Latin Sentiment Analysis

## Introduction

This repository includes data and scripts the first experiments with Sentiment
Analysis of Latin literary texts.

So far, we ran 4 types of experiments on the 4 books of Horace's _Odes_. The text
and lemmatization of Horace are that of the [Opera Latina]()
of the LASLA laboratory.


## Experiments

### Lexicon-based Sentiment Analysis

This dataset is obtained by performing a simple dictionary lookup of LASLA lemmas on the
[LatinAffectus]() sentiment lexicon. Ambiguous terms (e.g. *ales*, *senectus*...)
were averaged (so e.g., *ales* = 0.25), and then manually revised. In particular,
the disambiguation was carried out using the POS annotation, so that e.g. adjectives
in LASLA received the sentiment value of the adjective entry in LatinAffectus.

In the process of lemma lookup in the dictionary, a series of erroneous identifications were produced. I reviewed manually the cases of tokens with: 1. polarity score != 0.0, 2. POS != A (noun) or C (adj).
We decided to:

- change all B (verb) to 0.0 (verbs involved: *labor, suspicio (suspecta), formido (formidatus), nitor*
- change all M (adverb) to 0.0 (they were all cases of adverbial *sat/satis*)
- change all S (conj) to 0.0 (just 1 case of adverbial *verum*)
- keep all D (numeral): *simplex, primus, prius, primum*
- keep all L (indef pron): *solus*

### Unsupervised Approaches

### Bilingual Sentiment Embeddings

### Zero-Shot Classification

## Copyright

<a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/3.0/"><img alt="Creative Commons Licence" style="border-width:0" src="https://i.creativecommons.org/l/by-nc-sa/3.0/88x31.png" /></a><br />The resources available in this repository is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/3.0/">Creative Commons Attribution-NonCommercial-ShareAlike 3.0 International License</a>.
