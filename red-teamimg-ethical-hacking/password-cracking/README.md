---
description: 🔐 Password Cracking Types & Attacks
---

# Password Cracking

#### 1. **Brute Force Attack**

* **How it works:**\
  Tries **every possible combination** of characters until it finds the correct password.
* **Pros:**\
  Guaranteed to find the password eventually.
* **Cons:**\
  Extremely slow for long or complex passwords; computationally expensive.
* **Use case:**\
  When you have no clues about the password.

***

#### 2. **Dictionary Attack**

* **How it works:**\
  Tries passwords from a **predefined list (dictionary)** of common passwords, words, or leaked passwords.
* **Pros:**\
  Much faster than brute force; effective if password is common or simple.
* **Cons:**\
  Won’t find passwords not in the dictionary.
* **Use case:**\
  When guessing simple or common passwords.

***

#### 3. **Hybrid Attack**

* **How it works:**\
  Combines dictionary and brute force; tries dictionary words with small variations (e.g., adding numbers, symbols).
* **Pros:**\
  Good balance of speed and coverage.
* **Cons:**\
  Can still miss very complex or random passwords.
* **Use case:**\
  When password is a slight modification of a common word.

***

#### 4. **Rainbow Table Attack**

* **How it works:**\
  Uses **precomputed tables** of hash-to-password mappings to reverse hashed passwords quickly.
* **Pros:**\
  Extremely fast lookup of common hashes.
* **Cons:**\
  Requires large storage; ineffective against salted hashes.
* **Use case:**\
  When cracking unsalted hashes like old password databases.

| Type                | Target                           | Online/Offline | Typical Tools            | Notes                           |
| ------------------- | -------------------------------- | -------------- | ------------------------ | ------------------------------- |
| Hash Cracking       | Password hashes                  | Offline        | Hashcat, John the Ripper | Needs hashes, fast with GPU     |
| Service Brute-Force | Online services (SSH, FTP, etc)  | Online         | Hydra, Medusa, Ncrack    | Limited by lockouts/captcha     |
| Offline Cracking    | Password hashes                  | Offline        | Hashcat, John the Ripper | No lockouts, very fast          |
| Online Cracking     | Login interfaces                 | Online         | Hydra, Burp Suite        | Slower, with protections        |
| Password Spraying   | Many accounts with few passwords | Online         | Custom scripts           | Evades lockouts                 |
| Credential Stuffing | Using leaked creds               | Online         | Sentry MBA, Snipr        | Exploits password reuse         |
| Rainbow Table       | Unsalted hashes                  | Offline        | Ophcrack, custom tables  | Large storage, outdated method  |
| Hybrid Attacks      | Password hashes                  | Offline        | Hashcat, John the Ripper | Dictionary + brute force combos |
|                     |                                  |                |                          |                                 |

**5.Passowrd spraying**

**Password spraying** is a type of attack where an attacker tries a **few common passwords** against **many accounts**, instead of trying many passwords on a single account.

This is different from a traditional brute-force attack. Let me break it down:

#### 1. **How it works**

* Pick a list of common passwords (e.g., `Password123`, `Welcome1`, `Summer2025`)
* Try **the same password on multiple accounts** (e.g., user1, user2, user3…)
* Wait between attempts to **avoid account lockouts**

#### 2. **Why attackers do this**

* Many organizations **lock accounts after multiple failed login attempts**, so brute-force on one account often fails.
* By spreading attempts across multiple accounts, the attacker **avoids triggering lockouts**.
* It exploits the fact that **users often reuse common passwords**.
