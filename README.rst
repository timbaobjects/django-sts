Django STS
==========

Strict Transport Security is a mechanism that enables a web server or
web application to tell supporting browsers to always use HTTPS when 
communicating with them.

Most users or web browsers tend to always visit the HTTP version of 
a website before being redirected by the website to the HTTPS version. 
This could leave the user vulnerable to man-in-the-middle attacks 
like phishing or session hijacking involving a compromised router. 

By explicitly telling browsers to always contact a given server over 
HTTPS, such clever attacks can be limited.

For more information, please visit http://tools.ietf.org/html/draft-hodges-strict-transport-sec-02 and http://dev.chromium.org/sts

This middleware is built to automatically include the STS headers in 
outgoing responses from a django-based web application.

To enable this middleware, simply include it in you MIDDLEWARE_CLASSES 
setting in the project settings after the standard middleware:

	MIDDLEWARE_CLASSES = (
		...
		'django-sts.STSMiddleware',
		...
	)

The following parameters in your settings file can be used to change 
the values sent out in the headers.

**STS_MAXAGE**: Which specifies the maximum duration the browser is allowed 
to cache the setting to always use HTTPS for this web app. The value is 
specified in number of seconds.

Example:
	STS_MAXAGE = 60 * 60 * 24 * 30 # specifies a maximum age of 30 days

**STS_INCLUDESUBDOMAINS**: This setting specifies whether the feature also 
applies to subdomains under this domain. The value is boolean

Example:
	STS_INCLUDESUBDOMAINS = True
