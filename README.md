# Apache-A-score-htaccess

Apache server configuration file .htaccess with __A+ score__ in security on [Security Report](https://securityheaders.com).

## What does this file include?

- Safety Headers that guarantee your website a score __A+__ in a Security Report Summary
- General protection (to extend)
- Smart links
- Redirection to https
- Turned off indexing

All explained bellow.

### Example

Following example is a generated report from a website with a proper .htacces:

[securityheaders.com/bambit.com.pl](https://securityheaders.com/?q=bambit.com.pl&followRedirects=on)

## General

| Rule | Description |
|:----------------------------------------------------------------------:|:---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
| Options -Indexes | Enabled by default: Users can browse inside directory that doesn't have a index file (.html, .php, etc.). Turning it off, prevents from listing files of directories. |
| RewriteEngine On | Turns rewrite engine on - enable to write your own rules. |
| RewriteCond %{REQUEST_FILENAME} !-d | Rule condition 1, requested URL is not a directory |
| RewriteCond %{REQUEST_FILENAME} !-f | Rule condition 2, requested URL is not a file |
| RewriteRule ^([^\.]+)$ $1.html [NC,L] | If both conditions are passed (1 & 2), "Smart link" works. Request to bambit.com.pl/[name] will be identical to bambit.com.pl/[name.html]. <BR>Both URLs works, but user has not to enter full URL. |
| RewriteCond %{HTTPS} off [OR]<br> RewriteCond %{HTTP_HOST} ^www\. [NC] | Automatically redirects request to HTTPS. E.g. URL http://bambit.com.pl, will be changed to https://bambit.com.pl. |
| RewriteRule ^ https://bambit.com.pl/%{REQUEST_URI} [L,NE,R=301] | Domain prefix 'www' will be remove. E.g. URL https://www.bambit.com.pl will be changed to https://bambit.com.pl |

## Safety

| __Header name__                    | Description                                                                                                                                                                                                                                                                                                                                             |
|-----------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| __Content-Security-Policy__       | Content Security Policy is an effective measure to protect your site from XSS attacks. By whitelisting sources of approved content, you can prevent the browser from loading malicious assets. Analyse this policy in more detail. You can sign up for a free account on Report URI to collect reports about problems on your site. |
| __X-Content-Type-Options__        | X-Content-Type-Options stops a browser from trying to MIME-sniff the content type and forces it to stick with the declared content-type. The only valid value for this header is "X-Content-Type-Options: nosniff".                                                                                                                                |
| __Set-Cookie__                    | This header is used to configure cookies. The `HttpOnly` flag prevents access via JavaScript, and the `Secure` flag ensures the cookie is only sent over HTTPS connections.                                                                                                                                                                          |
| __X-FRAME-OPTIONS__               | X-Frame-Options tells the browser whether you want to allow your site to be framed or not. By preventing a browser from framing your site you can defend against attacks like clickjacking.                                                                                                                                                         |
| __X-XSS-Protection__              | X-XSS-Protection sets the configuration for the XSS Auditor built into older browsers. The recommended value was "X-XSS-Protection: 1; mode=block", but modern best practices now recommend relying on Content Security Policy instead.                                                                                                             |
| __Strict-Transport-Security__     | HTTP Strict Transport Security is an excellent feature to support on your site and strengthens your implementation of TLS by getting the User Agent to enforce the use of HTTPS. Example: `max-age=63072000; includeSubDomains; preload` enforces it for two years and allows preload list eligibility.                                             |
| __Referrer-Policy__              | Referrer Policy is a header that allows a site to control how much information the browser includes with navigations away from a document. A strict policy like `no-referrer` provides maximum privacy.                                                                                                                                            |
| __Permissions-Policy__           | Permissions Policy allows a site to control which features and APIs can be used in the browser. Example: `microphone=(), camera=(), payment=(), geolocation=(self)` disables all features except geolocation for the same origin.                                                                                                                    |
| __Cross-Origin-Opener-Policy__   | Helps prevent cross-origin attacks like Spectre by isolating browsing contexts. Recommended value: `same-origin` to ensure documents are fully isolated.                                                                                                                                                                                              |
| __Cross-Origin-Resource-Policy__ | Controls which origins can load resources. A value of `same-origin` ensures that only documents from the same origin can access the resource, improving privacy and security.                                                                                                                                                                         |


Information taken from https://securityheaders.com.

## Score A+

The delivered file achieves only A score. Hence, how to score A+, the highest possible mark?<br>
In my given example, we allow almost everything to happen in our website.<br><br>
To score A+ you need to directly allow specific files.
In report [Link](https://securityheaders.com/?q=bambit.com.pl&followRedirects=on) you can see how it should look.
The 'sha256-abc' is the answers. After turning the off, you will see them automatically generated in your console.
