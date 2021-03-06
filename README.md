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

- Request
  curl -X POST -H "Content-Type:application/json" -H "X-Custom-Id: 16cfbefd-28b3-4428-8221-95821cae8e77" -d @subscription.json https://codeacademy.co.in/api/v1/doc
 
- Response
  {"cs":201,"data":{"_id":{"ro":"3124Y"}}}


# READ Single Document
  - Use API Key to read any json document. 
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
- Request
  curl -X POST -H "Content-Type:application/json" -H "X-Custom-Id: 16cfbefd-28b3-4428-8221-95821cae8e77" -d @query.json https://codeacademy.co.in/api/v1/filter?query=one

- Response
  {"cs":200,"data":{"_id":{"ro":"3124Y"},"ct":25,"cs":10,"cd":{"email":"john.doe.1@gmail.com","options":["News","Promos"]}}}

# READ Single Partial Document
  - Use API Key to read any json document. 
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
- Request
  curl -X POST -H "Content-Type:application/json" -H "X-Custom-Id: 16cfbefd-28b3-4428-8221-95821cae8e77" -d @query.json https://codeacademy.co.in/api/v1/filter?query=one

- Response
  {"cs":200,"data":{"_id":{"ro":"3124Y"},"cd":{"email":"john.doe.1@gmail.com","options":["News","Promos"]}}}

# READ Many Documents
  - Use API Key to read json document. 
  - The Document must follow Code Academy QueryFilter class.
  - Use this sample for current demo. Read all Active(10) Subscriptions(25)

```sh
{
		 "pn" : 1,
		 "ps" : 20,
		 "andMap" : {
			 "ct" : 25,
			 "cs" : 10
		 },
	    "proj" : ["cd"]
}
```
- Request
  curl -X POST -H "Content-Type:application/json" -H "X-Custom-Id: 16cfbefd-28b3-4428-8221-95821cae8e77" -d @query.json https://codeacademy.co.in/api/v1/filter?query=many

- Response
  Returns 1st 20 Documents with 'cd' field for Active Subscriptions.
  
# READ Many Documents from Different document types
  - Use API Key to read json document. 
  - The Document must follow Code Academy QueryFilter class.
  - Use this sample for current demo. Read all Active(10) Subscriptions(25) and Comments(18)

```sh
{
		 "pn" : 1,
		 "ps" : 50,
		 "andMap" : {
			 "ct" : [18,25],
			 "cs" : 10
		 },
	    "proj" : ["ct", "cd"]
	}
```
- Request
  curl -X POST -H "Content-Type:application/json" -H "X-Custom-Id: 16cfbefd-28b3-4428-8221-95821cae8e77" -d @query.json https://codeacademy.co.in/api/v1/filter?query=many

- Response
  Returns 1st 50 Documents with 'ct' and 'cd' fields for Active Subscriptions and Comments.
  
  
### Development

    Issue or comment write to manager@codeacademy.co.in

### Todos
 - Update document
 - Patch document
 - Sort documents
