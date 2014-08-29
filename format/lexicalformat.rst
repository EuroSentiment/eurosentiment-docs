The Eurosentiment Format for Lexicoa
====================================

The EUROSENTIMENT sentiment lexicons are represented in RDF using the lemon_ format extended with some properties from the Marl_ vocabulary for representing the sentiment information. Deliverable D4.3_ (p54-56) describes in details the model.


.. _lemon: http://lemon-model.net/
.. _Marl: http://www.gsi.dit.upm.es/ontologies/marl
.. _D4.3: http://eurosentiment.eu/wp-content/uploads/2014/02/EUROSENTIMENT-D4_3-Adaptation-of-legacy-language-resources-Final-version-v16_Final.pdf

The following figure shows an example of RDF domain-specific lexicon. 
In this figure we see snippets from two lexicons: a lexicon for the hotel domain in english (i.e. le:hotel) and a lexicon for the hotel domain in german (ld:hotel).
The sentiment lexicons are composed of lexical entries: in our example lee:location and lee:pretty-good for the English lexicon and led:Lage for the german lexicon. Some of the lexical entries are domain aspects like "location" and "Lage" and some are sentiment words like "pretty good".



