# model-A-score-htaccess
A model '.htacces' file with score A on Security Report (from securityheaders.com)

# What does this file include?
- Safety Headers that guarantee your website a score A in a Security Report Summary
- General protection (to extend)
- Smart links
- Redirection to https
- Turned off indexing 

All explained bellow.

# Example
Following example is a generated report from a website with a proper .htacces:<br>
https://securityheaders.com/?q=rondofitness.pl&followRedirects=on

# General
| Rule | Description |
|-----------------------------------------------------------------|-------------|
| Options -Indexes |  |
| RewriteEngine On |  |
| RewriteCond %{REQUEST_FILENAME} !-d |  |
| RewriteCond %{REQUEST_FILENAME} !-f |  |
| RewriteRule ^([^\.]+)$ $1.html [NC,L] |  |
| RewriteCond %{HTTPS} off [OR] |  |
| RewriteCond %{HTTP_HOST} ^www\. [NC] |  |
| RewriteRule ^ https://bambit.com.pl/%{REQUEST_URI} [L,NE,R=301] |  |

# Safety
| Header name | Description |
|---------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Content-Security-Policy | Content Security Policy is an effective measure to protect your site from XSS attacks. By whitelisting sources of approved content, you can prevent the browser from loading malicious assets. Analyse this policy in more detail. You can sign up for a free account on Report URI to collect reports about problems on your site. |
| X-Content-Type-Options |  |
| X-FRAME-OPTIONS |  |
| X-XSS-Protection |  |
| Strict-Transport-Security |  |
| Referrer-Policy |  |
| Feature-Policy |  |
<br>
Information taken from https://securityheaders.com/

# Score A+
The delivered file achieves only A score. Hence, a how to score A+, the highest possible mark?<br>
The 'Content-Security-Policy' should be a field of your intrest. 
In my given example, we allow almost everything to happen in our website.<br><br>
To score A+ you need to directly allow specific files.
In report https://securityheaders.com/?q=bambit.com.pl&followRedirects=on you can see how it should look.
The 'sha256-abc' is the answers. After turning the off, you will see them automatically generated in your console.
