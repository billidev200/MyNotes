---
description: Expression Language Injection
---

# EL Injection

EL Injection and SSTI are closely related, but not exactly the same.

#### &#x20;**EL Injection**

Happens in systems that use **Expression Language**, typically in **Java-based** technologies:

* JSP / JSTL
* Spring
* Struts
* Thymeleaf
* Seam
* JSF

```
${7*7}
```

SSTI (Jinja2 in Python)

```
{{7*7}}
```
