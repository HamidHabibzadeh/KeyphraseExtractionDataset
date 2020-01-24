# Persian-Keyphrase-Extraction-Datasets

This repository contains two proposed annotated datasets for automatic keyphrase extraction task. Every dataset contains a document (.txt) and its corresponding text body and text gold-standard keywords list 

Following are the datasets  proposed.

1. **PersianNewsDataset**: Contains 1174 full persian news body with atleast four gold-standard keyphrase that annotated by news authors.this dataset genereted from 20,000 news crawled from multiple subject 
2. **ThesisAbstractDataset**: Contains 450 thesis abstracts from Irandoc(Iranian Research Institute for Information Science and Technology) with humanities subject. We have only kept those documents that contain at least 4 gold-standard keyword.this dataset generate from 12000 thesis crawled 

## Dataset details and collection statistics

| Dataset | \|D\| | L<sub>avg</sub> | N<sub>avg</sub> | K<sub>avg</sub> | KP<sub>avg</sub>| Description |
| :---         |     :---:      |     :---:      |     :---:      |     :---:      |     :---:      |          :--- |
| PersianNewsDataset   | 1147 |  350   | 0.7 | 4.2 | 93.6 | persian full news body dataset
| ThesisAbstractDataset     | 450 |  323 | 1.3 | 5 | 80.3 | Abstracts from thesis articles published in irandoc 

\|D\|: Number of documents.
L<sub>avg</sub>: Average document length, in words.
N<sub>avg</sub>: Average gold-standard keywords (unigrams) assigned per document.
K<sub>avg</sub>: Average gold-standard keyphrases (*n*-grams) assigned per document.
KP<sub>avg</sub>: Average percentage of keyphrases present in the text

