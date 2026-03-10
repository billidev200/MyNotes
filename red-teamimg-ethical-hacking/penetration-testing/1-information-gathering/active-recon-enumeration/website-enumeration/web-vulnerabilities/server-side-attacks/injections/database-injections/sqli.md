# SQLi

<figure><img src="../../../../../../../../../.gitbook/assets/image (22).png" alt=""><figcaption></figcaption></figure>

## Vulnerable Check

First we can check by typing `'` for any errors

## Bypass with comments

Imagine an application that lets users log in with a username and password. If a user submits the username `wiener` and the password `bluecheese`, the application checks the credentials by performing the following SQL query:

`SELECT * FROM users WHERE username = 'wiener' AND password = 'bluecheese'`

If the query returns the details of a user, then the login is successful. Otherwise, it is rejected.

In this case, an attacker can log in as any user without the need for a password. They can do this using the SQL comment sequence `--` to remove the password check from the `WHERE` clause of the query. For example, submitting the username `administrator'--` and a blank password results in the following query:

`SELECT * FROM users WHERE username = 'administrator'--' AND password = ''`

This query returns the user whose `username` is `administrator` and successfully logs the attacker in as that user.

## Boolean bypass

Boolean conditions such as `'OR 1=1` and `'OR 1=2`, and look for differences in the application's responses.

## SQL injection UNION attacks

When an application is vulnerable to SQL injection, and the results of the query are returned within the application's responses, you can use the `UNION` keyword to retrieve data from other tables within the database. This is commonly known as a SQL injection UNION attack.

The `UNION` keyword enables you to execute one or more additional `SELECT` queries and append the results to the original query. For example:

`SELECT a, b FROM table1 UNION SELECT c, d FROM table2`

This SQL query returns a single result set with two columns, containing values from columns `a` and `b` in `table1` and columns `c` and `d` in `table2`.

For a `UNION` query to work, two key requirements must be met:

* The individual queries must return the same number of columns.
* The data types in each column must be compatible between the individual queries.

**To carry out a SQL injection UNION attack, make sure that your attack meets these two requirements. This normally involves finding out:**

* How many columns are being returned from the original query.
* Which columns returned from the original query are of a suitable data type to hold the results from the injected query.

**When you perform a SQL injection UNION attack, there are two effective methods to determine how many columns are being returned from the original query.**

One method involves injecting a series of `ORDER BY` clauses and incrementing the specified column index until an error occurs. For example, if the injection point is a quoted string within the `WHERE` clause of the original query, you would submit:

`' ORDER BY 1-- ' ORDER BY 2-- ' ORDER BY 3-- etc.`

This series of payloads modifies the original query to order the results by different columns in the result set. The column in an `ORDER BY` clause can be specified by its index, so you don't need to know the names of any columns. When the specified column index exceeds the number of actual columns in the result set, the database returns an error, such as:

`The ORDER BY position number 3 is out of range of the number of items in the select list.`

The application might actually return the database error in its HTTP response, but it may also issue a generic error response. In other cases, it may simply return no results at all. Either way, as long as you can detect some difference in the response, you can infer how many columns are being returned from the query.

**The second method involves submitting a series of `UNION SELECT` payloads specifying a different number of null values:**

`' UNION SELECT NULL-- ' UNION SELECT NULL,NULL-- ' UNION SELECT NULL,NULL,NULL-- etc.`

## **Authentication Bypass**

One of the most straightforward Blind SQL Injection techniques is when bypassing authentication methods such as login forms. In this instance, we aren't that interested in retrieving data from the database; We just want to get past the login.&#x20;

## **Time-Based**

A time-based blind SQL injection is very similar to the above boolean-based one in that the same requests are sent, but there is no visual indicator of your queries being wrong or right this time. Instead, your indicator of a correct query is based on the time the query takes to complete. This time delay is introduced using built-in methods such as **SLEEP(x)** alongside the UNION statement. The SLEEP() method will only ever get executed upon a successful UNION SELECT statement.&#x20;

`admin123' UNION SELECT SLEEP(5);--`

`admin123' UNION SELECT SLEEP(5),2;--`

## Best Practices

**Secure Coders**

