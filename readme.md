FB Connect JS SDK with external datasources
===============================

This is a fork of the Facebook Connect JavaScript SDK with support for connecting to other graph data sources than Facebook. This readme will explain what is added to the Facebook SDK. Please see [Facebook Connect JavaScript SDK][Facebook Connect JavaScript SDK] for details on all the rest of the library.

[Facebook Connect JavaScript SDK]: http://github.com/facebook/connect-js "Facebook Connect JavaScript SDK"


What does "external datasource" mean?
------

This version of connect.js allows you to connect to other datasources than facebook through the graph API. Set up a database server that follows the FB graph standard, and this API can talk to it. 

Getting a server running
-----

There is currently work beeing done on a beta backend server that wraps a [Neo4j][Neo4j] graph database and exposes its data the same way facebook does. It should be available shortly.

Using a full blood graph database like [Neo4j][Neo4j] enables you to fully benifit from using the graph API. A graph database backend opens the possibility for more advanced paths (such as XPath) in the future.

[Neo4j]: http://neo4j.org "Neo4j"

Usage
-----

Initiate connect.js with the "external_domains" parameter:

    FB.init({
        appId  : 'YOUR APP ID',
        status : true, // check login status
        cookie : true, // enable cookies to allow the server to access the session
        xfbml  : true, // parse XFBML

        external_domains : {
            myserver : 'http://graph.example.com/'
        }

    });

Access your external domain through namespacing the api paths:

    FB.api('myserver:/path/to/data', function(response) {
        
    });

The namespace "fb:" is available by default for consistency. If you do not provide a namespace the SDK behaves the same as the standard facebook connect.js.
