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

Following example is a generated report from a website with a proper .htacces:<br>
[securityheaders.com/bambit](https://securityheaders.com/?q=bambit.com.pl&followRedirects=on)

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

| __Header name__ | Description |
|---------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| __Content-Security-Policy__ | Content Security Policy is an effective measure to protect your site from XSS attacks. By whitelisting sources of approved content, you can prevent the browser from loading malicious assets. Analyse this policy in more detail. You can sign up for a free account on Report URI to collect reports about problems on your site. |
| __X-Content-Type-Options__ | X-Content-Type-Options stops a browser from trying to MIME-sniff the content type and forces it to stick with the declared content-type. The only valid value for this header is "X-Content-Type-Options: nosniff". |
| __X-FRAME-OPTIONS__ | X-Frame-Options tells the browser whether you want to allow your site to be framed or not. By preventing a browser from framing your site you can defend against attacks like clickjacking. |
| __X-XSS-Protection__ | X-XSS-Protection sets the configuration for the XSS Auditor built into older browser. The recommended value was "X-XSS-Protection: 1; mode=block" but you should now look at Content Security Policy instead. |
| __Strict-Transport-Security__ | HTTP Strict Transport Security is an excellent feature to support on your site and strengthens your implementation of TLS by getting the User Agent to enforce the use of HTTPS. |
| __Referrer-Policy__ | 	Referrer Policy is a new header that allows a site to control how much information the browser includes with navigations away from a document and should be set by all sites. |
| __Permissions-Policy__ | Permissions Policy is a new header that allows a site to control which features and APIs can be used in the browser. |


Information taken from https://securityheaders.com.

## Score A+

The delivered file achieves only A score. Hence, how to score A+, the highest possible mark?<br>
In my given example, we allow almost everything to happen in our website.<br><br>
To score A+ you need to directly allow specific files.
In report [Link](https://securityheaders.com/?q=bambit.com.pl&followRedirects=on) you can see how it should look.
The 'sha256-abc' is the answers. After turning the off, you will see them automatically generated in your console.
