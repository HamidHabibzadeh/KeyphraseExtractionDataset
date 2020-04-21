# Persian Keyphrase Extraction Datasets

This repository contains two proposed annotated datasets for automatic keyphrase extraction task. Every dataset contains a document (.txt) and its corresponding text body and text gold-standard keywords list 

Following are the datasets  proposed.

1. **PersianNewsDataset**: Contains 1174 full persian news body with atleast four gold-standard keyphrase that annotated by news authors.this dataset genereted from 20,000 news crawled from multiple subject 
2. **ThesisAbstractDataset**: Contains 450 thesis abstracts from Irandoc(Iranian Research Institute for Information Science and Technology) with humanities subject. We have only kept those documents that contain at least 4 gold-standard keyword.this dataset generate from 12000 thesis crawled 

## Dataset details and collection statistics

| Dataset | \|D\| | L<sub>avg</sub> | N<sub>avg</sub> | K<sub>avg</sub> | KP<sub>avg</sub>| S<sub>avg</sub>| ngram% | Description |
| :---         |     :---:      |     :---:      |     :---:      |     :---:      |     :---:     |     :---:     |     :---:     |         :--- |
| PersianNewsDataset   | 1147 |  350   | 7 | 4.2 | 93.6 | 24% | 14/50/24/12 | persian full news body dataset
| ThesisAbstractDataset     | 450 |  323 | 9 | 5 | 80.3 | 15% | 20/58/14/8 | Abstracts from thesis articles published in irandoc 

\|D\|: Number of documents.

L<sub>avg</sub>: Average document length, in words.

N<sub>avg</sub>: Average gold-standard keywords (unigrams) assigned per document.

K<sub>avg</sub>: Average gold-standard keyphrases (*n*-grams) assigned per document.

KP<sub>avg</sub>: Average percentage of keyphrases present in the text.

S<sub>avg</sub>: Average percentage of stopword in gold keyphrases.

ngram% :average percentage of 1/2/3/3+ -gram distribution.

## Dataset Evaluation
we conducted an empirical study on 5 models, the results of which are shown in  following  tables for each dataset , @5 meaning the results on the top five keyphrases and @10, top ten

All the models are implemented using [pke](https://github.com/boudinfl/pke) (an open source python-based keyphrase extraction toolkit)
by deafult pke dont support persian lingustics tools and we use [parsivar](https://github.com/ICTRC/Parsivar) (A Language Processing Toolkit for Persian) and [hazm](https://github.com/sobhe/hazm) (Python library for digesting Persian text) for Normalizing,Tokenizing,Stemming and POS Tag also we use [kharazi
persian-stopwords list](https://github.com/kharazi/persian-stopwords) in pke 

1.**PersianNewsDataset**

| Models | P@5| R@5 | F@5 | P@10 | R@10 | F@10 |
| :---         |     :---:      |     :---:      |     :---:      |     :---:      |     :---:      |          :---       |
|KpMiner	|**0.19**	|**0.21**|**0.20**|	0.13|	0.24|	017
|Yake|	0.16|	0.18|	0.17|	**0.13**|	**0.28**|	**0.18**
|TextRank	|0.15|	0.17|	0.16|	0.11|	0.23|	0.15
|TopicRank|	0.14|	0.16|	0.15|	0.10|	0.22|	0.14
|MultiPartitiRank|	0.14|	0.16|	0.15|	0.11|	0.22|	0.15


2.**ThesisAbstract**

| Models | P@5| R@5 | F@5 | P@10 | R@10 | F@10 |
| :---         |     :---:      |     :---:      |     :---:      |     :---:      |     :---:      |          :---       |
| Kpminer   |**0.21** |	**0.22** |	**0.21** |	**0.16** |	**0.25** |	**0.20**
| Yake      |0.15 |	0.16 |	0.15 |	0.14 |	0.24 |	0.18
|TextRank	|0.15 |	0.16 |	0.15 |	0.11 |	0.19 |	0.14
|TopicRank	|0.14 |	0.15 |	0.14 |	0.11 |	0.19 |	0.14
|MultiPartitiRank |	0.16 |	0.17 |	0.17 |	0.14 |	0.22 |	0.17

### pke models parameters :
**Kpminer:**

Candidate Selection: candidate_selection(lasf=3, cutoff=250, stoplist=stoplist)

candidate Weighting: candidate_weighting( alpha=2.3, sigma=3.0)

**Yake:**

  Candidate Selection: candidate_selection(n=3, stoplist=stoplist)
  
  candidate Weighting: candidate_weighting(threshold = 0.8 ,stoplist=stoplist, window=2, use_stems=False)
  
**TextRank:**

Candidate Selection: grammar_selection(grammar="NP: {<N.*>+<AJ.*>*}")

candidate Weighting: candidate_weighting(threshold=0.74, method='average')

**TopicRank:**

Candidate Selection: grammar_selection(grammar="NP: {<N.*>+<AJ.*>*}")

candidate Weighting: candidate_weighting(threshold=0.74, method='average')

**MultiPartitiRank:**

Candidate Selection: grammar_selection(grammar="NP: {<N.*>+<AJ.*>*}")

candidate Weighting: candidate_weighting(alpha=1.1, threshold=0.25, method='average')


**tanks F.sheikhsofla for help me**

