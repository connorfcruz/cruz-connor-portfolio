# Ports & Protocols

### Investigating HTTP Status Codes and Redirect Behavior

**Observing an HTTP Redirect**

A redirect was analyzed by using *https://slides.google.com*, which should redirect to *https://docs.google.com/presentation*. To view the HTTP response headers, `curl -I https://slides.google.com` was run:

INSERT OUTPUT AND CIRCLE STATUS CODE/LOCATION

As highlighted above, the HTTP status code 301 was returned. This code signifies that the requested URL has been permanently moved to the URL listed under the *location* field. The Application Layer (Layer 7) of the OSI model is responsible for interpreting this message, since it determines how the application running the curl command should handle the result of the request.

**Investigating the Redirect Target**

Since the listed URL in *location* was *https://docs.google.com/presentation*, the curl command was next used with this URL:

INSERT OUTPUT AND CIRCLE STUFF

At this time, the HTTP status code 302 was returned. A status code of 301 signifies a permanent redirect to a new URL while a status code of 302 signifies a temporary redirect to another URL. A server may temporarily redirect a request if the request cannot be processed fast enough or if there is maintenance in the server. A web browser would respond to a 301 code by automatically redirecting to the *location* field and notifying the user that the URL they attempted to use is deprecated. Meanwhile, a browser would respond to a 302 code by automatically redirecting the user but telling the user to continue using the requested URL.

**Observing Transport Behavior**

`ss -tn` was then used to display the active TCP connections directly after a redirect:

INSERT SS TN

The ESTAB connections confirm that there is still a TCP connection to the remote server when redirecting. Thus, it is confirmed that the Transmission Control Protcol (TCP) carried out the HTTP request. Redirects are handled by HTTP because they only function at the Application layer, while TCP facilitates the actual transfer of redirect requests. TCP only ensures transport reliability and does not act on the Application layer. During this transaction, TLS encryption encrypts both the HTTP request and response during a redirect, ensuring that the request data is secured.

**Reasoning About Server Behavior**

A server does not simply send the new page content automatically because the application first needs to receive the new location URL in place of the incorrect URL used in the request. This is received via HTTP request redirect messages. The server instructs the client to make a new request since the server requires a request from the client to actually display a page's content. This provides the advantage of performing maintenance on a website's main URL while still keeping the website functional through the redirected URL. This can also help if a particular server is down, providing an alternate server to access the same service.