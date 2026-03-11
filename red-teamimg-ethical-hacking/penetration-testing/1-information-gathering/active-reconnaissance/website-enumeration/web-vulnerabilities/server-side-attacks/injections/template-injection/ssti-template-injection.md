---
description: Server-Side Template Injection
---

# SSTI Template Injection

<figure><img src="../../../../../../../../../.gitbook/assets/645b19f5d5848d004ab9c9e2-1717984475799.png" alt=""><figcaption></figcaption></figure>

Server-Side Template Injection (SSTI) is a vulnerability that occurs when user input is unsafely incorporated into a server-side template, allowing attackers to inject and execute arbitrary code on the server.&#x20;

Template engines are commonly used in web applications to generate dynamic HTML by combining fixed templates with dynamic data. When these engines process user input without proper sanitization, they become susceptible to SSTI attacks.

**Core Concepts of SSTI**

* **Dynamic Content Generation:** Template engines replace placeholders with actual dat&#x61;**,** allowing applications to generate dynamic HTML pages. This process can be exploited if user inputs are not properly sanitized.
* **User Input as Template Code:** When user inputs are treated as part of the template code, they can introduce harmful logic into the rendered output, leading to SSTI.

{% hint style="info" %}
**W look were tamplates are used. Example is a post commnets were user gives input**

![](<../../../../../../../../../.gitbook/assets/image (23).png>)
{% endhint %}

{% embed url="https://www.youtube.com/watch?t=126s&v=SN6EVIG4c-0" %}

## Template Engines

* **Jinja2**: Highly popular in Python applications, known for its expressiveness and powerful rendering capabilities.
* **Twig**: The default template engine for Symfony in PHP, Twig offers a robust environment with secure default settings.
* **Pug/Jade**: Known for its minimal and clean HTML templating syntax, Pug/Jade is popular among Node.js developers.

**Each tamplate engine has diffrent syntax**

**Function verie from each engine. For example in python engine we will use python code**

| Template Engine                | Variable Syntax   | Logic / Control Syntax                        | Comment Syntax      | Notes                                                                    |
| ------------------------------ | ----------------- | --------------------------------------------- | ------------------- | ------------------------------------------------------------------------ |
| **Jinja2 (Python)**            | `{{ variable }}`  | `{% if x %} ... {% endif %}`                  | `{# comment #}`     | Flask, Ansible use this. Very powerful.                                  |
| **Django Template Engine**     | `{{ variable }}`  | `{% for x in list %} ... {% endfor %}`        | `{# comment #}`     | More restricted than Jinja2.                                             |
| **Twig (PHP)**                 | `{{ var }}`       | `{% if cond %} ... {% endif %}`               | `{# comment #}`     | Symfony. Similar to Jinja2.                                              |
| **Laravel Blade (PHP)**        | `{{ $var }}`      | `@if ... @endif` / `@foreach ... @endforeach` | `{{-- comment --}}` | Blade also supports safe raw output `{!! !!}` but avoid with user input. |
| **Mustache / Handlebars (JS)** | `{{name}}`        | `{{#if cond}} ... {{/if}}`                    | `{{! comment }}`    | Logicless (no code execution).                                           |
| **EJS (Node.js)**              | `<%= variable %>` | `<% if () { %> ... <% } %>`                   | `<%# comment %>`    | Embeds raw JS.                                                           |
| **ERB (Ruby)**                 | `<%= var %>`      | `<% if cond %> ... <% end %>`                 | `<%# comment %>`    | Rails views.                                                             |
| **Velocity (Java)**            | `$var`            | `#if($cond) ... #end`                         | `## comment`        | Java template engine.                                                    |
| **Freemarker (Java)**          | `${var}`          | `<#if cond> ... </#if>`                       | `<#-- comment -->`  | Used in Java web apps.                                                   |
| **Thymeleaf (Java)**           | `${var}`          | HTML attributes: `th:if`, `th:each`           | `/* comment */`     | Inline inside HTML templates.                                            |
| **Smarty (PHP)**               | `{$var}`          | `{if $x} ... {/if}`                           | `{\* comment *\}`   | Older PHP engine.                                                        |
| **Razor (ASP.NET)**            | `@var`            | `@if () { }` / `@foreach`                     | `@* comment *@`     | Used in ASP.NET MVC.                                                     |
| **NodeJS - Pug**               | `#{7*7}`          |                                               |                     |                                                                          |

## Mitigation

#### Sandboxing in Template Engines

Sandboxing is a security feature that restricts the execution of potentially harmful code within templates. It limits the actions that templates can perform, such as file operations or system command execution. Proper sandboxing helps prevent security issues like SSTI.

Importance of Sandboxing

* Function Restrictions: Limits the functions or methods that can be called from within the template, blocking potentially harmful operations.
* Variable and Data Access: Controls access to global variables or sensitive data, ensuring templates cannot manipulate or expose critical information.

**Mitigation**

* **Input Sanitization**: Always sanitize inputs to escape or remove potentially dangerous characters and strings that can be interpreted as code. This is crucial when inputs are directly used in template expressions.
* **Template Auditing**: Regularly review and audit templates for insecure coding patterns, such as directly embedding user input without sanitization.

## Automating the Exploitation

```
           
user@tryhackme $ python3 sstimap.py -X POST -u 'http://ssti.thm:8002/mako/' -d 'page='           

    ╔══════╦══════╦═══════╗ ▀█▀
    ║ ╔════╣ ╔════╩══╗ ╔══╝═╗▀╔═
    ║ ╚════╣ ╚════╗  ║ ║    ║{║  _ __ ___   __ _ _ __
    ╚════╗ ╠════╗ ║  ║ ║    ║*║ | '_ ` _ \ / _` | '_ \
    ╔════╝ ╠════╝ ║  ║ ║    ║}║ | | | | | | (_| | |_) |
    ╚══════╩══════╝  ╚═╝    ╚╦╝ |_| |_| |_|\__,_| .__/
                             │                  | |
                                                |_|
[*] Version: 1.2.1
[*] Author: @vladko312
[*] Based on Tplmap
[!] LEGAL DISCLAIMER: Usage of SSTImap for attacking targets without prior mutual consent is illegal.
It is the end user's responsibility to obey all applicable local, state and federal laws.
Developers assume no liability and are not responsible for any misuse or damage caused by this program
[*] Loaded plugins by categories: languages: 5; generic: 3; engines: 17; legacy_engines: 2
[*] Loaded request body types: 4

[*] Scanning url: http://ssti.thm:8002/mako/
[*] Testing if Body parameter 'page' is injectable
[*] Mako plugin is testing rendering with tag '*'
[+] Mako plugin has confirmed injection with tag '*'
[+] SSTImap identified the following injection point:

  Body parameter: page
  Engine: Mako
  Injection: *
  Context: text
  OS: posix-linux
  Technique: render
  Capabilities:

    Shell command execution: ok
    Bind and reverse shell: ok
    File write: ok
    File read: ok
    Code evaluation: ok, python code
```

{% embed url="https://github.com/vladko312/SSTImap" %}

## Example

<figure><img src="../../../../../../../../../.gitbook/assets/Screenshot 2025-12-05 202334.png" alt=""><figcaption></figcaption></figure>

<figure><img src="../../../../../../../../../.gitbook/assets/Screenshot 2025-12-05 202613.png" alt=""><figcaption></figcaption></figure>
