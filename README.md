micro-http
==========
µHTTP is an overly simplified protocol for HTTP

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
```bnf
key      =
value    = 
dict     = <key>, ':', <value>, { ',', <dict> }
method   = 'g' | 'p' | 'p' | 'd'
ip       = 
domain   = { domain, '.' }, [a-Z0-9] 
host     = ip | domain, ':', port
uri      = /
headers  = '%', dict
query    = '?', dict
body     = '&', value
status   = 'ok' | 'not found' | ...
request  = method, host, '/', uri, [ headers ], [ query ], [ body ]
response = status, ': ', body
```

Examples
--------
Get latest [reddit](http://reddit.com) frontpage posts

  g www.reddit.com
  
Search through reddit

  g www.reddit.com/search ? q: search terms, sort: relevance, t: all 
  
Same request, compressed

  g www.reddit.com/search?q:search terms,sort:relevance,t:all