* **Parameterised Queries and Prepared Statements:** Use parameterised queries and prepared statements to ensure all user inputs are treated as data rather than executable code. This technique helps prevent SQL injection by separating the query structure from the data. For example, in PHP with PDO, you can prepare a statement and bind parameters, which ensures that user inputs are safely handled like `$stmt = $pdo->prepare("SELECT * FROM users WHERE username = :username"); $stmt->execute(['username' => $username]);`.
* **Input Validation and Sanitisation:** Implement strong input validation and sanitization to ensure that inputs conform to expected formats. Validate data types, lengths, and ranges, and reject any input that does not meet these criteria. Use built-in functions such as `htmlspecialchars()` and `filter_var()` in PHP to sanitise inputs effectively.
* **Least Privilege Principle:** Apply the principle of least privilege by granting application accounts the minimum necessary database permissions. Avoid using database accounts with administrative privileges for everyday operations. This minimises the potential impact of a successful SQL injection attack by limiting the attacker's access to critical database functions.
* **Stored Procedures:** Encapsulate and validate SQL logic using stored procedures. This allows you to control and validate the inputs within the database itself, reducing the risk of SQL injection. Ensure that stored procedures accept only validated inputs and are designed to handle input sanitization internally.
* **Regular Security Audits and Code Reviews:** Conduct regular security audits and code reviews to identify and address vulnerabilities. Automated tools can help scan for SQL injection risks, but manual reviews are also essential to catch subtle issues. Regular audits ensure that your security practices stay up-to-date with evolving threats.

**Pentesters**

* **Exploiting Database-Specific Features:** Different database management systems (DBMS) have unique features and syntax. A pentester should understand the specifics of the target DBMS (e.g., MySQL, PostgreSQL, Oracle, MSSQL) to **exploit these features effectively. For instance, MSSQL supports the `xp_cmdshell` command, which can be used to execute system commands.**
* **Leveraging Error Messages:** Exploit verbose error messages to gain insights into the database schema and structure. Error-based SQL injection involves provoking the application to generate error messages that reveal useful information. For example, using 1' AND 1=CONVERT(int, (SELECT @@version)) -- can generate errors that leak version information.
* **Bypassing WAF and Filters:** Test various obfuscation techniques to bypass Web Application Firewalls (WAF) and input filters. This includes using mixed case (SeLeCt), concatenation (CONCAT(CHAR(83), CHAR(69), CHAR(76), CHAR(69), CHAR(67), CHAR(84))), and alternate encodings (hex, URL encoding). Additionally, using inline comments (/\*\*/) and different character encodings (e.g., %09, %0A) can help bypass simple filters.
* **Database Fingerprinting:** Determine the type and version of the database to tailor the attack. This can be done by sending specific queries that yield different results depending on the DBMS. For instance, SELECT version() works on PostgreSQL, while SELECT @@version works on MySQL and **MSSQL.**
* **Pivoting with SQL Injection:** Use SQL injection to pivot and exploit other parts of the network. Once a database server is compromised, it can be used to gain access to other internal systems. This might involve extracting credentials or exploiting trust relationships between systems.

## Automation

Major Issues During Identification

Identifying SQL Injection vulnerabilities involves several challenges, similar to identifying any other server-side vulnerability. Here are the key issues:

* Dynamic Nature of SQL Queries: SQL queries can be dynamically constructed, making it difficult to detect injection points. Complex queries with multiple layers of logic can obscure potential vulnerabilities.
* Variety of Injection Points: SQL Injection can occur in different parts of an application, including input fields, HTTP headers, and URL parameters. Identifying all potential injection points requires thorough testing and a comprehensive understanding of the application.
* Use of Security Measures: Applications may use prepared statements, parameterized queries, and ORM frameworks, which can prevent SQL Injection. Automated tools must be able to differentiate between safe and unsafe query constructions.
* Context-Specific Detection: The context in which user inputs are used in SQL queries can vary widely. Tools must adapt to different contexts to accurately identify vulnerabilities.

Few Important Tools

Several renowned tools and projects have been developed within the security community to aid in the automation of finding SQL Injection vulnerabilities. Here are a few well-known tools and GitHub repositories that provide functionalities for detecting and exploiting SQL Injection:

* [SQLMap](https://github.com/sqlmapproject/sqlmap): SQLMap is an open-source tool that automates the process of detecting and exploiting SQL Injection vulnerabilities in web applications. It supports a wide range of databases and provides extensive options for both identification and exploitation. You can learn more about the tool [here](https://tryhackme.com/r/room/sqlmap).
* [SQLNinja](https://github.com/xxgrunge/sqlninja): SQLNinja is a tool specifically designed to exploit SQL Injection vulnerabilities in web applications that use Microsoft SQL Server as the backend database. It automates various stages of exploitation, including database fingerprinting and data extraction.&#x20;
* [JSQL Injection](https://github.com/ron190/jsql-injection): A Java library focused on detecting SQL injection vulnerabilities within Java applications. It supports various types of SQL Injection attacks and provides a range of options for extracting data and taking control of the database.
* [BBQSQL](https://github.com/CiscoCXSecurity/bbqsql): BBQSQL is a Blind SQL Injection exploitation framework designed to be simple and highly effective for automated exploitation of Blind SQL Injection vulnerabilities.&#x20;
