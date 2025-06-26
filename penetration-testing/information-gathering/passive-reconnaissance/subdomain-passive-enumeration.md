# Subdomain Passive Enumeration

## Sublist3r

<figure><img src="../../../.gitbook/assets/image (1) (1).png" alt="" width="509"><figcaption></figcaption></figure>

**Sublist3r** finds subdomains **without brute-force by default.**

```bash
sublist3r -d example.com -p 80,443
```

| Short Form | Long Form    | Description                                             |
| ---------- | ------------ | ------------------------------------------------------- |
| -d         | --domain     | Domain name to enumerate subdomains of                  |
| -b         | --bruteforce | Enable the subbrute bruteforce module                   |
| -p         | --ports      | Scan the found subdomains against specific tcp ports    |
| -v         | --verbose    | Enable the verbose mode and display results in realtime |
| -t         | --threads    | Number of threads to use for subbrute bruteforce        |
| -e         | --engines    | Specify a comma-separated list of search engines        |
| -o         | --output     | Save the results to text file                           |
| -h         | --help       | show the help message and exit                          |
