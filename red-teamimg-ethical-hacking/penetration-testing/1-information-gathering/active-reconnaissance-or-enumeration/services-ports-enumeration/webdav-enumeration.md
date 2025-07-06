# WebDAV Enumeration

**WebDAV (Web Distributed Authoring and Versioning)** is an extension of HTTP that allows clients to perform remote web content authoring operations like create, move, delete files on a web server.

{% hint style="warning" %}
WebDAV is a protocol for file uploading and downloading services. After logging in, we can view directories, and by accessing these directories, we can upload files to gain access to the system or download confidential information.
{% endhint %}

Commonly runs on ports:

* **80** (HTTP)
* **443** (HTTPS)
* Sometimes custom ports

### Why enumerate WebDAV?

* To identify exposed file shares/folders
* Discover sensitive files or directories
* Exploit misconfigurations for uploading/downloading files
* Gain foothold or escalate privileges

***

## **Common WebDAV Enumeration Techniques**

### 1. **Identify WebDAV Support**

* Check if HTTP methods like `OPTIONS`, `PROPFIND`, `PUT`, `DELETE`, `PROPPATCH` are allowed.

```bash
curl -v -X OPTIONS http://target/
```

***

### 2. **Using Davtest**

[`davtest`](https://github.com/jonathanchu/davtest) is a popular tool to test for WebDAV on a target.

* It brute forces common WebDAV endpoints and tests file upload/download abilities.

1. Test Dav connection

<figure><img src="../../../../../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

2. Connect with to WebDav

```bash
davtest -auth bob:password_123321 -url http://10.2.17.124/webdav
```

#### What happens?

* `davtest` will try to **connect to the WebDAV server at `http://10.2.17.124/webdav` using the provided username and password**.
* It will check if WebDAV is enabled and supported.
* It will attempt operations like:
  * Listing directories (using PROPFIND)
  * Will try Upload test files to check if write access is allowed
  * Will try  Downloading files
  * Will try  Checking for common vulnerabilities or misconfigurations.

{% hint style="warning" %}
Based of the results of davtest we can see what we can upload and execute

Based of the succeed files results we can create a reverse shell payload Examle if asp or php succeed means it support that file and that means we can use it to create a payload
{% endhint %}

<figure><img src="../../../../../.gitbook/assets/image (10).png" alt=""><figcaption></figcaption></figure>

3. Next we use the cadaver Utility to upload our payload

Login

```bash
cadaver https://example.com/webdav
```

Common commands&#x20;

* ls

Upload file/payload webshell

```bash
put localfile.txt remotefile.txt
```

* `localfile.txt` is the file on your local machine.
* `remotefile.txt` is the filename to save as on the server (optional, defaults to the same name).

Download a File

```bash
get remotefile.txt localfile.txt    
```

* `remotefile.txt` is the file on the server.
* `localfile.txt` is the filename to save as locally (optional).

***

### 3. **Using Nmap WebDAV scripts**

```bash
nmap -sV -p 80 --script=http-enum <target>
```

```bash
nmap -sV -p 80 --script=http-webdav-scan <target>
```

***

### 4. **Manual PROPFIND Enumeration**

```bash
curl -X PROPFIND http://target/webdav/ -H "Depth: 1"
```

***

### 5. Metasploit Auxiliary

* auxiliary/scanner/http/webdav\_scanner

<figure><img src="../../../../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>

***

### 6. Bruteforce

```bash
hydra -L users.txt -P passwords.txt http-get://webdav/
```

On `http-get://` specify the directory that contains the authentication form
