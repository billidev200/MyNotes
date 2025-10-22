# Curl - Wget

## wget

```bash
wget [options] <URL>
```

#### 🔸 Tips:

* Use `-q` for quiet mode (no output).
* Use `--no-check-certificate` if the SSL cert is invalid (not recommended for secure sites).

| Use Case                      | Command                                                | Explanation                           |
| ----------------------------- | ------------------------------------------------------ | ------------------------------------- |
| Download a file               | `wget https://example.com/file.zip`                    | Saves `file.zip` in current directory |
| Save with a custom name       | `wget -O newname.zip https://example.com/file.zip`     | Saves file as `newname.zip`           |
| Continue interrupted download | `wget -c https://example.com/file.zip`                 | Resumes download if interrupted       |
| Download in background        | `wget -b https://example.com/file.zip`                 | Runs download in background           |
| Limit download speed          | `wget --limit-rate=500k https://example.com/file.zip`  | Max speed: 500 KB/s                   |
| Mirror a full site            | `wget -m https://example.com`                          | Recursively downloads the entire site |
| Download recursively          | `wget -r https://example.com/folder/`                  | Downloads entire folder tree          |
| Specify user-agent            | `wget --user-agent="Mozilla" https://example.com`      | Spoofs browser identity               |
| Use authentication            | `wget --user=user --password=pass https://example.com` | For login-protected files             |

## curl

```bash
curl [options] <URL>
```

Make a JSON POST request:

```bash
curl -X POST -H "Content-Type: application/json" \
     -d '{"name": "John"}' \
     https://api.example.com/users
```

| Purpose                 | Command                                                                                         | Explanation                      |
| ----------------------- | ----------------------------------------------------------------------------------------------- | -------------------------------- |
| Download a file         | `curl -O https://example.com/file.zip`                                                          | Save file with original name     |
| Save with a custom name | `curl -o newfile.zip https://example.com/file.zip`                                              | Save file as `newfile.zip`       |
| Follow redirects        | `curl -L https://short.url`                                                                     | Follows URL redirects            |
| Get HTTP headers only   | `curl -I https://example.com`                                                                   | Shows response headers           |
| Send GET request        | `curl https://api.example.com/data`                                                             | Basic GET request                |
| Send POST request       | `curl -X POST -d "key=value" https://example.com`                                               | Submit form data                 |
| Send JSON data          | `curl -X POST -H "Content-Type: application/json" -d '{"key":"value"}' https://api.example.com` | API-style POST                   |
| Use Basic Auth          | `curl -u username:password https://example.com`                                                 | Authenticate via HTTP Basic Auth |
| Download silently       | `curl -s https://example.com`                                                                   | Suppresses progress output       |
