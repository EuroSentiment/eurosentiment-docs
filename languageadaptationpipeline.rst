The Language Resource Adaptation Pipeline (a.ka. LRAP) implements a methodology for legacy language resource adaptation that generates domain-specific sentiment lexicons organized around domain entities described with lexical information and sentiment words described in the context of these entities. 

The outcome of the Language Resource Adaptation Pipeline are annotated corpora represented the NIF/Marl format and domain-specific sentiment lexicons represented in RDF using the Lemon/Marl format. The legacy language resources are enriched with semantics and additional linguistic information from resources like DBpedia and BabelNet. 

There are four main steps of the LRAP as shown in Figure 1: (i) the Cor- pus Conversion step normalizes the different language re- sources to a common schema based on Marl and NIF4; (ii) the Semantic Analysis step extracts the domain-specific entity classes and named entities and identifies links be- tween these entities and concepts from the LLOD Cloud; (iii) the Sentiment Analysis step extracts contextual senti- ments and identifies SentiWordNet synsets corresponding to these contextual sentiment words; (iv) the Lexicon Gen- erator step uses the results of the previous steps, enhances them with multilingual and morphosyntactic information and converts the results into a lexicon based on the lemon and Marl formats. Different language resources are pro- cessed with variations of the given adaptation pipeline. 

.. image:: overall.jpg
   
