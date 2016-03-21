---
layout: post
title: Curl Notes
tags: Curl
category: General
---

#### About ####

curl is a tool to transfer data from or to a server, using one of the supported protocols (DICT, FILE, FTP, FTPS, GOPHER, HTTP, HTTPS, IMAP, IMAPS, LDAP, LDAPS, POP3, POP3S, RTMP, RTSP, SCP, SFTP, SMTP, SMTPS, TELNET and TFTP). The command is designed to work without user interaction.

[more info](http://curl.haxx.se/docs/manpage.html)

#### Examples ####

Perform a HTTP Put

~~~
curl -v -X PUT http://localhost:8092/riak/favs/db \
	-H "Content-type: text/html" \
	-d "<html><body><h1>My new favorite DB is Riak</h1></body></html>"
~~~

Peform a HTTP Put from file where @example.json is the file - use anyfile provided it has @ infront of it  

~~~
curl -X PUT \
     -H 'Content-Type: application/json' \
     -d @example.json
     echo.httpkit.com
~~~

[more examples](http://www.thegeekstuff.com/2012/04/curl-examples/)
[9 uses for cURL worth knowing](http://httpkit.com/resources/HTTP-from-the-Command-Line/)
