# HTTP Protocol

## the difference between GET and POST requests

Post and Get are two methods of HTTP requests. The differences are as follows:
**Application scene:** A GET request is an idempotent request. Generally, a Get request is used in scene where it does not affect server resources, such as requesting a webpage resource. Post is not an idempotent request and is generally used in scene where it may affect server resources, such as registering users.

**Whether to cache:** Because the application scene of the two are different, browsers generally cache Get requests, but rarely cache Post requests.

**The format of the message sent:** The entity part of the Get request message is empty, while the entity part of the Post request message is generally data sent to the server.

**Security:** Get requests can put the requested parameters into the URL and send them to the server, which is less secure compared to Post requests because the requested URL will be kept in the history record.

**Request length:** Due to the limitation on URL length in browsers, it can affect the length of the get request when sending data. This restriction is specified by the browser, not by RFC.

**Parameter type:** The parameter passing of post supports more data types.
