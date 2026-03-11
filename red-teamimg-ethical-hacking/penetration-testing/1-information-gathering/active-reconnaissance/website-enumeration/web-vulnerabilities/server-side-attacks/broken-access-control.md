# Broken Access Control

A regular visitor being able to access protected pages can lead to the following:

* Being able to view sensitive information from other users
* Accessing unauthorized functionality

Simply put, broken access control allows attackers to bypass authorisation, allowing them to view sensitive data or perform tasks they aren't supposed to.

For example, a [vulnerability was found in 2019](https://bugs.xdavidhu.me/google/2021/01/11/stealing-your-private-videos-one-frame-at-a-time/), where an attacker could get any single frame from a Youtube video marked as private. The researcher who found the vulnerability showed that he could ask for several frames and somewhat reconstruct the video. Since the expectation from a user when marking a video as private would be that nobody had access to it, this was indeed accepted as a broken access control vulnerability.

If you don't get access to more roles but can view the data of another users, what type of privilege escalation is this?

```
Horizontal PrivEsc
```

