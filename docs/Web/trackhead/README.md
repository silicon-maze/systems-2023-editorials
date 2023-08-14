# **TrackHead**

Category: Web

Author: Utkar5hM

Answer / Flag: `MAZE{TRAC3DTH3F0RC3WITHHE4DERS}`

## Problem Statement

Help Baby yoda balance the force.


## Solution

sending a curl request to the endpoint:
```sh
curl http://127.0.0.1:3000/
Found. Redirecting to /NeverEver
```
we Notice, we get redirected to /NeverEver.

trying to visit /NeverEver. We get the text `You will need to balance the force. Try tracing the path of it.` and a Yoda's image with RFC and 2616 as texts.

Searching for RFC2616 will lead the user to the RFC of HTTP protocol where various requests types have been defined.

The text hints us about tracing of the path. so first thing we can do is make a curl request again at `/` with higher verbosity.
```sh
curl http://127.0.0.1:3000/ -v
* processing: http://127.0.0.1:3000/
*   Trying 127.0.0.1:3000...
* Connected to 127.0.0.1 (127.0.0.1) port 3000
> GET / HTTP/1.1
> Host: 127.0.0.1:3000
> User-Agent: curl/8.2.1
> Accept: */*
> 
< HTTP/1.1 302 Found
< X-Powered-By: Express
< Light: 8201
< Balance: M0LcoTq0uZE2GWKrqnx+z4sbKEI=
< Location: /NeverEver
< Vary: Accept
< Content-Type: text/plain; charset=utf-8
< Content-Length: 32
< Date: Wed, 09 Aug 2023 18:43:22 GMT
< Connection: keep-alive
< Keep-Alive: timeout=5
< 
* Connection #0 to host 127.0.0.1 left intact
```

We can see two interesting headers,  Balance and Light. Both of them seem to change everytime I make a request.

Let's try to send the Balance back as a header.
```sh
curl http://127.0.0.1:3000/ -v -H 'balance: M0LcoTq0uZE2GWKrqnx+z4sbKEI='
* processing: http://127.0.0.1:3000/
*   Trying 127.0.0.1:3000...
* Connected to 127.0.0.1 (127.0.0.1) port 3000
> GET / HTTP/1.1
> Host: 127.0.0.1:3000
> User-Agent: curl/8.2.1
> Accept: */*
> balance: M0LcoTq0uZE2GWKrqnx+z4sbKEI=
> 
< HTTP/1.1 200 OK
< X-Powered-By: Express
< Content-Type: text/html; charset=utf-8
< Content-Length: 37
< ETag: W/"25-5ILxh+dr7iU0O70ee2dgi6FdQlQ"
< Date: Wed, 09 Aug 2023 18:45:16 GMT
< Connection: keep-alive
< Keep-Alive: timeout=5
< 
* Connection #0 to host 127.0.0.1 left intact
I find your lack of faith disturbing.[user@g14arch Systems-2023]$ 

```

we don't get redirected but get a different output but this again tells us we might've missed something.

Lets try sending DARK header with value same as respective light along with balance header. as we're trying to balance of something.

```sh
curl http://127.0.0.1:3000/ -v -H 'Balance: kcuLTJN3J/40/iKaRPp01o7mtyM=' -H 'DARK: 4466'
* processing: http://127.0.0.1:3000/
*   Trying 127.0.0.1:3000...
* Connected to 127.0.0.1 (127.0.0.1) port 3000
> GET / HTTP/1.1
> Host: 127.0.0.1:3000
> User-Agent: curl/8.2.1
> Accept: */*
> Balance: kcuLTJN3J/40/iKaRPp01o7mtyM=
> DARK: 4466
> 
< HTTP/1.1 200 OK
< X-Powered-By: Express
< Content-Type: text/html; charset=utf-8
< Content-Length: 37
< ETag: W/"25-5ILxh+dr7iU0O70ee2dgi6FdQlQ"
< Date: Wed, 09 Aug 2023 18:49:59 GMT
< Connection: keep-alive
< Keep-Alive: timeout=5
< 
* Connection #0 to host 127.0.0.1 left intact
I find your lack of faith disturbing.
```

There's no difference in the output.

There is a TRACE request method mentioned under RFC2616 which is often used for diagnosing. This usually helps us see the request which is exactly been received by the server. Helps in case if the server owner is using any proxy in between.

Sending a trace request.
```sh
curl http://127.0.0.1:3000/ -v -X TRACE
* processing: http://127.0.0.1:3000/
*   Trying 127.0.0.1:3000...
* Connected to 127.0.0.1 (127.0.0.1) port 3000
> TRACE / HTTP/1.1
> Host: 127.0.0.1:3000
> User-Agent: curl/8.2.1
> Accept: */*
> 
< HTTP/1.1 200 OK
< X-Powered-By: Express
< d4rk: Don't Miss me :p
< Content-Type: text/html; charset=utf-8
< Content-Length: 86
< ETag: W/"56-lZrfKLXpo2lOIX85K1V/gtDYji4"
< Date: Wed, 09 Aug 2023 18:47:54 GMT
< Connection: keep-alive
< Keep-Alive: timeout=5
< 
Some people say d4rk can be balanced with light.

  "Rebellions are built on hope."
* Connection #0 to host 127.0.0.1 left intact
```

It hints us with d4rk header and as well as with text.

Trying to send the request:
```sh
curl http://127.0.0.1:3000/ -v -H 'Balance: kcuLTJN3J/40/iKaRPp01o7mtyM=' -H 'd4rk: 4466'
* processing: http://127.0.0.1:3000/
*   Trying 127.0.0.1:3000...
* Connected to 127.0.0.1 (127.0.0.1) port 3000
> GET / HTTP/1.1
> Host: 127.0.0.1:3000
> User-Agent: curl/8.2.1
> Accept: */*
> Balance: kcuLTJN3J/40/iKaRPp01o7mtyM=
> d4rk: 4466
> 
< HTTP/1.1 200 OK
< X-Powered-By: Express
< Content-Type: text/html; charset=utf-8
< Content-Length: 31
< ETag: W/"1f-I1gzt/o2hkYmamxafLeIP407/J8"
< Date: Wed, 09 Aug 2023 18:53:42 GMT
< Connection: keep-alive
< Keep-Alive: timeout=5
< 
* Connection #0 to host 127.0.0.1 left intact
MAZE{TRAC3DTH3F0RC3WITHHE4DERS}
```

We get the flag. :) 