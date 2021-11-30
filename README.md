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

### Zero-Shot Classification

We trained a language model for SA on English and tested it on our GS by relying on two state-of-the-art multilingual models. More specifically, we fine-tuned Multilingual BERT (mBERT) and XLM-RoBERTa with the GoEmotions corpus using the Hugging Face’s PyTorch implementation. We compared the results obtained on Latin with the ones achieved in a mono-lingual setting or in other cross-lingual experiments.

### Results

Accuracy of the mono-lingual and cross-lingual (zero-shot) classification method.
| Language | Test Set         | Genre             | mBERT | XLM-RoBERTa |
|----------|------------------|-------------------|-------|-------------|
| English  | GoEmotions       | social media      | 86%  | 73%        |
|          | AIT-2018         | social media      | 64%  | 59%        |
|          | Poem Sentiment   | literary - poetry | 50%  | 70%        |
| Italian  | MultiEmotions-It | social media      | 70%  | 75%        |
|          | AriEmozione      | literary - opera  | 50%  | 52%        |
| Latin    | Horace GS        | literary - poetry | 32%  | 30%        |


F1 of the experiments
|          | Lexicon-Based SA | Zero-shot mBERT | XML-RoBERTa |
|----------|------------------|-----------------|-------------|
|          | F1               | F1              | F1          |
| positive | 0.62             | 0.38            | 0.18        |
| negative | 0.50             | 0.60            | 0.59        |
| neutral  | 0.36             | 0.18            | 0.20        |
| mixed    | 0.00             | 0.00            | 0.00        |

## Citation

If you use the resources available in this repository, please cite the following paper:
- Rachele Sprugnoli, Francesco Mambrini, Marco Passarotti, Giovanni Moretti. *Sentiment Analysis of Latin Poetry: First Experiments on the Odes of Horace.* In Proceedings of the Eighth Italian Conference on Computational Linguistics (CLiC-it 2021).

## Copyright

<a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/4.0/"><img alt="Creative Commons Licence" style="border-width:0" src="https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png" /></a><br />This work is licensed under a <a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/4.0/">Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License</a>.
