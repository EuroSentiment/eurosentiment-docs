The Eurosentiment Format for Lexica
====================================

The EUROSENTIMENT sentiment lexicons are represented in RDF using the lemon_ format extended with some properties from the Marl_ vocabulary for representing the sentiment information such as polarity and polarity value. Deliverable D4.3_ (p54-56) describes in details the model.

.. _lemon: http://lemon-model.net/
.. _Marl: http://www.gsi.dit.upm.es/ontologies/marl
.. _D4.3: http://eurosentiment.eu/wp-content/uploads/2014/02/EUROSENTIMENT-D4_3-Adaptation-of-legacy-language-resources-Final-version-v16_Final.pdf

The following figure shows an example of RDF domain-specific lexicon. 

.. image:: /_static/img/lexicon-example.jpg
 
In this figure we see snippets from two lexicons: a lexicon for the hotel domain in english (i.e. *le:hotel* ) and a lexicon for the hotel domain in german (i.e. *ld:hotel*).
The sentiment lexicons are composed of lexical entries: in our example *lee:location* and *lee:pretty-good* for the English lexicon and *led:Lage* for the german lexicon. Some of the lexical entries are domain aspects like *location* and *Lage* and some are sentiment words like *pretty good*.

Each lexical entry is defined by a lemon canonicalForm, several lemon otherForm properties representing the morphological variations, several senses and part of speech information. The connection of the EUROSENITMENT lexicons to other linguistic linked data datasets (i.e. DBpedia and Wordnet) happen at the sense level.
For instance in our case, the sens of the *lee:location* lexical entry is linked to the http://dbpedia.org/page/Location entity and to the Wordnet synset: http://wordnet-rdf.princeton.edu/wn31/100027365-n.

In the case of sentiment lexical entries we use two more properties (i.e. *marl:PolarityValue* and *marl:hasPolarity*) to represent the sentiment inforation. In our example, *lee:pretty-good* has a positive polarity of 0.75 where the most positive value is 1 and the most negative value is -1. 

The domain-specific aspect of the EUROSENTIMENT lexicons is given by the lemon property context which connectsa sentiment word to a domain aspect. In the example, the *lmn:context* property signifies that the sentiment word *pretty good* has a positive value of 0.75 in the context of the *location* domain aspect.

We recall from D4.3_ that we generate domain-specific lexicons in other languages based on the initial english lexicon. For example, in our case, the german lexicon for hotel was automatically generated form the english lexicon for hotel. This relation between the two lexicons is represneted via the *isocat:translationOf* relation between the senses of the translated lexical entries. 






