//Full status code
HTTP/1.1 200 OK

// Headers
 "headers": {
    "Accept": "*/*",
    "Host": "httpbin.org",
    "User-Agent": "curl/8.15.0",
    "X-Amzn-Trace-Id": "Root=1-695d88b5-49b5dbcf5a69f0d651356f52"
  },

//Body
{
  "args": {},
  "headers": {
    "Accept": "*/*",
    "Host": "httpbin.org",
    "User-Agent": "curl/8.15.0",
    "X-Amzn-Trace-Id": "Root=1-695d88b5-49b5dbcf5a69f0d651356f52"
  },
  "origin": "102.253.97.13",
  "url": "https://httpbin.org/get"
}

//What does -i do?
It includes the headers and other information in the response because curl does not include

// Why is the status code not part of the body?
Status code tells us if were were able to reach the endpoint and the body is the actual response from the request

//Why does HTTP separate headers and body?
hearder serves as a guide or protocol to vieve the file