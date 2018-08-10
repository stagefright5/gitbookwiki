# Initial page

## Un-Untitled

### API tutorial {#title-text}

* [Start MongoDB and RESTHeart](https://github.com/stagefright5/gitbookwiki/tree/49e1067a57da8b0686c3ef907b3ec95da7ee1f69/documentation/api-tutorial.md#APItutorial-StartMongoDBandRESTHeart)
* [Create a Database ](https://github.com/stagefright5/gitbookwiki/tree/49e1067a57da8b0686c3ef907b3ec95da7ee1f69/documentation/api-tutorial.md#APItutorial-CreateaDatabase)
* [Create a Collection](https://github.com/stagefright5/gitbookwiki/tree/49e1067a57da8b0686c3ef907b3ec95da7ee1f69/documentation/api-tutorial.md#APItutorial-CreateaCollection)
* [Create two Documents](https://softinstigate.atlassian.net/wiki/spaces/RH/pages/9207832/API+tutorial#APItutorial-CreatetwoDocuments)
* [Get all Documents from the Collection](https://github.com/stagefright5/gitbookwiki/tree/49e1067a57da8b0686c3ef907b3ec95da7ee1f69/documentation/api-tutorial.md#APItutorial-GetallDocumentsfromtheCollection)
* [GET Document by URL \(by id\)](https://github.com/stagefright5/gitbookwiki/tree/49e1067a57da8b0686c3ef907b3ec95da7ee1f69/documentation/api-tutorial.md#APItutorial-GetallDocumentsfromtheCollection)

In this tutorial we’ll use RESTHeart to create a db, a collection and a couple of documents in MongoDB.

RESTHeart represents resources as HAL+JSON documents. Before going further you might want to check:

* [Installation and Setup](https://softinstigate.atlassian.net/wiki/spaces/RH/pages/9207828/Installation+and+Setup)
* [Resource Representation Format](https://softinstigate.atlassian.net/wiki/spaces/RH/pages/9207888/Representation+Format)
* the [HAL specification](http://stateless.co/hal_specification.html)

We’ll use [httpie](http://httpie.org/), a brilliant command line HTTP client \(you can also use curl of course!\).

If you just want to play with RESTHeart without installing it, you can use our [online test instance](http://restheart.org/try.html). This instance is constrained to document-related operations on the collection _/db/coll_, you can't create databases or collections there.

#### Start MongoDB and RESTHeart {#APItutorial-StartMongoDBandRESTHeart}

| \`\` |
| :--- |


```text
$ mongod --fork --syslog$ java -jar restheart.jar14:21:54.854 
[main] INFO  org.restheart.Bootstrapper - Starting RESTHeart14:21:54.857 
[main] INFO  org.restheart.Bootstrapper - version 2.0.014:21:54.862 
[main] INFO  org.restheart.Bootstrapper - Logging to file /var/folders/yx/mgksqtzn41j41xdnv74snjpc0000gn/T/restheart.log with level INFO14:21:54.862 [main] INFO  org.restheart.Bootstrapper - Logging to console with level INFO14:21:55.080 [main] INFO  org.restheart.Bootstrapper - MongoDB connection pool initialized14:21:55.080 [main] 
INFO  org.restheart.Bootstrapper - MongoDB version 3.2.014:21:55.080 
[main] WARN  org.restheart.Bootstrapper - ***** No Identity Manager specified. Authentication disabled.14:21:55.080 
[main] WARN  org.restheart.Bootstrapper - ***** No access manager specified. users can do anything.14:21:55.081 
[main] INFO  org.restheart.Bootstrapper - Token based authentication enabled with token TTL 15 minutes14:21:55.302 
[main] INFO  org.restheart.Bootstrapper - HTTPS listener bound at 0.0.0.0:444314:21:55.303 
[main] INFO  org.restheart.Bootstrapper - HTTP listener bound at 0.0.0.0:808014:21:55.304 [main] INFO  org.restheart.Bootstrapper - Local cache for db and collection properties enabled with TTL 1000 msecs14:21:55.304 [main] INFO  org.restheart.Bootstrapper - Local cache for schema stores not enabled14:21:55.428 [main] INFO  org.restheart.Bootstrapper - URL / bound to MongoDB resource *14:21:55.560 [main] INFO  org.restheart.Bootstrapper - Embedded static resources browser extracted in /var/folders/yx/mgksqtzn41j41xdnv74snjpc0000gn/T/restheart-197996856511506935614:21:55.577 [main] INFO  org.restheart.Bootstrapper - URL /browser bound to static resources browser. Access Manager: false14:21:55.783 [main] INFO  org.restheart.Bootstrapper - Pid file /var/folders/yx/mgksqtzn41j41xdnv74snjpc0000gn/T/restheart-0.pid14:21:55.783 [main] INFO  org.restheart.Bootstrapper - RESTHeart started
```

#### Create a Database {#APItutorial-CreateaDatabase}

**request**

```http
http PUT 127.0.0.1:8080/db/coll 
desc='this is my first collection created with restheart'
```

**response**

#### Create a Collection {#APItutorial-CreateaCollection}

**request**

**response**

```http
HTTP/1.1 201 
CreatedAccess-Control-Allow-Credentials: 
trueAccess-Control-Allow-Origin: *Access-Control-Expose-Headers: Location, ETag, Auth-Token, Auth-Token-Valid-Until, Auth-Token-Location, 
X-Powered-ByConnection: keep-aliveContent-Length: 0Date: Tue, 08 Mar 2016 13:24:31 
GMTETag: 56ded28e2d174c2a08cdee81X-Powered-By: restheart.org
```

#### Create two Documents {#APItutorial-CreatetwoDocuments}

**request**

```http
http POST 127.0.0.1:8080/db/coll name='restheart' rating='super cool'
```

**response**

```http
HTTP/1.1 201 CreatedAccess-Control-Allow-Credentials: trueAccess-Control-Allow-Origin: *Access-Control-Expose-Headers: Location, 
ETag, Auth-Token, Auth-Token-Valid-Until, Auth-Token-Location, 
X-Powered-ByConnection: keep-aliveContent-Length: 
0Date: Tue, 08 Mar 2016 13:25:40 
GMTETag: 56ded2d42d174c2a08cdee84Location: 
http://127.0.0.1:8080/db/coll/56ded2d4ad66b2a1e741c053
X-Powered-By: restheart.org
```

**request**

```http
http POST 127.0.0.1:8080/db/coll name='mongodb' rating='hyper cool'
```

**response**

```http
HTTP/1.1 201 CreatedAccess-Control-Allow-Credentials: 
trueAccess-Control-Allow-Origin: *Access-Control-Expose-Headers: Location, ETag, Auth-Token, Auth-Token-Valid-Until, Auth-Token-Location, 
X-Powered-ByConnection: keep-aliveContent-Length: 
0Date: Tue, 08 Mar 2016 13:26:06 
GMTETag: 56ded2ee2d174c2a08cdee85Location: 
http://127.0.0.1:8080/db/coll/56ded2eead66b2a1e741c054
X-Powered-By: restheart.org
```

#### Get all Documents from the Collection {#APItutorial-GetallDocumentsfromtheCollection}

**request**

```text
$ http GET 127.0.0.1:8080/db/coll
```

**response**

```http
HTTP/1.1 200 
OKAccess-Control-Allow-Credentials: trueAccess-Control-Allow-Origin: *Access-Control-Expose-Headers: Location, ETag, Auth-Token, Auth-Token-Valid-Until, Auth-Token-Location, 
X-Powered-ByConnection: keep-alive
Content-Encoding: gzipContent-Length: 235
Content-Type: application/hal+json
Date: Tue, 08 Mar 2016 13:26:29 
GMTETag: 56ded2b22d174c2a08cdee83X-Powered-By: 
restheart.org {    
"_embedded": {
                "rh:doc": [
                    {
                    "_etag": {
                        "$oid": "56ded2ee2d174c2a08cdee85"
                },
                "_id": {
                   "$oid": "56ded2eead66b2a1e741c054"
                                   },                
                                   "name": "mongodb",
                                   "rating": "hyper cool"            
                                   },            
                                   {                "_etag": {
                                       "$oid": "56ded2d42d174c2a08cdee84"
                                       },                
                                       "_id": {                    
                                       "$oid": "56ded2d4ad66b2a1e741c053"
                                              },                
                                              "name": "restheart",                
                                              "rating": "super cool"            
                                              }        
                              ]    
                              },    
                              "_etag": {        
                              "$oid": "56ded2b22d174c2a08cdee83"    
                              },    
                              "_id": "coll",    
                              "_returned": 2,    
                              "desc": "this is my first collection created with restheart"
              }
```

The interesting part of the returned HAL+JSON object is the \_embedded object:

```javascript
{    "rh:doc": [        
{            
"_etag": {                
"$oid": "56ded2ee2d174c2a08cdee85"            
},            
"_id": {                
"$oid": "56ded2eead66b2a1e741c054"            
},            
"name": "mongodb",            
"rating": "hyper cool"        
},        
{            
"_etag": {                
"$oid": "56ded2d42d174c2a08cdee84"            
},            
"_id": {                
"$oid": "56ded2d4ad66b2a1e741c053"            
},
"name": "restheart",            
"rating": "super cool"        
}    
]
}
```

#### GET Document by URL \(by id\) {#APItutorial-GETDocumentbyURL(byid)}

**request**

| `$ http GET 127.0.0.1:8080/db/coll/56ded2eead66b2a1e741c054` |
| :--- |


**response**

```http
HTTP/1.1 200 OK
Access-Control-Allow-Credentials: true
Access-Control-Allow-Origin: *Access-Control-Expose-Headers: Location, ETag, Auth-Token, Auth-Token-Valid-Until, Auth-Token-Location, X-Powered-By
Connection: keep-alive
Content-Encoding: gzip
Content-Length: 204
Content-Type: application/hal+json
Date: Tue, 08 Mar 2016 13:28:18 GMT
ETag: 56ded2b22d174c2a08cdee83X-Powered-By: restheart.org {
   "_embedded": {        
   "rh:doc": [ 
              { 
                 "_etag": {                    
                 "$oid": "56ded2d42d174c2a08cdee84"                
                 },                
                 "_id": {
                                     "$oid": "56ded2d4ad66b2a1e741c053"                
                                     },                
                                     "name": "restheart",                
               "rating": "super cool"            
               }        
               ]    
               },    
               "_etag": {        
               "$oid": "56ded2b22d174c2a08cdee83"    
               },    
               "_id": "coll",    
               "_returned": 1,    
               "desc": "this is my first collection created with restheart"
               }
```

#### Query documents by name property \(using Collection filter\) {#APItutorial-Querydocumentsbynameproperty(usingCollectionfilter)}

* [Start MongoDB and RESTHeart](https://github.com/stagefright5/gitbookwiki/tree/49e1067a57da8b0686c3ef907b3ec95da7ee1f69/documentation/api-tutorial.md#APItutorial-StartMongoDBandRESTHeart)
* [Create a Database ](https://github.com/stagefright5/gitbookwiki/tree/49e1067a57da8b0686c3ef907b3ec95da7ee1f69/documentation/api-tutorial.md#APItutorial-CreateaDatabase)
* [Create a Collection](https://github.com/stagefright5/gitbookwiki/tree/49e1067a57da8b0686c3ef907b3ec95da7ee1f69/documentation/api-tutorial.md#APItutorial-CreateaCollection)
* [Create two Documents](https://softinstigate.atlassian.net/wiki/spaces/RH/pages/9207832/API+tutorial#APItutorial-CreatetwoDocuments)
* [Get all Documents from the Collection](https://github.com/stagefright5/gitbookwiki/tree/49e1067a57da8b0686c3ef907b3ec95da7ee1f69/documentation/api-tutorial.md#APItutorial-GetallDocumentsfromtheCollection)
* [GET Document by URL \(by id\)](https://github.com/stagefright5/gitbookwiki/tree/49e1067a57da8b0686c3ef907b3ec95da7ee1f69/documentation/api-tutorial.md#APItutorial-GetallDocumentsfromtheCollection)

### API tutorial {#title-text}

* [Start MongoDB and RESTHeart](https://github.com/stagefright5/gitbookwiki/tree/49e1067a57da8b0686c3ef907b3ec95da7ee1f69/documentation/api-tutorial.md#APItutorial-StartMongoDBandRESTHeart)
* [Create a Database ](https://github.com/stagefright5/gitbookwiki/tree/49e1067a57da8b0686c3ef907b3ec95da7ee1f69/documentation/api-tutorial.md#APItutorial-CreateaDatabase)
* [Create a Collection](https://github.com/stagefright5/gitbookwiki/tree/49e1067a57da8b0686c3ef907b3ec95da7ee1f69/documentation/api-tutorial.md#APItutorial-CreateaCollection)
* [Create two Documents](https://softinstigate.atlassian.net/wiki/spaces/RH/pages/9207832/API+tutorial#APItutorial-CreatetwoDocuments)
* [Get all Documents from the Collection](https://github.com/stagefright5/gitbookwiki/tree/49e1067a57da8b0686c3ef907b3ec95da7ee1f69/documentation/api-tutorial.md#APItutorial-GetallDocumentsfromtheCollection)
* [GET Document by URL \(by id\)](https://github.com/stagefright5/gitbookwiki/tree/49e1067a57da8b0686c3ef907b3ec95da7ee1f69/documentation/api-tutorial.md#APItutorial-GetallDocumentsfromtheCollection)

In this tutorial we’ll use RESTHeart to create a db, a collection and a couple of documents in MongoDB.

RESTHeart represents resources as HAL+JSON documents. Before going further you might want to check:

* [Installation and Setup](https://softinstigate.atlassian.net/wiki/spaces/RH/pages/9207828/Installation+and+Setup)
* [Resource Representation Format](https://softinstigate.atlassian.net/wiki/spaces/RH/pages/9207888/Representation+Format)
* the [HAL specification](http://stateless.co/hal_specification.html)

We’ll use [httpie](http://httpie.org/), a brilliant command line HTTP client \(you can also use curl of course!\).

If you just want to play with RESTHeart without installing it, you can use our [online test instance](http://restheart.org/try.html). This instance is constrained to document-related operations on the collection _/db/coll_, you can't create databases or collections there.

#### Start MongoDB and RESTHeart {#APItutorial-StartMongoDBandRESTHeart}

| \`\` |
| :--- |


```text
$ mongod --fork --syslog$ java -jar restheart.jar14:21:54.854 
[main] INFO  org.restheart.Bootstrapper - Starting RESTHeart14:21:54.857 
[main] INFO  org.restheart.Bootstrapper - version 2.0.014:21:54.862 
[main] INFO  org.restheart.Bootstrapper - Logging to file /var/folders/yx/mgksqtzn41j41xdnv74snjpc0000gn/T/restheart.log with level INFO14:21:54.862 [main] INFO  org.restheart.Bootstrapper - Logging to console with level INFO14:21:55.080 [main] INFO  org.restheart.Bootstrapper - MongoDB connection pool initialized14:21:55.080 [main] 
INFO  org.restheart.Bootstrapper - MongoDB version 3.2.014:21:55.080 
[main] WARN  org.restheart.Bootstrapper - ***** No Identity Manager specified. Authentication disabled.14:21:55.080 
[main] WARN  org.restheart.Bootstrapper - ***** No access manager specified. users can do anything.14:21:55.081 
[main] INFO  org.restheart.Bootstrapper - Token based authentication enabled with token TTL 15 minutes14:21:55.302 
[main] INFO  org.restheart.Bootstrapper - HTTPS listener bound at 0.0.0.0:444314:21:55.303 
[main] INFO  org.restheart.Bootstrapper - HTTP listener bound at 0.0.0.0:808014:21:55.304 [main] INFO  org.restheart.Bootstrapper - Local cache for db and collection properties enabled with TTL 1000 msecs14:21:55.304 [main] INFO  org.restheart.Bootstrapper - Local cache for schema stores not enabled14:21:55.428 [main] INFO  org.restheart.Bootstrapper - URL / bound to MongoDB resource *14:21:55.560 [main] INFO  org.restheart.Bootstrapper - Embedded static resources browser extracted in /var/folders/yx/mgksqtzn41j41xdnv74snjpc0000gn/T/restheart-197996856511506935614:21:55.577 [main] INFO  org.restheart.Bootstrapper - URL /browser bound to static resources browser. Access Manager: false14:21:55.783 [main] INFO  org.restheart.Bootstrapper - Pid file /var/folders/yx/mgksqtzn41j41xdnv74snjpc0000gn/T/restheart-0.pid14:21:55.783 [main] INFO  org.restheart.Bootstrapper - RESTHeart started
```

#### Create a Database {#APItutorial-CreateaDatabase}

**request**

```http
http PUT 127.0.0.1:8080/db/coll 
desc='this is my first collection created with restheart'
```

**response**

#### Create a Collection {#APItutorial-CreateaCollection}

**request**

**response**

```http
HTTP/1.1 201 
CreatedAccess-Control-Allow-Credentials: 
trueAccess-Control-Allow-Origin: *Access-Control-Expose-Headers: Location, ETag, Auth-Token, Auth-Token-Valid-Until, Auth-Token-Location, 
X-Powered-ByConnection: keep-aliveContent-Length: 0Date: Tue, 08 Mar 2016 13:24:31 
GMTETag: 56ded28e2d174c2a08cdee81X-Powered-By: restheart.org
```

#### Create two Documents {#APItutorial-CreatetwoDocuments}

**request**

```http
http POST 127.0.0.1:8080/db/coll name='restheart' rating='super cool'
```

**response**

```http
HTTP/1.1 201 CreatedAccess-Control-Allow-Credentials: trueAccess-Control-Allow-Origin: *Access-Control-Expose-Headers: Location, 
ETag, Auth-Token, Auth-Token-Valid-Until, Auth-Token-Location, 
X-Powered-ByConnection: keep-aliveContent-Length: 
0Date: Tue, 08 Mar 2016 13:25:40 
GMTETag: 56ded2d42d174c2a08cdee84Location: 
http://127.0.0.1:8080/db/coll/56ded2d4ad66b2a1e741c053
X-Powered-By: restheart.org
```

**request**

```http
http POST 127.0.0.1:8080/db/coll name='mongodb' rating='hyper cool'
```

**response**

```http
HTTP/1.1 201 CreatedAccess-Control-Allow-Credentials: 
trueAccess-Control-Allow-Origin: *Access-Control-Expose-Headers: Location, ETag, Auth-Token, Auth-Token-Valid-Until, Auth-Token-Location, 
X-Powered-ByConnection: keep-aliveContent-Length: 
0Date: Tue, 08 Mar 2016 13:26:06 
GMTETag: 56ded2ee2d174c2a08cdee85Location: 
http://127.0.0.1:8080/db/coll/56ded2eead66b2a1e741c054
X-Powered-By: restheart.org
```

#### Get all Documents from the Collection {#APItutorial-GetallDocumentsfromtheCollection}

**request**

```text
$ http GET 127.0.0.1:8080/db/coll
```

**response**

```http
HTTP/1.1 200 
OKAccess-Control-Allow-Credentials: trueAccess-Control-Allow-Origin: *Access-Control-Expose-Headers: Location, ETag, Auth-Token, Auth-Token-Valid-Until, Auth-Token-Location, 
X-Powered-ByConnection: keep-alive
Content-Encoding: gzipContent-Length: 235
Content-Type: application/hal+json
Date: Tue, 08 Mar 2016 13:26:29 
GMTETag: 56ded2b22d174c2a08cdee83X-Powered-By: 
restheart.org {    
"_embedded": {
                "rh:doc": [
                    {
                    "_etag": {
                        "$oid": "56ded2ee2d174c2a08cdee85"
                },
                "_id": {
                   "$oid": "56ded2eead66b2a1e741c054"
                                   },                
                                   "name": "mongodb",
                                   "rating": "hyper cool"            
                                   },            
                                   {                "_etag": {
                                       "$oid": "56ded2d42d174c2a08cdee84"
                                       },                
                                       "_id": {                    
                                       "$oid": "56ded2d4ad66b2a1e741c053"
                                              },                
                                              "name": "restheart",                
                                              "rating": "super cool"            
                                              }        
                              ]    
                              },    
                              "_etag": {        
                              "$oid": "56ded2b22d174c2a08cdee83"    
                              },    
                              "_id": "coll",    
                              "_returned": 2,    
                              "desc": "this is my first collection created with restheart"
              }
```

The interesting part of the returned HAL+JSON object is the \_embedded object:

```javascript
{    "rh:doc": [        
{            
"_etag": {                
"$oid": "56ded2ee2d174c2a08cdee85"            
},            
"_id": {                
"$oid": "56ded2eead66b2a1e741c054"            
},            
"name": "mongodb",            
"rating": "hyper cool"        
},        
{            
"_etag": {                
"$oid": "56ded2d42d174c2a08cdee84"            
},            
"_id": {                
"$oid": "56ded2d4ad66b2a1e741c053"            
},
"name": "restheart",            
"rating": "super cool"        
}    
]
}
```

#### GET Document by URL \(by id\) {#APItutorial-GETDocumentbyURL(byid)}

**request**

| `$ http GET 127.0.0.1:8080/db/coll/56ded2eead66b2a1e741c054` |
| :--- |


**response**

```http
HTTP/1.1 200 OK
Access-Control-Allow-Credentials: true
Access-Control-Allow-Origin: *Access-Control-Expose-Headers: Location, ETag, Auth-Token, Auth-Token-Valid-Until, Auth-Token-Location, X-Powered-By
Connection: keep-alive
Content-Encoding: gzip
Content-Length: 204
Content-Type: application/hal+json
Date: Tue, 08 Mar 2016 13:28:18 GMT
ETag: 56ded2b22d174c2a08cdee83X-Powered-By: restheart.org {
   "_embedded": {        
   "rh:doc": [ 
              { 
                 "_etag": {                    
                 "$oid": "56ded2d42d174c2a08cdee84"                
                 },                
                 "_id": {
                                     "$oid": "56ded2d4ad66b2a1e741c053"                
                                     },                
                                     "name": "restheart",                
               "rating": "super cool"            
               }        
               ]    
               },    
               "_etag": {        
               "$oid": "56ded2b22d174c2a08cdee83"    
               },    
               "_id": "coll",    
               "_returned": 1,    
               "desc": "this is my first collection created with restheart"
               }
```

#### Query documents by name property \(using Collection filter\) {#APItutorial-Querydocumentsbynameproperty(usingCollectionfilter)}

In this tutorial we’ll use RESTHeart to create a db, a collection and a couple of documents in MongoDB.

RESTHeart represents resources as HAL+JSON documents. Before going further you might want to check:

* [Installation and Setup](https://softinstigate.atlassian.net/wiki/spaces/RH/pages/9207828/Installation+and+Setup)
* [Resource Representation Format](https://softinstigate.atlassian.net/wiki/spaces/RH/pages/9207888/Representation+Format)
* the [HAL specification](http://stateless.co/hal_specification.html)

We’ll use [httpie](http://httpie.org/), a brilliant command line HTTP client \(you can also use curl of course!\).

If you just want to play with RESTHeart without installing it, you can use our [online test instance](http://restheart.org/try.html). This instance is constrained to document-related operations on the collection _/db/coll_, you can't create databases or collections there.

#### Start MongoDB and RESTHeart {#APItutorial-StartMongoDBandRESTHeart}

| \`\` |
| :--- |


```text
$ mongod --fork --syslog$ java -jar restheart.jar14:21:54.854 
[main] INFO  org.restheart.Bootstrapper - Starting RESTHeart14:21:54.857 
[main] INFO  org.restheart.Bootstrapper - version 2.0.014:21:54.862 
[main] INFO  org.restheart.Bootstrapper - Logging to file /var/folders/yx/mgksqtzn41j41xdnv74snjpc0000gn/T/restheart.log with level INFO14:21:54.862 [main] INFO  org.restheart.Bootstrapper - Logging to console with level INFO14:21:55.080 [main] INFO  org.restheart.Bootstrapper - MongoDB connection pool initialized14:21:55.080 [main] 
INFO  org.restheart.Bootstrapper - MongoDB version 3.2.014:21:55.080 
[main] WARN  org.restheart.Bootstrapper - ***** No Identity Manager specified. Authentication disabled.14:21:55.080 
[main] WARN  org.restheart.Bootstrapper - ***** No access manager specified. users can do anything.14:21:55.081 
[main] INFO  org.restheart.Bootstrapper - Token based authentication enabled with token TTL 15 minutes14:21:55.302 
[main] INFO  org.restheart.Bootstrapper - HTTPS listener bound at 0.0.0.0:444314:21:55.303 
[main] INFO  org.restheart.Bootstrapper - HTTP listener bound at 0.0.0.0:808014:21:55.304 [main] INFO  org.restheart.Bootstrapper - Local cache for db and collection properties enabled with TTL 1000 msecs14:21:55.304 [main] INFO  org.restheart.Bootstrapper - Local cache for schema stores not enabled14:21:55.428 [main] INFO  org.restheart.Bootstrapper - URL / bound to MongoDB resource *14:21:55.560 [main] INFO  org.restheart.Bootstrapper - Embedded static resources browser extracted in /var/folders/yx/mgksqtzn41j41xdnv74snjpc0000gn/T/restheart-197996856511506935614:21:55.577 [main] INFO  org.restheart.Bootstrapper - URL /browser bound to static resources browser. Access Manager: false14:21:55.783 [main] INFO  org.restheart.Bootstrapper - Pid file /var/folders/yx/mgksqtzn41j41xdnv74snjpc0000gn/T/restheart-0.pid14:21:55.783 [main] INFO  org.restheart.Bootstrapper - RESTHeart started
```

#### Create a Database {#APItutorial-CreateaDatabase}

**request**

```http
http PUT 127.0.0.1:8080/db/coll 
desc='this is my first collection created with restheart'
```

**response**

#### Create a Collection {#APItutorial-CreateaCollection}

**request**

**response**

```http
HTTP/1.1 201 
CreatedAccess-Control-Allow-Credentials: 
trueAccess-Control-Allow-Origin: *Access-Control-Expose-Headers: Location, ETag, Auth-Token, Auth-Token-Valid-Until, Auth-Token-Location, 
X-Powered-ByConnection: keep-aliveContent-Length: 0Date: Tue, 08 Mar 2016 13:24:31 
GMTETag: 56ded28e2d174c2a08cdee81X-Powered-By: restheart.org
```

#### Create two Documents {#APItutorial-CreatetwoDocuments}

**request**

```http
http POST 127.0.0.1:8080/db/coll name='restheart' rating='super cool'
```

**response**

```http
HTTP/1.1 201 CreatedAccess-Control-Allow-Credentials: trueAccess-Control-Allow-Origin: *Access-Control-Expose-Headers: Location, 
ETag, Auth-Token, Auth-Token-Valid-Until, Auth-Token-Location, 
X-Powered-ByConnection: keep-aliveContent-Length: 
0Date: Tue, 08 Mar 2016 13:25:40 
GMTETag: 56ded2d42d174c2a08cdee84Location: 
http://127.0.0.1:8080/db/coll/56ded2d4ad66b2a1e741c053
X-Powered-By: restheart.org
```

**request**

```http
http POST 127.0.0.1:8080/db/coll name='mongodb' rating='hyper cool'
```

**response**

```http
HTTP/1.1 201 CreatedAccess-Control-Allow-Credentials: 
trueAccess-Control-Allow-Origin: *Access-Control-Expose-Headers: Location, ETag, Auth-Token, Auth-Token-Valid-Until, Auth-Token-Location, 
X-Powered-ByConnection: keep-aliveContent-Length: 
0Date: Tue, 08 Mar 2016 13:26:06 
GMTETag: 56ded2ee2d174c2a08cdee85Location: 
http://127.0.0.1:8080/db/coll/56ded2eead66b2a1e741c054
X-Powered-By: restheart.org
```

#### Get all Documents from the Collection {#APItutorial-GetallDocumentsfromtheCollection}

**request**

```text
$ http GET 127.0.0.1:8080/db/coll
```

**response**

```http
HTTP/1.1 200 
OKAccess-Control-Allow-Credentials: trueAccess-Control-Allow-Origin: *Access-Control-Expose-Headers: Location, ETag, Auth-Token, Auth-Token-Valid-Until, Auth-Token-Location, 
X-Powered-ByConnection: keep-alive
Content-Encoding: gzipContent-Length: 235
Content-Type: application/hal+json
Date: Tue, 08 Mar 2016 13:26:29 
GMTETag: 56ded2b22d174c2a08cdee83X-Powered-By: 
restheart.org {    
"_embedded": {
                "rh:doc": [
                    {
                    "_etag": {
                        "$oid": "56ded2ee2d174c2a08cdee85"
                },
                "_id": {
                   "$oid": "56ded2eead66b2a1e741c054"
                                   },                
                                   "name": "mongodb",
                                   "rating": "hyper cool"            
                                   },            
                                   {                "_etag": {
                                       "$oid": "56ded2d42d174c2a08cdee84"
                                       },                
                                       "_id": {                    
                                       "$oid": "56ded2d4ad66b2a1e741c053"
                                              },                
                                              "name": "restheart",                
                                              "rating": "super cool"            
                                              }        
                              ]    
                              },    
                              "_etag": {        
                              "$oid": "56ded2b22d174c2a08cdee83"    
                              },    
                              "_id": "coll",    
                              "_returned": 2,    
                              "desc": "this is my first collection created with restheart"
              }
```

The interesting part of the returned HAL+JSON object is the \_embedded object:

```javascript
{    "rh:doc": [        
{            
"_etag": {                
"$oid": "56ded2ee2d174c2a08cdee85"            
},            
"_id": {                
"$oid": "56ded2eead66b2a1e741c054"            
},            
"name": "mongodb",            
"rating": "hyper cool"        
},        
{            
"_etag": {                
"$oid": "56ded2d42d174c2a08cdee84"            
},            
"_id": {                
"$oid": "56ded2d4ad66b2a1e741c053"            
},
"name": "restheart",            
"rating": "super cool"        
}    
]
}
```

#### GET Document by URL \(by id\) {#APItutorial-GETDocumentbyURL(byid)}

**request**

| `$ http GET 127.0.0.1:8080/db/coll/56ded2eead66b2a1e741c054` |
| :--- |


**response**

```http
HTTP/1.1 200 OK
Access-Control-Allow-Credentials: true
Access-Control-Allow-Origin: *Access-Control-Expose-Headers: Location, ETag, Auth-Token, Auth-Token-Valid-Until, Auth-Token-Location, X-Powered-By
Connection: keep-alive
Content-Encoding: gzip
Content-Length: 204
Content-Type: application/hal+json
Date: Tue, 08 Mar 2016 13:28:18 GMT
ETag: 56ded2b22d174c2a08cdee83X-Powered-By: restheart.org {
   "_embedded": {        
   "rh:doc": [ 
              { 
                 "_etag": {                    
                 "$oid": "56ded2d42d174c2a08cdee84"                
                 },                
                 "_id": {
                                     "$oid": "56ded2d4ad66b2a1e741c053"                
                                     },                
                                     "name": "restheart",                
               "rating": "super cool"            
               }        
               ]    
               },    
               "_etag": {        
               "$oid": "56ded2b22d174c2a08cdee83"    
               },    
               "_id": "coll",    
               "_returned": 1,    
               "desc": "this is my first collection created with restheart"
               }
```

#### Query documents by name property \(using Collection filter\) {#APItutorial-Querydocumentsbynameproperty(usingCollectionfilter)}

## name: restheart

```http
               "rating": "super cool"            
               }        
               ]    
               },    
               "_etag": {        
               "$oid": "56ded2b22d174c2a08cdee83"    
               },    
               "_id": "coll",    
               "_returned": 1,    
               "desc": "this is my first collection created with restheart"
               }
```

#### Query documents by name property \(using Collection filter\) {#APItutorial-Querydocumentsbynameproperty(usingCollectionfilter)}

