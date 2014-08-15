Language Resource Types
=======================

This section describes the type of language resources that the EUROSENTIMENT LRP supports. Based on the initial list of language resources (see here_) from the project we identified the following supported formats. please not in brackets the number of the Lnagua resource addressed by the listed format.

.. _here: https://www.google.com/url?q=https%3A%2F%2Fdocs.google.com%2Fspreadsheet%2Fccc%3Fkey%3D0AjXPAtb06jnMdFNicWRlV3FrVG9GT1dOMG9QYk9Ea1E%26usp%3Ddrive_web%23gid%3D17

1. **domain-specific-lexicon-TSV** (5): Tab-separated-values file that describes sentiments in the context of domain aspects (e.g. myFile.tsv). 
The header of the TSV file should have the following columns:

``entityWNid    entityPOS    entity    sentiWNid    sentiPOS    sentiment    sentiScore``

where:

* *entityWNid*: WordNet30 synset ID of the domain aspect (e.g. 02671062).
* *entityPOS*: part of speech of the domain aspect (i.e. n, a, v, r).
* *entity*: domain aspect as string (e.g. “access”).
* *sentiWNid*: WordNet30 synset ID of the sentiment associated with the domain aspect (00979366).
* *sentiPOS*:  part of speech of the sentiment word (i.e. n, a, v, r).
* *sentiment*: sentiment word as string (e.g. “quick”) 
* *sentiScore*: the polarity value of the sentiment (a rational number between -1 and 1,  where -1 is very negative, 0 is neutral and 1 is very positive).

e.g.
 
``02671062    n    access    00979366    a    quick    0.5``

2. **entiment-lexicon-CSV** (45 (needs to be converted), 54): Comma-separated-values file that describes the sentiment words and their polarities from a domain.  (e.g. myFile.csv). 
The header of the CSV file should have the following columns:

``sentiment,sentimentPOS,sentimentScore,morphosyntacticVariations``

where: 

* *sentiment*: the sentiment word in the domain.
* *sentimentPOS*: the part-of-speech of the sentiment word.
* *sentimentScore*: the polarity value of the sentiment (a rational number between -1 and 1,  where -1 is very negative, 0 is neutral and 1 is very positive).
* *morphosyntacticVariations*:the sentiment morphosyntactic variations. 

e.g.

``Besserung|NN    0.40    Besserungen,Besserungnen``

3. **review-corpus-no-polarity** (36): A file containing one review per line.

e.g.

``The location was great and the staff friendly. I like it!``
``The room was a bit too small.``
``…``

4. **review-corpus-overall-polarity-TSV**(3, 31, 34): A tab-separated-values file with reviews and overall polarity. The header of the TSV file should have the following columns:

reviewText    overallPolarity

where
reviewText: A string that contains the review (no tabs in the string).
overallPolarity: The overall polarity of the given review text (rational number between -1 and 1,  where -1 is very negative, 0 is neutral and 1 is very positive).

e.g.
Rien à dire. Très bon produit de qualité.    1.0

5. **review-corpus-pos-lemma-wn-overall-polarity-TSV** (2, 4): A tab-separated-values file with columns of the following form:

reviewText    annotation    overallPolarity

where: 
reviewText: A string that contains the review (no tabs in the string).
annotation: A list with comma-separated values for each word in the text review containing: word, part-of-speech, lemma and a list of possible WordNet30 synsteIDs.
overallPolarity: The overall polarity of the given review text (rational number between -1 and 1,  where -1 is very negative, 0 is neutral and 1 is very positive).

e.g.
Excellent location.    [Excellent;;JJ;;excellent;;[], location;;NN;;location;;[n#01051331]]    0.8


6. **review-corpus-pos-lemma-wn-overall-polarity-Excel** (7,8,9,10,11,12,13,14,17,18,20,21,22,50,51,52,53): A .gz compressed folder containing Excel files with several reviews per file. Each review in the Excel file is spread over several lines. The header of the Excel file is: TEXT    LEMMA    WN_POS    WN_SYNSET    DOMAIN    SENTIMENT    EMOTION.

where:
TEXT: the full review text in the first line; subsequent lines have one word of the review per line.
LEMMA: nothing in the first line; in subsequent lines it describes the lemma value of an individual word from the review.
WN_POS: nothing in the first line; in subsequent lines it describes the part-of-speech value of an individual word from the review.
WN_SYNSET: nothing in the first line; in subsequent lines it describes the WordNet30 synset ID value of an individual word from the review.
DOMAIN: the domain of the review (only in the first line)
SENTIMENT: (only in the first line)
EMOTION: (only in the first line)

For each review in the file there are several lines in the Excel file.
the first line: 
where
the subsequent lines contain for each word in the text (first column) its LEMMA (column 2), its part-of-speech (column 3) and WordNet30 synsetID

text, list of words in text, list of base lemmas, list of POS, list of synset, domain, brand, kind, product, part, quality, sentiment, emotion


7. **dataset-rdf** (25, 26, 27, 29, 37(needs conversion to RDF),42,55): RDF dump (*.nt.gz) of linked data dataset like WordNet, DBpedia, BabelNet.
8. **aspects-review-corpus-TripAdvisor**(49): A file with annotated reviews and aspect ratings. Each review in the file is spread over several lines where each line starts with a dedicated tag as in the example below.

e.g.
<Author>IndieLady
<Content>Lovely hotel, unique decor, friendly front desk staff […] 
<Date>Nov 13, 2008
<No. Reader>-1
<No. Helpful>-1
<Overall>4
<Value>5
<Rooms>4
<Location>5
<Cleanliness>4
<Check in / front desk>5
<Service>5
<Business service>-1

9. **aspects-review-corpus-Amazon** (44): A file that consists of plain text reviews for products with custom ratings annotations that spread over several lines. The marker for a new review is [t] whereas the numbers in brackets stand for the rating of a certain aspect in the review. See below an example:

e.g.                    
[ t ] the best 4mp compact digital available camera[+2]## this camera is perfect for an enthusiastic amateur photographer . picture [+3] ,
                    
macro[+3]## the pictures are razor sharp , even in macro . . .        
     




