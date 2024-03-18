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

## Common HTTP request methods

● GET: Get data from the server
● POST：Submitting an entity to a specified resource usually results in a modification of the server resource.
● PUT：Upload files, update data;
● DELETE：Delete objects on the server;
● HEAD：Gets the header of the message, and does not return the body of the message compared to GET;
● OPTIONS：Ask for supported request methods for cross-domain requests;
● CONNECT：It is required to establish a tunnel when communicating with the proxy server and use the tunnel for TCP communication.
● TRACE: The request received by the server is displayed for testing or diagnosis.

## OPTIONS Request method and application scene

OPTIONS is one of the HTTP request methods in addition to GET and POST.

The OPTIONS method is a functional option that can be used in the Request/response communication process to obtain the resource identified by the Request-URI. In this way, the client can decide what actions are necessary for a specific resource before making a request for that resource, or understand the performance of the server. The response of the request method cannot be cached.

The OPTIONS request method has two main uses:
● Gets all HTTP request methods supported by the server;
● Used to check access permissions. For example, in CORS cross-domain resource sharing, for complex requests, the OPTIONS method is used to send sniff requests to check whether the access permission to the specified resource is available.

## What are the differences between HTTP 1.0 and HTTP 1.1?

HTTP 1.0 and HTTP 1.1 have the following differences:

- For connections, http1.0 uses non-persistent connections by default, while http1.1 uses persistent connections by default. http1.1 avoids the latency required to establish a connection each time a non-persistent connection is used by using persistent connections to allow multiple http requests to reuse the same TCP connection.

- Resource request, in http1.0, there are some phenomena of wasting bandwidth, such as the client only needs a part of an object, while the server sends the whole object, and does not support the resumable function, http1.1 bring in the range header in the request header, which allows only a part of the resource to be requested, the return code is 206 (Partial Content), which makes it easy for developers to choose freely to make full use of bandwidth and connections.

- In terms of cache, http1.0 mainly uses If-Modified-Since and Expires in the header as the criteria for cache judgment, while http1.1 introduces more cache control strategies. For example, Etag, If-Unmodified-Since, If-Match, If-None-Match, and many more alternative cache headers control the cache policy.

- The host field has been added to HTTP 1.1 to specify the domain name of the server. In http1.0, each server is bound to a unique IP address, so the URL in the request message does not pass the hostname. However, with the development of virtual hosting technology, multiple virtual hosts can exist on a single physical server, and they share a single IP address. Hence the host field, which allows requests to be sent to different websites on the same server.

- http1.1 also adds many new request methods over http1.0, such as PUT, HEAD, OPTIONS, and so on.

## The difference between HTTP 1.1 and HTTP 2.0

- Binary protocol: HTTP/2 is a binary protocol. In HTTP/1.1, the header of the message must be text (ASCII encoding), and the data body can be either text or binary. HTTP/2 is a thorough binary protocol, header information and data body are binary, and collectively referred to as "frame", can be divided into header information frame and data frame. The concept of frame is the basis of its multiplexing.
- Multiplexing: HTTP/2 implements multiplexing, HTTP/2 still multiplexes TCP connections, but in a connection, both the client and the server can send multiple requests or responses at the same time, and do not send them one by one in order, so as to avoid the "Head-of-line blocking" [1] problem.

- Data stream：HTTP/2 uses the concept of data stream, because HTTP/2 packets are not sent sequentially, and successive packets within the same connection may belong to different requests. Therefore, the packet must be marked to indicate which request it belongs to. HTTP/2 refers to all packets of each request or response as a data stream. Each data stream has a unique number. When a packet is sent, it must be marked with a data stream ID to distinguish which data stream it belongs to.

- Header compression: HTTP/2 implements header compression, and since the HTTP 1.1 protocol is stateless, all information must be attached to each request. Therefore, many fields of the request are repeated, such as cookies and User Agent, the same content must be attached to each request, which will waste a lot of bandwidth and affect the speed. HTTP/2 optimizes this by introducing a header compression mechanism. On the one hand, header information is compressed using gzip or compress before being sent. On the other hand, the client and server maintain a header table at the same time, all the fields are stored in this table, generate an index number, and then do not send the same field, only send the index number, which can improve the speed.

- Server push: HTTP/2 allows the server to actively send resources to the client without request, which is called server push. By using server push to push the necessary resources to the client in advance, you can relatively reduce some latency. It should be noted here that the server actively pushes static resources under http2, and WebSocket and the use of SSE and other ways to send real-time data to the client push is different.

## Differences between HTTP and HTTPS

The main differences between HTTP and HTTPS are as follows:

- HTTPS requires a CA certificate and costs a lot. HTTP does not;
- HTTP is a hypertext transmission protocol, and information is transmitted in plain text. HTTPS is a secure SSL encryption transmission protocol.
- The port number varies according to the connection mode. The HTTP port number is 80, and the HTTPS port number is 443.
- HTTP connections are simple and stateless; HTTPS is a network protocol based on SSL and HTTP for encrypted transmission and identity authentication, and is more secure than HTTP.

## Reasons for the URL length limitation of the GET method

In fact, the HTTP protocol specification does not impose a limit on the url length requested by the get method, which is a specific browser and server limit.

Internet Explorer limits URL length to 2083 bytes (2K+35). Since Internet Explorer has a minimum allowable URL length, as long as the URL does not exceed 2083 bytes during development, it will work in all browsers without problems.

```js
GET的长度值 = URL（2083）- （你的Domain+Path）-2（2是get请求中?=两个字符的长度）
```

Let's take a look at the length limit range of URLs in the get method for mainstream browsers:

