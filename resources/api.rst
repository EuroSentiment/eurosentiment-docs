Resources API
=============
.. http:post:: /sparql

   The posts tagged with `tag` that the user (`user_id`) wrote.

   **Example request**:

   .. sourcecode:: http


       POST /sparql HTTP/1.1
       Host: eurosentiment.eu
       Content-Length: 199
       x-eurosentiment-token: 23aee871-d18d-4afa-c2e3-283f8ae9232ca
       Accept-Encoding: gzip, deflate, compress
       Accept: */*
       content-type: application/json

       {"query": "PREFIX lemon: <http://lemon-model.net/lemon#>\nSELECT * FROM <http://www.eurosentiment.eu/dataset/hotel/es/gabvul/9/lexicon>\nWHERE {?s lemon:sense ?sense }", "format": "application/json"}

   **Example response**:

   .. sourcecode:: http

      HTTP/1.1 200 OK
      date: Mon, 07 Jul 2014 16:46:21 GMT
      content-length: 596
      content-type: application/json
      server: Jetty(8.1.10.v20130312)

      {
          "head": {
              "link": [],
              "vars": [
                  "s",
                  "sense"
              ]
          },
          "results": {
              "bindings": [
                  {
                      "s": {
                          "type": "uri",
                          "value": "http://www.eurosentiment.eu/dataset/hotel/es/gabvul/9/lexicalentry/H2O"
                      },
                      "sense": {
                          "type": "uri",
                          "value": "http://www.eurosentiment.eu/dataset/hotel/es/gabvul/9/lexicalentry/sense/H2O_0"
                      }
                  },
                  {
                      "s": {
                          "type": "uri",
                          "value": "http://www.eurosentiment.eu/dataset/hotel/es/gabvul/9/lexicalentry/a_gusto"
                      },
                      "sense": {
                          "type": "uri",
                          "value": "http://www.eurosentiment.eu/dataset/hotel/es/gabvul/9/lexicalentry/sense/a_gusto_0"
                      }
                  }
              ],
              "distinct": false,
              "ordered": true
          }
      }



   :data 
   :reqheader Accept: the response content type depends on
                      :mailheader:`Accept` header
   :reqheader Authorization: optional OAuth token to authenticate
   :resheader Content-Type: this depends on :mailheader:`Accept`
                            header of request
   :statuscode 200: no error
   :statuscode 404: there's no user

