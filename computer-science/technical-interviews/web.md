# Web

## HTTP

* **Which ones are the HTTP request methods?**
  * **GET:** Requests a representation of the specified resource.
  * **HEAD:** Same as Get but without the response body.
  * **POST:** Used to submit data to be processed to a specified resource. Often used when submitting form data or uploading a file.
  * **PUT:** Updates a current resource or creates a new resource.
  * **DELETE:** Requests to remove the specified resource.
  * **CONNECT:** Establishes a network connection to a resource, usually used for SSL tunneling.
  * **OPTIONS:** Returns the HTTP methods that the server supports for the specified URL.
  * **TRACE:** Echoes back the received request so the client can see what changes or additions have been made by intermediate servers.
  * **PATCH:** Used to apply partial modifications to a resource.
* **What are the differences between put and patch?**
  * **Purpose:** _PUT_ is used to update an existing resource or create a new one and _PATCH_ is used to apply partial modifications.
  * **Idempotency**: _PUT_ is idempotent but _PATCH_ might not be idempotent.
  * **Payload**: _PUT_ typically requires the client to send the entire representation of the resource and _PATCH_ only requires the modified parts
* **What is SSL and how it works?**
* **What are websockets?**
* **What is CORS?**

## AWS

* **In AWS, what is the CloudWatch service used for?**
  * Monitoring and observability service allowing users to collect and track metrics, collect and monitor log files, set alarms and automatically react to changes in AWS resources.
* **Which AWS service is used to restrict who can access other AWS services and resources?**
  * AWS Identity and Access Management (IAM)
* **Is AWS DynamoDB a SQL or NoSQL database?**
  * NoSQL
* **What is the serverless SQL database service in AWS called?**
  * Lambda or Fargate
