micro-http
==========
µHTTP is an overly simplified protocol for HTTP

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
