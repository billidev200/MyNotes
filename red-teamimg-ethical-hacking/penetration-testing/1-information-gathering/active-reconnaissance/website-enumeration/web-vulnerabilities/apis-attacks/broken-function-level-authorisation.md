# Broken Function Level Authorisation

## 🧪 **Simple Example of BFLA (Web App)**

A regular user only sees a normal dashboard.\
The admin sees a “Delete User” button.

But the frontend hides the admin button visually using the UI.

However, the backend endpoint still exists:

```
POST /admin/deleteUser?id=55
```

[**https://chatgpt.com/share/691e33ec-0cc0-8013-9ca4-0e49dd3e9e6f**](https://chatgpt.com/share/691e33ec-0cc0-8013-9ca4-0e49dd3e9e6f)
