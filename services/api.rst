NIF API
=======
.. http:get:: /services/server/access/(service_id)

   Access the service at `service_url`. The `service_id` can be retrieved from the service page in the Portal
   Since the requests to the server are likely to be long, :http:post:`/services/server/access/(service_id)` is recommended.

   **Example request**:

   .. sourcecode:: http

      GET /service/access/SentimentAnalysisExample?input=I%20love%20EUROSENTIMENT HTTP/1.1
      Host: eurosentiment.eu
      Accept: application/json, text/javascript


   **Example response**:

   .. sourcecode:: http

      HTTP/1.1 200 OK
      Vary: Accept
      Content-Type: text/javascript

      {
        "@context": [
          "http://eurosentiment.eu/context.jsonld",
          {
            "@base": "http://eurosentiment.eu/service/access/SentimentAnalysisExample#"
          }
      ],
      "analysis": [
        {
          "@id": "SentimentAnalysisExample",
          "@type": "marl:SentimentAnalysis",
          "dc:language": "en", 
          "marl:maxPolarityValue": 10.0,
          "marl:minPolarityValue": 0.0
        }
      ],
      "domain": "wndomains:electronics", 
      "entries": [
        {
          "opinions": [
            {
              "prov:generatedBy": "SentimentAnalysisExample",
              "marl:polarityValue": 7.8, 
              "marl:hasPolarity": "marl:Positive",
              "marl:describesObject": "http://eurosentiment.eu",
            }
          ],
          "nif:isString": "I love EUROSENTIMENT",
          "strings": [
            {
              "nif:anchorOf": "EUROSENTIMENT",
              "nif:taIdentRef": "http://eurosentiment.eu"
            }
          ]
        }
       ]
      }

   :query i input: No default. Depends on informat and intype
   :query f informat: one of `turtle` (default), `text`, `json-ld`
   :query t intype: one of `direct` (default), `url`
   :query o outformat: one of `turtle` (default), `text`, `json-ld`
   :query p prefix: prefix for the URIs

   :reqheader Accept: the response content type depends on
                      :mailheader:`Accept` header
   :reqheader X-eurosentiment-token: optional OAuth token to authenticate
   :resheader Content-Type: this depends on :mailheader:`Accept`
                            header of request
   :statuscode 200: no error
   :statuscode 404: service not found

.. http:post:: /services/server/access/(service_id)

   The same as the previous method. This is the recommended method.


   :form i/input: No default. Depends on informat and intype
   :form f/informat: one of `turtle` (default), `text`, `json-ld`
   :form t/intype: one of `direct` (default), `url`
   :form o/outformat: one of `turtle` (default), `text`, `json-ld`
   :form p/prefix: prefix for the URIs

   :reqheader Accept: the response content type depends on
                      :mailheader:`Accept` header
   :reqheader X-eurosentiment-token: optional OAuth token to authenticate
   :resheader Content-Type: this depends on :mailheader:`Accept`
                            header of request
   :statuscode 200: no error
   :statuscode 404: service not found

