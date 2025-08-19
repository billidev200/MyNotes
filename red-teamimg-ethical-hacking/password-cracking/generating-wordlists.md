# Generating Wordlists

## &#x20;Crunch

## &#x20;CeWL

| **Tool**   | **Purpose**                                                            | **Basic Command**                        | **Example Use Case**                                                                 |
| ---------- | ---------------------------------------------------------------------- | ---------------------------------------- | ------------------------------------------------------------------------------------ |
| **Crunch** | Generates wordlists from scratch using character sets or patterns.     | `crunch <min> <max> [charset] -o <file>` | `crunch 5 5 -t THM@% -o tryhackme.txt` → Generates words like `THMa0`, `THMb9`, etc. |
| **CeWL**   | Crawls a website and extracts unique words to build a custom wordlist. | `cewl [options] <URL> -w <file>`         | `cewl -d 2 http://example.com -w sitewords.txt` → Scrapes up to depth 2 for words.   |

🔑 **Quick Recap of Placeholders in Crunch (`-t` flag):**

* `@` → lowercase letter (a-z)
* `,` → uppercase letter (A-Z)
* `%` → number (0-9)
* `^` → special character
