0.13.1 (12-31-2014)
--------------------

- Add `aiohttp.web.StreamResponse.started` property #213

- Html escape traceback text in `ServerHttpProtocol.handle_error`

- Mention handler and middlewares in `aiohttp.web.RequestHandler.handle_request`
  on error (#218)


0.13.0 (12-29-2014)
-------------------

- `StreamResponse.charset` converts value to lower-case on assigning.

- Chain exceptions when raise `ClientRequestError`.

- Support custom regexps in route variables #204

- Fixed graceful shutdown, disable keep-alive on connection closing.

- Decode http message with `utf-8` encoding, some servers send headers in utf-8 encoding #207

- Support `aiohtt.web` middlewares #209

- Add ssl_context to TCPConnector #206


0.12.0 (12-12-2014)
-------------------

- Deep refactoring of `aiohttp.web` in backward-incompatible manner.
  Sorry, we have to do this.

- Automatically force aiohttp.web handlers to coroutines in
  `UrlDispatcher.add_route()` #186

- Rename `Request.POST()` function to `Request.post()`

- Added POST attribute

- Response processing refactoring: constructor does't accept Request instance anymore.

- Pass application instance to finish callback

- Exceptions refactoring

- Do not unquote query string in `aiohttp.web.Request`

- Fix concurrent access to payload in `RequestHandle.handle_request()`

- Add access logging to `aiohttp.web`

- Gunicorn worker for `aiohttp.web`

- Removed deprecated `AsyncGunicornWorker`

- Removed deprecated HttpClient


0.11.0 (11-29-2014)
-------------------

- Support named routes in `aiohttp.web.UrlDispatcher` #179

- Make websocket subprotocols conform to spec #181


0.10.2 (11-19-2014)
-------------------

- Don't unquote `environ['PATH_INFO']` in wsgi.py #177


0.10.1 (11-17-2014)
-------------------

- aiohttp.web.HTTPException and descendants now files response body
  with string like `404: NotFound`

- Fix multidict `__iter__`, the method should iterate over keys, not (key, value) pairs.


0.10.0 (11-13-2014)
-------------------

- Add aiohttp.web subpackage for highlevel http server support.

- Add *reason* optional parameter to aiohttp.protocol.Response ctor.

- Fix aiohttp.client bug for sending file without content-type.

- Change error text for connection closed between server responses
  from 'Can not read status line' to explicit 'Connection closed by
  server'

- Drop closed connections from connector #173

- Set server.transport to None on .closing() #172


0.9.3 (10-30-2014)
------------------

- Fix compatibility with asyncio 3.4.1+ #170


0.9.2 (10-16-2014)
------------------

- Improve redirect handling #157

- Send raw files as is #153

- Better websocket support #150


0.9.1 (08-30-2014)
------------------

- Added MultiDict support for client request params and data #114.

- Fixed parameter type for IncompleteRead exception #118.

- Strictly require ASCII headers names and values #137

- Keep port in ProxyConnector #128.

- Python 3.4.1 compatibility #131.


0.9.0 (07-08-2014)
------------------

- Better client basic authentication support #112.

- Fixed incorrect line splitting in HttpRequestParser #97.

- Support StreamReader and DataQueue as request data.

- Client files handling refactoring #20.

- Backward incompatible: Replace DataQueue with StreamReader for request payload #87.


0.8.4 (07-04-2014)
------------------

- Change ProxyConnector authorization parameters.


0.8.3 (07-03-2014)
------------------

- Publish TCPConnector properties: verify_ssl, family, resolve, resolved_hosts.

- Don't parse message body for HEAD responses.

- Refactor client response decoding.


0.8.2 (06-22-2014)
------------------

- Make ProxyConnector.proxy immutable property.

- Make UnixConnector.path immutable property.

- Fix resource leak for aiohttp.request() with implicit connector.

- Rename Connector's reuse_timeout to keepalive_timeout.


0.8.1 (06-18-2014)
------------------

- Use case insensitive multidict for server request/response headers.

- MultiDict.getall() accepts default value.

- Catch server ConnectionError.

- Accept MultiDict (and derived) instances in aiohttp.request header argument.

- Proxy 'CONNECT' support.


0.8.0 (06-06-2014)
------------------

- Add support for utf-8 values in HTTP headers

- Allow to use custom response class instead of HttpResponse

- Use MultiDict for client request headers

- Use MultiDict for server request/response headers

- Store response headers in ClientResponse.headers attribute

- Get rid of timeout parameter in aiohttp.client API

- Exceptions refactoring


0.7.3 (05-20-2014)
------------------

- Simple HTTP proxy support.


0.7.2 (05-14-2014)
------------------

- Get rid of __del__ methods

- Use ResourceWarning instead of logging warning record.


0.7.1 (04-28-2014)
------------------

- Do not unquote client request urls.

- Allow multple waiters on transport drain.

- Do not return client connection to pool in case of exceptions.

- Rename SocketConnector to TCPConnector and UnixSocketConnector to UnixConnector.


0.7.0 (04-16-2014)
------------------

- Connection flow control.

- Http client session/connection pool refactoring.

- Better handling for bad server requests.


0.6.5 (03-29-2014)
------------------

- Added client session reuse timeout.

- Better client request cancellation support.

- Better handling responses without content length.

- Added HttpClient verify_ssl parameter support.


0.6.4 (02-27-2014)
------------------

- Log content-length missing warning only for put and post requests.


0.6.3 (02-27-2014)
------------------

- Better support for server exit.

- Read response body until eof if content-length is not defined #14


0.6.2 (02-18-2014)
------------------

- Fix trailing char in allowed_methods.

- Start slow request timer for first request.


0.6.1 (02-17-2014)
------------------

- Added utility method HttpResponse.read_and_close()

- Added slow request timeout.

- Enable socket SO_KEEPALIVE if available. (@polymorphm)


0.6.0 (02-12-2014)
------------------

- Better handling for process exit.


0.5.0 (01-29-2014)
------------------

- Allow to use custom HttpRequest client class.

- Use gunicorn keepalive setting for async worker.

- Log leaking responses.

- python 3.4 compatibility


0.4.4 (11-15-2013)
------------------

- Resolve only AF_INET family, because it is not clear how to pass extra info to asyncio.


0.4.3 (11-15-2013)
------------------

- Allow to wait completion of request with `HttpResponse.wait_for_close()`


0.4.2 (11-14-2013)
------------------

- Handle exception in client request stream.

- Prevent host resolving for each client request.


0.4.1 (11-12-2013)
------------------

- Added client support for `expect: 100-continue` header.


0.4 (11-06-2013)
----------------

- Added custom wsgi application close procedure

- Fixed concurrent host failure in HttpClient


0.3 (11-04-2013)
----------------

- Added PortMapperWorker

- Added HttpClient

- Added tcp connection timeout to http client

- Better client connection errors handling

- Gracefully handle process exit


0.2
---

- Fix packaging
