micro-http
==========

µHTTP is an overly simplified protocol for HTTP

Grammar
-------
µHTTP is defined using [extended BNF grammer](http://en.wikipedia.org/wiki/Extended_Backus%E2%80%93Naur_Form).
```ebnf
<key>     :==
<value>   :==
<dict>    :== <key>: <value> {, <dict>}
<method>  :== g | p | p | d
<ip>      :== 
<domain>  :==
<host>    :== <ip> | <domain> : <port>
<uri>     :== /
<headers> :== % <dict>
<query>   :== ? <dict>
<body>    :== & <value>
<request> :== <method> <host>/<uri> [ <headers> ] [ <query> ] [ <body> ]
```

Examples
--------
