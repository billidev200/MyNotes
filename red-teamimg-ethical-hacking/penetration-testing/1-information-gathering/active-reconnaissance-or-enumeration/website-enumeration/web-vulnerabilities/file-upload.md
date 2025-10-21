---
description: >-
  Revshells depends on file server example if server php then a php revshell
  might work
---

# File Upload

## Methodology

## Overwriting Existing Files

<figure><img src="../../../../../../.gitbook/assets/5e86dbbd98fde62929a7e03b-1759494686706.png" alt="" width="278"><figcaption></figcaption></figure>

<figure><img src="../../../../../../.gitbook/assets/5e86dbbd98fde62929a7e03b-1759494769552.png" alt="" width="497"><figcaption></figcaption></figure>

<figure><img src="../../../../../../.gitbook/assets/5e86dbbd98fde62929a7e03b-1759495388389.png" alt="" width="375"><figcaption></figcaption></figure>

And our attack was successful! We managed to overwrite the original `images/spaniel.jpg` with our own copy.

## RCE

Uploading WebShells and gaining access revshell , c2 webshell.

## Filtering Types

### _Extension Validation:_

They either _blacklist_ extensions (i.e. have a list of extensions which are **not** allowed) or they _whitelist_ extensions (i.e. have a list of extensions which **are** allowed, and reject everything else).

### _File Type Filtering:_

Similar to Extension validation, but more intensive, file type filtering looks, once again, to verify that the contents of a file are acceptable to upload. We'll be looking at two types of file type validation:

_**MIME validation:**_ MIME (**M**ultipurpose **I**nternet **M**ail **E**xtension) types are used as an identifier for files -- originally when transfered as attachments over email, but now also when files are being transferred over HTTP(S). The MIME type for a file upload is attached in the header of the request, and looks something like this:

<figure><img src="../../../../../../.gitbook/assets/uptWRKW.png" alt=""><figcaption></figcaption></figure>

_**Magic Number validation:**_ Magic numbers are the more accurate way of determining the contents of a file; although, they are by no means impossible to fake. The "magic number" of a file is a string of bytes at the very beginning of the file content which identify the content. For example, a PNG file would have these bytes at the very top of the file:

{% hint style="info" %}
Unlike Windows, Unix systems use magic numbers for identifying files; however, when dealing with file uploads, it is possible to check the magic number of the uploaded file to ensure that it is safe to accept. This is by no means a guaranteed solution, but it's more effective than checking the extension of a file.
{% endhint %}

### _File Size Filtering:_

File length filters are used to prevent huge files from being uploaded to the server via an upload form (as this can potentially starve the server of resources). In most cases this will not cause us any issues when we upload shells; however, it's worth bearing in mind that if an upload form only expects a very small file to be uploaded, there may be a length filter in place to ensure that the file length requirement is adhered to. As an example, our fully fledged PHP reverse shell from the previous task is 5.4Kb big -- relatively tiny, but if the form expects a maximum of 2Kb then we would need to find an alternative shell to upload.

### _File Name Filtering:_

As touched upon previously, files uploaded to a server should be unique. Usually this would mean adding a random aspect to the file name, however, an alternative strategy would be to check if a file with the same name already exists on the server, and give the user an error if so. Additionally, file names should be sanitised on upload to ensure that they don't contain any "bad characters", which could potentially cause problems on the file system when uploaded (e.g. null bytes or forward slashes on Linux, as well as control characters such as `;` and potentially unicode characters). What this means for us is that, on a well administered system, our uploaded files are unlikely to have the same name we gave them before uploading, so be aware that you may have to go hunting for your shell in the event that you manage to bypass the content filtering.

## Bypassing Client-Side Filtering



