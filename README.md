# 🚀 Roblox VM Email Checker

## 📌 Overview

This Python script checks if an **email address** is **registered** on Roblox by sending a request to the Roblox Account Settings API.  
It can be useful for verifying if an email is linked to an existing Roblox account.

---

## ✅ Features

- 📨 Checks if an email is registered.
- 🔒 Uses your own `.ROBLOSECURITY` cookie for authentication.
- 🔑 Uses your own CSRF token.
- ⚡️ Optionally supports proxies for faster or bulk checks.

---

## 🛠️ Example Usage

```python
import requests

def roblox_vm(email):
    url = "https://accountsettings.roblox.com/v1/email"

    headers = {
        "Connection": "keep-alive",
        "Content-Type": "application/json;charset=UTF-8",
        "Cookie": "<YOUR_ROBLOX_COOKIES_HERE>",
        "User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/137.0.0.0 Safari/537.36",
        "x-csrf-token": "<YOUR_CSRF_TOKEN_HERE>"
    }

    data = {
        "emailAddress": email,
        "password": ""
    }

    # OPTIONAL: Use proxies for faster/bulk checks
    proxies = {
        # Example: "http": "http://username:password@proxy_ip:proxy_port",
        # Example: "https": "http://username:password@proxy_ip:proxy_port",
    }

    response = requests.post(url, headers=headers, json=data, proxies=proxies)
    if "There are too many accounts associated with this email address" in response.text:
        return 'Registered'
    else:
        return "Available"

print(roblox_vm('asd@gmail.com'))
```

---

## ⚡️ Proxies (Optional)

- To check many emails quickly, use proxies.
- Add a `proxies` dictionary as shown in the example.
- Format:  
  ```python
  proxies = {
      "http": "http://username:password@ip:port",
      "https": "http://username:password@ip:port",
  }
  ```

---

## 📦 Requirements

- Python 3.x
- Install `requests`:
  ```bash
  pip install requests
  ```

---

## ⚠️ Disclaimer

- You **must** use your own `.ROBLOSECURITY` cookie and CSRF token.
- **NEVER share your cookie/token!**
- For **educational purposes only**. Use responsibly.

---

## ✅ How to Use

1️⃣ Replace `<YOUR_ROBLOX_COOKIES_HERE>` with your `.ROBLOSECURITY` cookie.  
2️⃣ Replace `<YOUR_CSRF_TOKEN_HERE>` with your valid CSRF token.  
3️⃣ Optionally configure proxies for speed.  
4️⃣ Run the script and check emails!

---

## 📃 License

**Educational use only. Use at your own risk.**
