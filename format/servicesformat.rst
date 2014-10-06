The EUROSENTIMENT format for services and corpora
=================================================
The Eurosentiment format is an extension of the NIF_ format data model for use in Sentiment Analysis.
However, NIF_ and the Eurosentiment differ in one respect: Eurosentiment sets JSON-LD_ as its primary serialisation format, whereas NIF defaults to XML+RDF or turtle.
It includes properties from Marl_, Onyx_ and other ontologies that complement those in NIF_ for sentiment and emotion tagging.
However, NIF_ and the Eurosentiment differ in one respect: Eurosentiment sets JSON-LD_ as its primary serialisation format, whereas NIF defaults to XML+RDF or turtle.

JSON-LD is a subset of JSON that makes it possible to embed semantic information in plain JSON objects.
It retains full compatibility with JSON while adding useful information.

By using this serialisation format, Eurosentiment targets both semantic web developers and traditional developers alike.

.. _NIF: http://persistence.uni-leipzig.org/nlp2rdf/
.. _Marl: http://www.gsi.dit.upm.es/ontologies/marl
.. _Onyx: http://www.gsi.dit.upm.es/ontologies/onyx
.. _JSON-LD: http://www.json-ld.org

Overview
--------
.. :emphasize-lines: 35, 38
.. code-block:: javascript

    {
      "@context": [
        "http://demos.gsi.dit.upm.es/eurosentiment/static/context.jsonld",
    ],
    "@id": {{ processID }},
    "analysis": [
      {
        "@id": {{ analysisID }},
        "@type": [
          {{ analysisType }}
        ],
        "prov:wasAssociatedWith": {{ agent }},
        "dc:language": {{ language}},
        "marl:maxPolarityValue": {{ minValue }},
        "marl:minPolarityValue": {{ maxValue }}
      }
      [...]
    ],
    "domain": {{ domain }},
    "entries": [
      {
        "@id": {{ entry_id }},
        "dc:subject": {{ topic }},
        "emotions": [
          {
            "prov:generatedBy": {{ analysisID }},
            "onyx:hasEmotion": [
              {
                "onyx:hasEmotionCategory": {{ emotions[i].category }},
                "onyx:intensity": {{ emotions[i].emotion_intensity }}
              },
              [...]
            ]

          }
          [...]
        ],
        "opinions": [
          {
            "prov:generatedBy": {{ analysisID }},
            "marl:polarityValue": {{ opinions[i].polarityValue }},
            "marl:hasPolarity": {{ opinions[i].polarity }},
            "marl:describesObject": {{ opinions[i].described_object }},
          },
          [...]
        ],
        "nif:isString": {{ string_representation }},
        "strings": [
          {
            "nif:anchorOf": {{ strings[i].value }},
            "itsrdf:taIdentRef": {{ strings[i].entity }},
            "nif:posTag": {{ strings[i].posTag }},
            "nif:lemma": {{ strings[i].lemma }}
          },
          [...]
        ]
      },
      [...]
    ]
    }

processID
    Is the ID of the process that gathered the results.
domain  
    Domain detected in the entries, or used by the analysis
analysis
    A set of results can be produced by combining the results from several analysis processes. Each of them needs to be described here.

    :analysisID: Each of the analysis needs an unique URI so that the generated opinions/emotions can be linked to it. A set of results may aggregate the results from independent analysis (e.g. a sentiment analysis and an emotion analysis)
    :analysisType: Example: *marl:SentimentAnalysis* or *onyx:EmotionAnalysis*
    :algorithm: [In marl] Algorithm that was used to generate the results
    :agent: Responsible for or creator of the analysis

language    
    Language that the analysis uses. e.g. *"es"*
minValue    
    [In marl opinions] Minimum value of the opinion value
maxValue    
    [In marl opinions] Maximum value of the opinion value
domain  
    Domain where the analysis was run. e.g. *wnd:electronics*
entry_id    
    Each entry must have a unique URI
topic   
    The subject or subjects of the entry. e.g. *wnd:electronics*
emotions    
    The emotions found in the context. Depending on the theory of emotions used, emotions can be categorised and/or be defined by different dimensions. This example represents the usual case which is a model using categories.

           category 
            Category of the emotion. e.g. *wna:Hatred*
           emotion_intensity    
            Intensity of the emotion as defined by the algorithm

opinions    
    The opinions found in the context.

           polarity 
            Polarity of the opinion. e.g. *marl:Positive*
           polarityValue    
            Numerical value of the polarity, as a floating point
           described_object 
            Object that the opinion is about

string_representation   
    Plain text representation
strings  
    A NIF context can be subdivided in substrings, which have their own properties. This is usually done to associate a particular string with an entity in Named Entity Recognition

             strings[i].value
                Text representation
             strings[i].entity   
                Entity the string represents
             strings[i].posTag   
                Part-of-speech tag
             strings[i].lemma    
                Lemma of the word

