# Apache-A-score-htaccess
Apache server configuration file .htaccess with __A+ score__ in security on [Security Report](securityheaders.com).

# What does this file include?
- Safety Headers that guarantee your website a score __A+__ in a Security Report Summary
- General protection (to extend)
- Smart links
- Redirection to https
- Turned off indexing 

All explained bellow.

# Example
Following example is a generated report from a website with a proper .htacces:<br>
[securityheaders.com/bambit](https://securityheaders.com/?q=bambit.com.pl&followRedirects=on)

# General
| Rule | Description |
|-----------------------------------------------------------------|-------------|
| Options -Indexes | Defaultly enabled: Users can browse inside directory that doesn't have a index file (.html, .php, etc.). Turning it off, prevents from listing files of directories. |
| RewriteEngine On |  |
| RewriteCond %{REQUEST_FILENAME} !-d |  |
| RewriteCond %{REQUEST_FILENAME} !-f |  |
| RewriteRule ^([^\.]+)$ $1.html [NC,L] |  |
| RewriteCond %{HTTPS} off [OR] |  |
| RewriteCond %{HTTP_HOST} ^www\. [NC] |  |
| RewriteRule ^ https://bambit.com.pl/%{REQUEST_URI} [L,NE,R=301] |  |

# Safety
| __Header name__ | Description |
|---------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| __Content-Security-Policy__ | Content Security Policy is an effective measure to protect your site from XSS attacks. By whitelisting sources of approved content, you can prevent the browser from loading malicious assets. Analyse this policy in more detail. You can sign up for a free account on Report URI to collect reports about problems on your site. |
| __X-Content-Type-Options__ |  |
| __X-FRAME-OPTIONS__ |  |
| __X-XSS-Protection__ |  |
| __Strict-Transport-Security__ |  |
| __Referrer-Policy__ |  |
| __Feature-Policy__ |  |
<br>
Information taken from https://securityheaders.com.

# Score A+
The delivered file achieves only A score. Hence, how to score A+, the highest possible mark?<br>
The 'Content-Security-Policy' should be a field of your intrest. 
In my given example, we allow almost everything to happen in our website.<br><br>
To score A+ you need to directly allow specific files.
In report [Link](https://securityheaders.com/?q=bambit.com.pl&followRedirects=on) you can see how it should look.
The 'sha256-abc' is the answers. After turning the off, you will see them automatically generated in your console.