- Microsoft Internet Explorer (Browser) : Internet Explorer has a maximum URL limit of 2083 characters, if you exceed this number, the submit button does not respond.
- Firefox (Browser)：The URL length limit for Firefox is 65,536 characters.
- Safari (Browser) : The maximum URL length is 80,000 characters.
- Opera (Browser) : The maximum URL length is 190,000 characters.
- Google (chrome) : The maximum URL length is 8182 characters.

Mainstream servers limit the length of the url in the get method:

- Apache (Server) : Accepts a maximum url length of 8192 characters.
- Microsoft Internet Information Server(IIS) : Accepts a maximum url length of 16384 characters.

Based on the above data, you can see that the URL length in the get method is no more than 2083 characters, so that all browsers and servers are likely to work properly.

## What happens when you type Google.com into your browser and hit Enter?

1. Parsing URL: Firstly, the URL will be parsed to analyze the required transport protocol and the path of the requested resource. If the protocol or host name in the input URL is illegal, the content entered in the address bar will be passed to the search engine. If there is no problem, the browser will check if there are any illegal characters in the URL. If there are any illegal characters, they will be escaped before proceeding to the next process.

2. Cache judgment: The browser will determine whether the requested resource is in the cache. If the requested resource is in the cache and has not expired, it will be used directly. Otherwise, a new request will be made to the server.

3. DNS resolution: The next step is to obtain the IP address of the domain name in the input URL. Firstly, it will check whether there is a cache of the IP address of the domain name locally. If there is, use it. If not, make a request to the local DNS server. The local DNS server will also first check for cache presence. If not, it will first make a request to the root domain name server, obtain the address of the responsible top-level domain name server, and then request to the top-level domain name server. After obtaining the address of the responsible authoritative domain name server, it will then make a request to the authoritative domain name server, and finally obtain the IP address of the domain name, The local DNS server will then return this IP address to the requesting user. User requests to local DNS servers are recursive requests, while requests from local DNS servers to domain name servers at all levels are iterative requests.

4. Obtain the MAC address: After the browser obtains the IP address, it also needs to know the MAC address of the destination host for data transmission. This is because the application layer sends data to the transport layer. The TCP protocol specifies the source and destination port numbers, and then sends the data to the network layer. The network layer uses the local address as the source address and the obtained IP address as the destination address. At the data link layer, MAC addresses of both parties must be added to the data link layer. The local MAC address serves as the source MAC address, and the destination MAC address needs to be processed by case. By matching the IP address with the subnet mask of the host, you can determine whether it is in the same subnet as the request host. If it is in the same subnet, you can use the APR protocol to get the MAC address of the destination host. If it is not in the same subnet, then the request should be forwarded to the gateway and forwarded by it. In this case, you can also obtain the MAC address of the gateway through ARP. In this case, the MAC address of the destination host should be that of the gateway.

5. TCP three-way handshake: The following is the process of TCP establishing a connection through a triple handshake. Firstly, the client sends a SYN connection request segment and a random number to the server. After receiving the request, the server sends a SYN ACK segment to the server to confirm the connection request and also sends a random number to the client. After receiving the confirmation response from the server, the client enters the connection establishment state and also sends an ACK confirmation message segment to the server. After receiving the confirmation, the server enters the connection establishment state, and the connection between both parties is established.

6. HTTPS handshake: If using the HTTPS protocol, there is still a four handshake process in TLS before communication. Firstly, the client sends the version number of the protocol used, a random number, and the encryption methods that can be used to the server. After receiving it, the server confirms the encryption method, decrypts the data, and sends a hash value of all previous contents to the client for verification. At this point, both parties have three random numbers. According to the previously agreed encryption method, use these three random numbers to generate a secret key. Before communication between the two parties, use this key to encrypt the data and then transmit it.

7. Return data: When the page request is sent to the server, the server will return an HTML file as a response. After receiving the response, the browser starts parsing the HTML file and begins the page rendering process.

8. Page rendering: The browser will first build a DOM tree based on the HTML file, and then build a CSSOM tree based on the parsed CSS file. If a script tag is encountered, it will determine whether it contains the defer or async attribute, otherwise the loading and execution of the script will cause the rendering of the page to be blocked. After the DOM tree and CSSOM tree are established, build a rendering tree based on them. After the rendering tree is constructed, the layout will be based on the rendering tree. After the layout is completed, use the browser's UI interface to draw the page. At this point, the entire page is displayed.

9. TCP Four Waves: The final step is the four wave process of TCP disconnecting. If the client believes that the data transmission is complete, it needs to send a connection release request to the server. After receiving a connection release request, the server will tell the application layer to release the TCP link. Then it will send an ACK packet and enter CLOSE\_ WAIT status indicates that the connection between the client and the server has been released and no longer receives data sent by the client. However, because TCP connections are bidirectional, the server can still send data to the client. If there is still unfinished data to be sent by the server at this time, it will continue to send. After completion, it will send a connection release request to the client, and then the server will enter the LAST-ACK state. After receiving the release request, the client sends a confirmation response to the server, and the client enters the TIME-WAIT state. This state will last for 2 MSL (maximum segment lifetime, which refers to the duration of the message segment in the network, and timeout will be discarded). If there is no resend request from the server within this time period, it will enter the CLOSED state. When the server receives a confirmation response, it also enters the CLOSED state.

## How does HTTP load when there are multiple images on the page?

- Under HTTP 1, the browser has a maximum TCP connection count of 6 for a domain name, so it will request multiple times. It can be solved by deploying multiple domain names. This can increase the number of simultaneous requests and speed up the acquisition of page images.
- Under HTTP 2, many resources can be loaded instantly because it supports multiplexing and can send multiple HTTP requests within a TCP connection.
