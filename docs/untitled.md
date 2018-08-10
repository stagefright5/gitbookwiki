# Untitled

## ntitled

### API tutorial {#title-text}

### API tutorial {#title-text}

* [Start MongoDB and RESTHeart](../documentation/api-tutorial.md#APItutorial-StartMongoDBandRESTHeart)
* [Create a Database ](../documentation/api-tutorial.md#APItutorial-CreateaDatabase)
* [Create a Collection](../documentation/api-tutorial.md#APItutorial-CreateaCollection)
* [Create two Documents](https://softinstigate.atlassian.net/wiki/spaces/RH/pages/9207832/API+tutorial#APItutorial-CreatetwoDocuments)
* [Get all Documents from the Collection](../documentation/api-tutorial.md#APItutorial-GetallDocumentsfromtheCollection)
* [GET Document by URL \(by id\)](../documentation/api-tutorial.md#APItutorial-GetallDocumentsfromtheCollection)

In this tutorial we’ll use RESTHeart to create a db, a collection and a couple of documents in MongoDB.

RESTHeart represents resources as HAL+JSON documents. Before going further you might want to check:

* [Installation and Setup](https://softinstigate.atlassian.net/wiki/spaces/RH/pages/9207828/Installation+and+Setup)
* [Resource Representation Format](https://softinstigate.atlassian.net/wiki/spaces/RH/pages/9207888/Representation+Format)
* the [HAL specification](http://stateless.co/hal_specification.html)

We’ll use [httpie](http://httpie.org/), a brilliant command line HTTP client \(you can also use curl of course!\).

If you just want to play with RESTHeart without installing it, you can use our [online test instance](http://restheart.org/try.html). This instance is constrained to document-related operations on the collection _/db/coll_, you can't create databases or collections there.

#### Start MongoDB and RESTHeart {#APItutorial-StartMongoDBandRESTHeart}

