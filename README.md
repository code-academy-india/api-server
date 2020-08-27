# api-server

Desker API-Server

api-server is  a cloud-enabled, mobile-ready API Server with JSON Document store.

  - No need to manage os,containers,web servers,application servers and databases.
  - Prototype or build your web or mobile application in quick time.
  - Use cURL as REST Client to try these samples.

# API Key

  - Request
    curl -H "Content-Type:application/json" -H "X-CA-AccName:Code Academy" https://codeacademy.co.in/api/v1/accKey
  - Response
    {"cs":200,"data":{"apiKey":"16cfbefd-28b3-4428-8221-95821cae8e77","userId":"system","userName":"Code Academy"}}


# POST Document
  - Use API Key to add any json document. 
  - The Document must follow Code Academy Model class.
  - Use this sample for current demo. Assume you are posting Subscription document as subscription.json
```sh
 {
 	 "ct" : 25,
     "cs" : 10,
     "cn" : "John Doe",
     "ra" : {
         "cui" : "system",
         "cda" : 1552320926554,
         "cna" : "Code Academy"
     },
     "ve" : 0,
     "data" : "v1",
     "srcId" : 10,
     "cd" : {
  		"email" : "john.doe.1@gmail.com",
  		"options": [
  			"News",
  			"Promos"
  		]
  	}
 }
 ```
- Response
{"cs":201,"data":{"_id":{"ro":"3124Y"}}}

# READ Full Document
  - Use API Key to add any json document. 
  - The Document must follow Code Academy QueryFilter class.
  - Use this sample for current demo. Assume you are reading document with id 3124Y
```sh
 {
 	"m" : {
 	    "_id" : {
 	      "ro" : "3124Y"
 	    }
 	},
    "proj" : [ "null"]
 }
```
- Response
{"cs":200,"data":{"_id":{"ro":"3124Y"},"ct":25,"cs":10,"cd":{"email":"john.doe.1@gmail.com","options":["News","Promos"]}}}

# READ Partial Document
  - Use API Key to add any json document. 
  - The Document must follow Code Academy QueryFilter class.
  - Use this sample for current demo. Assume you are reading document with id 3124Y
```sh
 {
 	"m" : {
 	    "_id" : {
 	      "ro" : "3124Y"
 	    }
 	},
    "proj" : [ "cd"]
 }
```
- Response
{"cs":200,"data":{"_id":{"ro":"3124Y"},"cd":{"email":"john.doe.1@gmail.com","options":["News","Promos"]}}}

### Development

    Issue or comment write to manager@codeacademy.co.in

### Todos
 - Update document
 - Patch document



