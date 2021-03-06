micro-http
==========

µHTTP is an overly simplified interface for HTTP

µHTTP is designed for human with the idea that a good standard for expressing
HTTP request is essential when you do not have access to high-level tools like a 
full-featured web browser. The goals this standard has to focus on are:

* to use a minimum of characters
* to be easy to remember for a human
* to provide an extensible syntax
* to abstract the complexity of underlied protocol
* to be independant of the protocol version

The grammar is still under deep reflexion.


Grammar
-------
µHTTP is defined using [extended BNF grammer](http://en.wikipedia.org/wiki/Extended_Backus%E2%80%93Naur_Form).
```ebnf
key      = ;
value    = ;
dict     = key, ':', value, { ',', dict };
method   = 'g' | 'p' | 'p' | 'd';
ip       = ; (* see ip specification for ipv4 and ipv6 *)
domain   = { domain, '.' }, [a-Z0-9]; (* domain and subdomain *)
host     = ip | domain, ':', port;
uri      = ; (* see uri specifications *)
headers  = '%', dict;
query    = '?', dict;
body     = '&', value;
status   = 'ok' | 'not found' | '';
request  = method, host, '/', uri, [ headers ], [ query ], [ body ];
response = status, ': ', body;
```


Examples
--------

Get latest [reddit](http://reddit.com) frontpage posts

```
g www.reddit.com
```

Search through reddit (66 characters)

```
g www.reddit.com/search ? q: search terms, sort: relevance, t: all 
```

Same request, compressed (59 characters)

```
g www.reddit.com/search?q:search terms,sort:relevance,t:all
```

Same request, using HTTP/1.1 (73 characters including the CRLF end of line)

```http
GET www.reddit.com/search?q=search%2terms&sort=relevance&t=all HTTP/1.1
```