Context
-------
The JSON-LD context contains semantic information about the properties in the JSON document, including convenient prefixes or namespaces.
The Eurosentiment context would look like this:

.. code:: json

    {
      "@context": {
          "dc": "http://purl.org/dc/terms/",
          "dc:subject": {
            "@type": "@id"
          },
          "emotions": {
            "@container": "@list",
            "@id": "onyx:hasEmotionSet",
            "@type": "onyx:EmotionSet"
          },
          "marl": "http://www.gsi.dit.upm.es/ontologies/marl#",
          "nif": "http://persistence.uni-leipzig.org/nlp2rdf/ontologies/nif-core#",
          "onyx": "http://www.gsi.dit.upm.es/ontologies/onyx#",
          "opinions": {
            "@container": "@list",
            "@id": "marl:hasOpinion",
            "@type": "marl:Opinion"
          },
          "prov": "http://www.w3.org/ns/prov#",
          "rdfs": "http://www.w3.org/2000/01/rdf-schema#",
          "analysis": {
            "@id": "prov:wasInformedBy"
          },
          "entries": {
            "@id": "prov:generated"
          },
          "strings": {
            "@reverse": "nif:hasContext",
            "@type": "nif:String"
          },
          "wnaffect": "http://www.gsi.dit.upm.es/ontologies/wnaffect#",
          "xsd": "http://www.w3.org/2001/XMLSchema#"
      }
    }


Examples
--------

* Annotating one entry using a fictitious service (http://example.com/analyse) provided by http://example.com. Input: "My ipad is an awesome device".
.. code-block:: javascript

   {
    "@context": [
      "http://demos.gsi.dit.upm.es/eurosentiment/static/context.jsonld"
    ],
    "results": {
      "analysis": [
        {
          "@id": "http://example.com/analyse",
          "@type": [
            "marl:SentimentAnalysis"
          ],
          "dc:language": "en",
          "marl:maxPolarityValue": 10.0,
          "marl:minPolarityValue": 0.0
          "prov:wasAssociatedWith": "http://example.com"
        }
      ],
      "entries": [
        {
          "@id": "http://example.com/analyse?input=My%20ipad%20is%20an%20awesome%20device",
          "opinions": [
            {
              "marl:polarityValue": 9,
              "marl:hasPolarity": "marl:Positive",
              "marl:describesObject": "http://dbpedia.org/page/IPad"
              "prov:generatedBy": "http://example.com/analyse",
            }
          ],
          "nif:isString": "My ipad is an awesome device",
          "strings": [
            {
              "@id": "http://example.com/analyse?input=My%20ipad%20is%20an%20awesome%20device#char=3,6",
              "nif:anchorOf": "ipad",
              "itsrdf:taIdentRef": "http://dbpedia.org/page/IPad"
            }
          ]
        }
      ]
    }
   }


* Annotating complex emotions in Spanish. Input: "Mi ipad me tiene harto".
.. code-block:: javascript

   {
    "@context": [
      "http://demos.gsi.dit.upm.es/eurosentiment/static/context.jsonld"
    ],
    "results": {
      "analysis": [
        {
          "@id": "http://example.com/analyse",
          "@type": [
            "onyx:EmotionAnalysis"
          ],
          "dc:language": "es",
          "onyx:maxEmotionIntensity": 1.0,
          "onyx:minEmotionIntensity": 0.0
          "prov:wasAssociatedWith": "http://example.com/"
        }
      ],
      "entries": [
        {
          "@id": "http://example.com/analyse?input=Mi%20ipad%20me%20tiene%20harto",
          "dc:language": "es",
          "opinions": [
          ],
          "emotions": [
            {
              "onyx:aboutObject": "http://dbpedia.org/page/IPad"
              "prov:generatedBy": "http://example.com/analyse",
              "onyx:hasEmotion": [
                {
                    "onyx:hasEmotionCategory": "wna:dislike",
                    "onyx:hasEmotionIntensity": 0.7
                },
                {
                    "onyx:hasEmotionCategory": "wna:despair",
                    "onyx:hasEmotionIntensity": 0.1
                }
              ]
            }
          ],
          "nif:isString": "My ipad is an awesome device",
          "prov:generatedBy": "http://example.com/analyse",
          "strings": [
            {
              "@id": "http://example.com/analyse?input=Mi%20ipad%20me%20tiene%20harto#char=3,6",
              "nif:anchorOf": "ipad",
              "itsrdf:taIdentRef": "http://dbpedia.org/page/IPad"
            }
          ]
        }
      ]
    }
   }

Other serialisation formats
---------------------------
The Eurosentiment format is semantic, as is the NIF Format 
Althought the preferred and mainly used serialisation format is JSON-LD, there are other serialisation formats that could be used as well.

For instance, it is particularly interesting to convert corpora to N-Triples for storage in a semantic server such as Virtuoso.

Useful links
------------
:NIF: http://persistence.uni-leipzig.org/nlp2rdf/
:JSON-LD: http://json-ld.org
