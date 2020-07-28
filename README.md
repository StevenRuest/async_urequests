# async_urequests

asynchronous urequests for micropython. optional urequests class to make usable synchronously.

Tested on ESP32 only with esp32-idf3-20200725-unstable-v1.12-657-g37e1b5c89.bin

Requires uasyncio V3.

Notes:
- to import synchronously (normal) :

  from uasync_urequests import urequests as requests
  
- to import asynchronously: 

  import uasync_urequests as requests
  
- Default HTTP version is 1.0, to change HTTP version do: 

  requests.HTTP__version__ = "1.1"
  
- supported HTTP methods: GET, HEAD, POST, PUT, DELETE.
- Returns response with the following properties: content, status_code, reason, url, text, headers, encoder.
- json from response by gett .json().
- supports headers
- supports params
- supports HTTP & HTTPS.
- supports Chunked data.
- supports redirects: 

  r = requests.get("http://www.yahoo.ca")
  
  r.url ; will return 'https://ca.yahoo.com/'
  
- supports timeout, default timeout set to 10 seconds.
- Raises ConnectionError on any socket errors and TimeoutError on timeouts. To catch errors: requests.ConnectionError & requests.TimeoutError.

Known Issues:
- "memory allocation failed" occurs when reading large responses, will raise a ConnectionError.
