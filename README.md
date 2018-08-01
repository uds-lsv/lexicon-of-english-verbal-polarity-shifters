# Introducing a Lexicon of Verbal Polarity Shifters for English
This repository contains the data presented in:

[Schulder, Marc](http://marc.schulder.info) and [Wiegand, Michael](http://www.coli.uni-saarland.de/~miwieg/) and [Ruppenhofer, Josef](http://ruppenhofer.de/) and [Köser, Stephanie](http://www.skoeser.de/) (2018). **"Introducing a Lexicon of Verbal Polarity Shifters for English"**. Proceedings of the 11th Conference on Language Resources and Evaluation (LREC). Miyazaki, Japan, May 7-12, 2018.

[PDF](http://www.lrec-conf.org/proceedings/lrec2018/pdf/110.pdf)

## Content
We provide a complete lexicon of English verbal polarity shifters and their shifting scope.
Our lexicon covers all verbs of WordNet v3.1 (Miller et al., 1990) that are single word or particle verbs.
Polarity shifter and scope labels are given for each lemma-synset pair (i.e. each word sense of a lemma).

The data is presented in the following forms:
1. A complete lexicon of all verbal shifters and their shifting scopes.
2. Two auxiliary lists:
    1. A list of all lemmas with shifter labels
    2. A list of all word senses with shifter labels

All files are in CSV (comma-separated value) format.


## 1. Main Lexicon
File name: `shifter_lexicon.csv`

The main lexicon lists all verbal shifters and their shifting scopes.
Verbal shifters are modelled as lemma-sense pairs with one or more shifting scopes.

Each line of the lexicon file contains a single lemma-sense-scope triple, using the format:

    LEMMA,SYNSET,SCOPE

The elements are defined as follows:

- **LEMMA:** The lemma form of the verb.
- **SYNSET:** The numeric identifier of the synset, commonly referred to as _offset_ or _database location_.
              It consists of 8 digits, including leading zeroes (e.g. 00334568).
- **SCOPE:** The scope of the shifting:
  - `subj`: The verbal shifter affects its subject.
  - `dobj`: The verbal shifter affects its direct object.
  - `pobj_*`: The verbal shifter affects objects within a prepositional phrase.
              The preposition in question is included in the annotation.
              For example a _from_-preposition scope receives the label `pobj_from` and a a _for_-preposition receives `pobj_for`.
  - `comp`: The verbal shifter affects a clausal complement, such as infinitive clauses or gerunds.

The lexicon lists all lemma-sense pairs that are verbal shifters.
Any lemma-sense pair not listed is not a verbal shifter.
When a lemma-sense pair has more than one possible scope, a separate entry is made for each scope.


## 2. Auxiliary Lists
The auxiliary files represent the same shifter information as the main lexicon, but for lemmas and synsets, respectively, instead of for lemma-sense pairs.
Due to their nature, these lists are more coarse-grained than the main lexicon and contain no information on shifter scope.
They are provided as a convenience for fast experimentation.

### 2.1. List of Lemmas
File name: `shifter_lemma_lexicon.csv`

List of all verb lemmas and whether they are shifters in at least one of their word senses.

    LEMMA,LABEL

- **LEMMA:** The lemma form of the verb.
- **LABEL:** `shifter` if the verb is a shifter in at least one of its word senses, otherwise `nonshifter`.

Many verbal shifter lemmas only cause shifting in some of their word senses.
This list is therefore considerably more coarse-grained than the main lexicon.


### 2.2. List of Synsets
File name: `shifter_synset_lexicon.csv`

List of all synsets and whether their lemmas are shifters in this specific word sense. 

    SYNSET,LABEL

- **SYNSET:** The numeric identifier of the synset, commonly referred to as _offset_ or _database location_.
              It consists of 8 digits, including leading zeroes (e.g. 00334568).
- **LABEL:** `shifter` if the word sense causes shifting, otherwise `nonshifter`.

Shifting is shared among lemmas of the same word sense.
This list, therefore, provides (almost) the same granularity for the shifter label as the main lexicon.
However, in a few exceptions, synsets contained words with subtly different senses that did not all cause shifting.
These senses are considered shifters in this list, analogous to the generalisation in the list of lemmas.

## Attribution
This data set is published under [Creative Commons Attribution 4.0](https://github.com/uds-lsv/lexicon-of-english-verbal-polarity-shifters/blob/master/LICENSE).

If you use it in your research or work, please cite the publication (see above).

### BibTex
```
@InProceedings{schulder2018verbalshifter,
  author = {Schulder, Marc and Wiegand, Michael and Ruppenhofer, Josef and K\"oser, Stephanie},
  title = {Introducing a Lexicon of Verbal Polarity Shifters for English},
  booktitle = {Proceedings of the Eleventh International Conference on Language Resources and Evaluation (LREC 2018)},
  volume={1},
  pages={1393--1397},
  year = {2018},
  month = {May},
  date = {7-12},
  location = {Miyazaki, Japan},
  editor = {Nicoletta Calzolari (Conference chair) and Khalid Choukri and Christopher Cieri and Thierry Declerck and Sara Goggi and Koiti Hasida and Hitoshi Isahara and Bente Maegaard and Joseph Mariani and Hélène Mazo and Asuncion Moreno and Jan Odijk and Stelios Piperidis and Takenobu Tokunaga},
  publisher = {European Language Resources Association (ELRA)},
  address = {Paris, France},
  isbn = {979-10-95546-00-9},
  language = {English}
}
```

## Acknowledgements
This work was partially supported by the German Research Foundation (DFG) under grants RU 1873/2-1 and WI4204/2-1.

## References
G. Miller, R. Beckwith, C. Fellbaum, D. Gross, K. Miller: "Introduction to WordNet: An On-Line Lexical Database". International Journal of Lexicography, 3:235-244, 1990.
