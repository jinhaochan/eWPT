# eWPT

## Introduction

### HTML entities

If you use the less than `<` or greater than `>` signs in your text, the browser might mix them with tags.

Character entities are used to display reserved characters in HTML.

Used to dispaly user input in case of XSS

```
<	less than	&lt;	&#60;	
>	greater than	&gt;	&#62;	
&	ampersand	&amp;	&#38;	
"	double quotation mark	&quot;	&#34;
```

### Same Origin Policy

SOP is applied to HTTP requests from one origin to another. It does not affect requests like loading of Javascripts, CSS files or images.

A same origin has the same
- Protocol
- Hostname (excluding pathnames. subdomains are different hostnames)
- Port

Scripts from one origin cannot read data from another origin (Cross-site Read)

Scripts from one origin might be able to write to another origin (Cross-site Write)

A Cross Site Request Forgery (CSRF) token is implemented to combat Cross-site Writes, as the script needs to include the token in the POST request, which is high-entropy enough to be non-guessable

SOP does not stop XSS against the same website, because the origins are the same.

Cross Origin Resource Sharing allows a site to specify resources to share with other sites, circumventing SOP

### Cookies

HttpOnly flag in Cookies forces the browser to send the cookie ONLY through HTTP. This prevents XSS from stealing the cookie via Javascript.

Secure flag forces the cookie to be sent through HTTPS

### Sessions

Cookies are stored on the client side while Sessions are stored on the server

## Information Gathering

### OSINT

Information can be found via:
- WHOIS
- DNS Queries (MX, Zone Transfers, NS)

### Infrastructure

Information can be found via:
- `whatweb`
- Checking page extensions (.js, .php, .html)
- Checking HTTP response (Server)
- Session IDs (PHPSESSID, ASPSESSIONID. JSESSION)

### Subdomain Enumeration

- `ffuf -w wordlist:FUZZ -u http://FUZZ.site.com`
- `ffuf -w wordlist:FUZZ -u http://site.com -H "Host: http://FUZZ.site.com"` vhost scanning
- Sublist3r

### Resource Enumeration

- `ffuf -w wordlist:FUZZ -u http://site.com/FUZZ -e .php,.txt,bak`

