//Status line vs status code


Status line = protocol version + status code + reason phrase
Status code = numeric result of request processing

// rESPONSE HEADERS
Response headers contain metadata that tells the client and intermediaries how to interpret, cache, authenticate, or process the response body.

//Request headers vs response headers
Request headers carry information about the client and type of data

Response headers provide information about the response, how to handle the payload 

//response headers from curl output
Date: Wed, 07 Jan 2026 22:15:38 GMT
Content-Type: application/json
Content-Length: 254
Connection: keep-alive
Server: gunicorn/19.9.0
Access-Control-Allow-Origin: *
Access-Control-Allow-Credentials: true


//Explain why httpbin returns headers inside the body
its primary purpose is to act as an "echo server" for testing and debugging HTTP clients

// Why headers/body separation exists
To distinguish metadata from the actual content
Servers use headers like Authorization or Host to decide if a user has permission to access data before even processing the body, saving resources.
A blank line separates headers from the body in HTTP, acting as a clear delimiter so parsers know exactly where instructions end and data begins

# GIT workflow understood
Why is POST not idempotent but PUT is?
POST is not idempotent because each request represents an instruction to create a new resource, and the server assigns identity. Repeating the same POST represents a new creation request each time.
PUT is idempotent because it defines the complete desired state of a known resource. Repeating it results in the same server state regardless of how many times it’s applied.

Why must DELETE be idempotent even if the resource no longer exists?
DELETE must be idempotent because the desired final state is “resource does not exist”. Whether the resource existed before the request or was already deleted, the resulting state is identical.

Why is PATCH dangerous in distributed systems?
PATCH is dangerous in distributed systems because partial updates depend on the current server state. If requests are retried or reordered, applying the same patch multiple times can produce different results, leading to data corruption or lost updates.

Why should GET never return 201 Created?
GET must never return 201 because it is a safe, read-only method. Returning 201 implies a resource was created as a side effect, which violates HTTP semantics, breaks caching, and destroys client assumptions.