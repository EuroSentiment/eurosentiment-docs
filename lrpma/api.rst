The LRP Management Application API
=====================================================
It is possible to retrieve management information from the LRP such as listing a user's own services or the subscription details.

The basic endpoint is: http://217.26.90.243:8080/EuroSentimentServices/services/server

.. http:get:: /listAll

   Get a list of all the services in the platform.

   **Example request**:

   .. sourcecode:: http

      GET /listAll
      Host: portal.eurosentiment.eu
      Accept: application/json, text/javascript

   **Example response**:

   .. sourcecode:: http

      HTTP/1.1 200 OK
      Vary: Accept
      Content-Type: text/javascript

    [
        {
            "credentials": "",
            "lastModification": "2014-06-30 10:24:47.0",
            "request_limit": 10000,
            "serviceMethod": "POST",
            "serviceUrl": "http://54.187.254.3:8000/language_detector",
            "sid": "sptdl0407",
            "state": "enabled",
            "url": "http://217.26.90.243:8080/EuroSentimentServices/services/server/access/sptdl0407"
        }
    ]

   :statuscode 200: no error
   :statuscode 404: there's no user

.. todo:: Describe the LRPMA API in detail
