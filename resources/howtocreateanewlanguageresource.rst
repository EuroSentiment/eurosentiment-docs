How to add a new language resource 
===================================

This section describes how a new languag resource is added to teh EUROSENTIMENT LRP.

Resource upload steps:
	0. Precondition: the user is logged in: https://portal.eurosentiment.eu/ with his username and password
	1. Click on the 'Recources' tab -> 'New resource'
	2. Fill in the 'Resource creation form'
		* Name -> give a name of your LR
		* Graph URI prefix -> the platform will suggest you a unique graph URI (if you like it, leave it like it is)
		* Short Name -> give a short name of your LR. It will be used to dynamically generate the graph URI
		* Language -> select form the language drop-down list
		* Application Domain -> select form the drop-down list
		* Description -> add a detailed description of your language resource.
		* Resource type -> chose from the drop-down list the resource type you want to add.
		* Access control -> select the type of license under which you want to publish the LR
		* Upload hte LR file
		* Fill in the Fact sheet with similar details and send an email to eurosentimentpt@gmail.com
	3. Click on the 'Create' button
	4. What will happen behind the scenes:
		* an email is sent to the EUROSENTIMENT LRP
		* you are notified by email that your LR was submitted and will be reviewed before added to the LRP as soon as possible
		* an administrator will carefully read the resource submission and will decide if the language resource will be added to the language resource pool
		* if the LR is provided in an existing format then move to 4.6
		* if the LR is provided in a new format not known previously to the platform, the administrator will develop a specific language resource adaptation pipeline
		* the administrator runs the language resource adaptation pipeline and the provided LR is processed, converted to RDF and linked-data and the result is uploaded to the SPARQL endpoint
		* you are notified by email that your language resource was processed
	5. Click on the 'Resources' -> 'List Own resources' and see your newly added LR that can be used by you or other users of the EUROSENTIMENT LRP
	
