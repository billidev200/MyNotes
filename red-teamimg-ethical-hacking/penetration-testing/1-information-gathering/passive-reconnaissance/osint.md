# OSINT

## ShadowMap

Allows you to view shadows cast by buildings anywhere in the world and simulates where those shadows will fall at any time. Useful for figuring out the location of photos and videos in dense urban areas.

{% embed url="https://app.shadowmap.org/?azimuth=0.00000&basemap=map&elevation=nextzen&f=29.0&hud=true&lat=51.48786&lng=-0.10660&polar=0.00000&time=1750918064088&vq=2&zoom=16.92" %}

## &#x20;What's My Name App

Helps you find out what social media platforms someone is using by entering a username. You can filter results and export URLs.

{% embed url="https://whatsmyname.app/" %}

## &#x20;Osint framework

{% embed url="https://osintframework.com/" %}

## Wigle

Find wirless networks on the map by ssid,bissd or location

{% embed url="https://wigle.net/index" %}

## &#x20;Flight Radar 24

{% embed url="https://www.flightradar24.com/multiview/34.8,27.73/6" %}

## More Websites

{% embed url="https://docs.google.com/spreadsheets/d/1AWBe47i25_6657AUHM46UmhoO5xxr96eEPCcuQlPy0M/edit?gid=0#gid=0" %}

## More Tools

### email2phonenumber&#x20;

```
root@kali:~# email2phonenumber -h
usage: email2phonenumber.py [-h] {scrape,generate,bruteforce} ...

An OSINT tool to find phone numbers associated to email addresses

positional arguments:
  {scrape,generate,bruteforce}
                        commands
    scrape              scrape online services for phone number digits
    generate            generate all valid phone numbers based on NANPA's
                        public records
    bruteforce          bruteforce using online services to find the phone
                        number

options:
  -h, --help            show this help message and exit
```

### **sherlock**

<figure><img src="../../../../.gitbook/assets/sherlock-logo.svg" alt="" width="256"><figcaption></figcaption></figure>

Sherlock relies on the site’s designers providing a unique URL for a registered username. To determine if a username is available, Sherlock queries that URL, and uses to response to understand if there is a claimed username already there.

Currently, the tool is capable of locating users on more than 300 social networks: Apple Developer, Arduino, Docker Hub, GitHub, GitLab, Facebook, BitCoinForum, CNET, IFTTT, Instagram, PlayStore PyPI, Scribd, Telegram, TikTok, Tinder etc.

```
root@kali:~# sherlock -h
usage: sherlock [-h] [--version] [--verbose] [--folderoutput FOLDEROUTPUT]
                [--output OUTPUT] [--tor] [--unique-tor] [--csv] [--xlsx]
                [--site SITE_NAME] [--proxy PROXY_URL] [--dump-response]
                [--json JSON_FILE] [--timeout TIMEOUT] [--print-all]
                [--print-found] [--no-color] [--browse] [--local] [--nsfw]
                USERNAMES [USERNAMES ...]

Sherlock: Find Usernames Across Social Networks (Version 0.15.0)

positional arguments:
  USERNAMES             One or more usernames to check with social networks.
                        Check similar usernames using {?} (replace to '_',
                        '-', '.').

options:
  -h, --help            show this help message and exit
  --version             Display version information and dependencies.
  --verbose, -v, -d, --debug
                        Display extra debugging information and metrics.
  --folderoutput, -fo FOLDEROUTPUT
                        If using multiple usernames, the output of the results
                        will be saved to this folder.
  --output, -o OUTPUT   If using single username, the output of the result
                        will be saved to this file.
  --tor, -t             Make requests over Tor; increases runtime; requires
                        Tor to be installed and in system path.
  --unique-tor, -u      Make requests over Tor with new Tor circuit after each
                        request; increases runtime; requires Tor to be
                        installed and in system path.
  --csv                 Create Comma-Separated Values (CSV) File.
  --xlsx                Create the standard file for the modern Microsoft
                        Excel spreadsheet (xlsx).
  --site SITE_NAME      Limit analysis to just the listed sites. Add multiple
                        options to specify more than one site.
  --proxy, -p PROXY_URL
                        Make requests over a proxy. e.g.
                        socks5://127.0.0.1:1080
  --dump-response       Dump the HTTP response to stdout for targeted
                        debugging.
  --json, -j JSON_FILE  Load data from a JSON file or an online, valid, JSON
                        file.
  --timeout TIMEOUT     Time (in seconds) to wait for response to requests
                        (Default: 60)
  --print-all           Output sites where the username was not found.
  --print-found         Output sites where the username was found (also if
                        exported as file).
  --no-color            Don't color terminal output
  --browse, -b          Browse to all results on default browser.
  --local, -l           Force the use of the local data.json file.
  --nsfw                Include checking of NSFW sites from default list.
```
