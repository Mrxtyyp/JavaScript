# HTTP Protocol

## the difference between GET and POST requests

Post and Get are two methods of HTTP requests. The differences are as follows:
**Application scene:** A GET request is an idempotent request. Generally, a Get request is used in scene where it does not affect server resources, such as requesting a webpage resource. Post is not an idempotent request and is generally used in scene where it may affect server resources, such as registering users.

**Whether to cache:** Because the application scene of the two are different, browsers generally cache Get requests, but rarely cache Post requests.

**The format of the message sent:** The entity part of the Get request message is empty, while the entity part of the Post request message is generally data sent to the server.

**Security:** Get requests can put the requested parameters into the URL and send them to the server, which is less secure compared to Post requests because the requested URL will be kept in the history record.

**Request length:** Due to the limitation on URL length in browsers, it can affect the length of the get request when sending data. This restriction is specified by the browser, not by RFC.

**Parameter type:** The parameter passing of post supports more data types.

## The difference between POST and PUT requests

A PUT request is to send data to the server to modify the content of the data, but it does not increase the type of data, which means that no matter how many times a PUT operation is performed, the result is not different. (Can be understood as updating data on a regular basis)

A POST request is a request to send data to the server, which changes the type of data and other resources, and creates new content. (Can be understood as creating data)

## Common HTTP request and response headers

Common HTTP Request Headers:
● Accept: The types of content that browsers can handle
● Accept-Charset: The character set that the browser can display
● Accept-Encoding：The compression encoding that browsers can handle
● Accept-Language：The language currently set by the browser
● Connection： The type of connection between browser and server
● Cookie：Any cookies set on the current page
● Host：The domain where the requested page is located
● Referer： The URL of the requested page
● User-Agent： The user agent string for the browser

Common response headers for HTTP Response Headers:
● Date：Indicates the time when the message was sent, and the format for describing the time is defined by rfc822
● server: Server name
● Connection：Type of connection between browser and server
● Cache-Control：Control HTTP caching
● content-type: What MIME type does the following document belong to

There are four common Content-Type attribute values:
（1）application/x-www-form-urlencoded：
application/x-www-form-urlencoded: A browser's native form form. If the enctype attribute is not set, it will eventually submit data as application/x-www-form-urlencoded. The data submitted in this way is placed in the body, and the data is encoded in the way of key1=val1&key2=val2. Both key and val perform URL transcoding.
（2）multipart/form-data：
multipart/form-data: This method is also a common POST submission method, which is commonly used when forms upload files.
（3）application/json：
application/json: The server message body is a serialized JSON string.
（4）text/xml：
text/xml: This mode is mainly used to submit data in XML format.

## HTTP status code 304 is more or less good

In order to improve the speed of website access, the server specifies the cache mechanism for some of the pages previously visited, when the client requests these pages here, the server will determine whether the page is the same as before according to the cache content, if the same, it will directly return 304, at this time the client calls the cache content, without having to download the second time.

Status code 304 should not be considered an error, but rather a response by the server when the client has a cache.

Search engine spiders tend to prefer sites with frequently updated content sources. The crawl frequency of the website is adjusted by the status code returned by the crawl of the website in a specific time. If the website has been in the state of 304 for a certain period of time, then the spider may reduce the number of times the website is crawled. On the contrary, if the frequency of the website changes very fast, each crawl can get new content, then over time, the return rate will increase.

Reasons for generating more 304 status codes:
● The page update period is long or not updated
● Pure static pages or force static html generation

Too many 304 status codes may cause the following problems:
● Site snapshot stops;
● Inclusion decrease;
● Weight drop
