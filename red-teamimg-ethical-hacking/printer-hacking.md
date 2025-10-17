---
icon: print
---

# Printer Hacking

## The Internet Printing Protocol (IPP) 631

When an IPP port is open to the internet, it is possible for anyone to print to the printer or even transfer malicious data through it (using it as a middleman for attacks).

An open IPP port can expose a lot of sensitive information such as printer name, location, model, firmware version, or even printer wifi SSID.

## Toolkit

{% embed url="https://github.com/RUB-NDS/PRET" %}

{% embed url="http://hacking-printers.net/wiki/index.php/Main_Page" %}

## Locating printers

```
python2 pret.py
```

## Usage&#x20;

```
usage: pret.py [-h] [-s] [-q] [-d] [-i file] [-o file] target {ps,pjl,pcl}

positional arguments:
  target                printer device or hostname
  {ps,pjl,pcl}          printing language to abuse

optional arguments:
  -h, --help            show this help message and exit
  -s, --safe            verify if language is supported
  -q, --quiet           suppress warnings and chit-chat
  -d, --debug           enter debug mode (show traffic)
  -i file, --load file  load and run commands from file
  -o file, --log file   log raw data sent to the target
```
