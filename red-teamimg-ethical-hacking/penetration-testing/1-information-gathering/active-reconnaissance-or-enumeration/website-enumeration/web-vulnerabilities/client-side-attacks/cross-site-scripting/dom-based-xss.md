# DOM-based XSS

**What is the DOM?**

DOM stands for Document Object Model and is a programming interface for HTML and XML documents. It represents the page so that programs can change the document structure, style and content. A web page is a document, and this document can be either displayed in the browser window or as the HTML source. A diagram of the HTML DOM is displayed below:

<figure><img src="../../../../../../../../.gitbook/assets/24a54ac532b5820bf0ffdddf00ab2247.png" alt=""><figcaption></figcaption></figure>

**Exploiting the DOM**

DOM Based XSS is where the JavaScript execution happens directly in the browser without any new pages being loaded or data submitted to backend code. Execution occurs when the website JavaScript code acts on input or user interaction.

**Example Scenario:**\
The website's JavaScript gets the contents from the `window.location.hash` parameter and then writes that onto the page in the currently being viewed section. The contents of the hash aren't checked for malicious code, allowing an attacker to inject JavaScript of their choosing onto the webpage.

**How to test for Dom Based XSS:**

```
https://realwebsite.com#<img src=1 onerror=alert(1)></img>
```
