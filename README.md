# Diversifying the Legal Order

This page is a companion for the paper on [Evaluation of Diversification Techniques for Legal Information Retrieval](http://dx.doi.org/10.20944/preprints201611.0116.v1), written by Koniaris Marios (me), Ioannis Anagnostopoulos and Yannis Vassiliou. 

This page hosts the complete dataset, ground-truth data, queries and relevance assessments we utilize in the article. Our goal is to encourage progress on the diversification in legal IR.

## Dataset

Our corpus contains 3.890 Australian legal cases from the [Federal Court of Australia](http://www.fedcourt.gov.au). The cases were originally downloaded from [AustLII](http://www.austlii.edu.au) and were used in 
> F. Galgani, P. Compton, and A. Hoffmann. Combining different summarization techniques for legal text. In Proceedings of the Workshop on Innovative Hybrid Approaches to the Processing of Textual Data, pages 115-123, Avignon, France, April 2012. Association for Computational Linguistics

to experiment with automatic summarization and citation analysis. The legal corpus contains all cases from the Federal Court of Australia spanning from 2006 up to 2009. From the cases, we extracted all needed text for our diversification framework.

Our dataset can de found [here](https://archive.ics.uci.edu/ml/datasets/Legal+Case+Reports)

## West Law Digest Topics

West Law Digest Topics is a taxonomy of identifying points of law from reported cases and organizing them by topic and key number. It is used to organize the entire body of American law.

1. [WikiPedia entry](https://en.wikipedia.org/wiki/West_American_Digest_System)
2. [PDF list](https://info.legalsolutions.thomsonreuters.com/documentation/westlaw/wlawdoc/wlres/keynmb06.pdf) 

 > we downloaded this list from WestLaw, process it and acquired a textual representation of it.

3. [Original Topics/ queries](https://github.com/mkoniari/LegalDivEval/blob/master/westlaw.txt)

 > Each topic was issued as candidate query to our retrieval system. Outlier queries, whether too specific/rare or too general, where removed using the interquartile range, below or above values Q1 and Q3, sequentially in terms of number of hits in the result set and score distribution for the hits, demanding in parallel a minimum cover of min|N| results.

4. [Used Topics/ queries](https://github.com/mkoniari/LegalDivEval/blob/master/QUERIES.txt) 
 > Our final list of user queries. In total, we kept 289 queries

## Query assessments and ground-truth.

For each topic/query we kept the top-n results. An LDA topic model, using an open source implementation ([mallet](http://mallet.cs.umass.edu/)) was trained on the top-n results for each query. From the resulting topic distributions for each document, with an acceptance threshold of 20%, we consider relevance judgments for each query/ document and subtopic. In other words, we consider the topics created from LDA as aspects of each query, and based
on the topic/ document distribution we can infer whether a document is relevant for an aspect. Our ground-truth data can be found:
* [Qrel format](https://github.com/mkoniari/LegalDivEval/blob/master/qrels.txt)
* [Compact format](https://github.com/mkoniari/LegalDivEval/blob/master/aspects.txt)

### Stop Words
Our stop word list can be found [here](https://github.com/mkoniari/LegalDivEval/blob/master/stopwords.en)

## Citing 

If you use queries and relevance assessments utilized in this work in your research, please cite:

Koniaris, M.; Anagnostopoulos, I.; Vassiliou, Y. Evaluation of Diversification Techniques for Legal Information Retrieval. Preprints 2016, 2016110116 (doi: 10.20944/preprints201611.0116.v1).