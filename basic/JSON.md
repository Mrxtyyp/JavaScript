## Understanding of JSON

JSON is a text-based lightweight data exchange format. It can be read by any programming language and transmitted as a data format.

In project development, use JSON as a way to exchange front-end and back-end data. In the front-end, a JSON formatted data structure is serialized into a JSON string, which is then passed to the back-end. The back-end parses the JSON formatted string to generate the corresponding data structure, thereby achieving the transfer of front-end and back-end data.

Because JSON syntax is based on js, it is easy to confuse objects in JSON and js. However, it should be noted that objects in JSON and js are not the same, and the format of objects in JSON is more strict. For example, attribute values such as NaN cannot be functions in JSON, so most js objects do not conform to the format of JSON objects.

Two functions are provided in js to convert js data structure and JSON format:

- converts a JSON-formatted data structure into a JSON string. If the input data structure does not conform to the JSON format, these values will be specially processed during serialization to make them conform to the specifications. When the front end sends data to the back end, you can call this function to convert the data object into a JSON string.

- converts a JSON-formatted string into a js data structure. If the input string is not a standard JSON-formatted string, an error is thrown. When a JSON string is received from the backend, you can use this method to parse it into a js data structure for data access.
