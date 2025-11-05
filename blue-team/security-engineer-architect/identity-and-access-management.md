# Identity & Access Management

Identity and Access Management (IAM) is a security framework that ensures the right people have the right access to the right resources at the right time. It involves managing user identities (like accounts and roles) and controlling their access to systems, applications, and data. IAM helps protect sensitive information by verifying user identities through authentication (like passwords or biometrics) and authorizing what actions they can perform. In short, it keeps systems secure while making it easier for users to access what they need safely.=

## IAAA Model

<figure><img src="../../.gitbook/assets/97c967ea1b1efd06260dbbf88ae5c19b.png" alt="" width="375"><figcaption></figcaption></figure>

1. **Identification** is the process of verifying who the user is. It starts with the user claiming a specific identity. The identity can be represented by a unique identifier such as an email address, a username, or an ID number. Any identifier unique in the respective environment is a valid option; hence, many websites would rely on an email address for identification instead of asking the user to create a unique username.
2. **Authentication** is the process of ensuring that the user is who they claim to be. In other words, this step is about confirming the claimed identity. One way to authenticate would be by providing the correct password. Because of potential password weaknesses, many other methods, such as asking users to type the code sent to their email, are gaining popularity.
3. **Authorisation** determines what the user is allowed to access. In other words, they will be authorised to carry out specific operations based on their account privileges. This process is typically done by assigning roles and permissions based on the user’s job function or level of clearance. The risk of unauthorised access or data breaches is reduced by restricting access to only the resources necessary for the user to perform their duties.
4. **Accountability** tracks user activity to ensure they are responsible for their actions. After a user is granted access to a system, it is essential to have mechanisms that hold everyone accountable for their actions. This process is achieved by logging all user activity and storing it in a centralised location. In the event of a security incident, this information can be used to identify the source of the problem and take appropriate action.

## Multi-Factor Authentication (MFA)

Multi-factor authentication (MFA) refers to using two or more of the above mechanisms (something you know/have/are). The purpose is to have additional security in case one authentication mechanism gets compromised.

If you want to use a bank’s ATM, insert your credit/debit card and type your PIN code. This procedure is one of the earliest two-factor authentication (2FA) examples. The apparent utility is that it is not enough for the attacker to get hold of your card, as they would also need to know your PIN code.

Many of the home safes available today use 2FA without necessarily marketing it. They require the owner to insert a key and enter the correct PIN code for the safe to open. You need to **know** the PIN and **have** the key to open it. Consequently, if someone else manages to get hold of the safe key, they still won’t be able to open the safe without knowing the PIN code.

In iterate, 2FA requires two authentication mechanisms, and it falls under the more general MFA, which requires two or more authentication factors. This requirement can significantly improve security and protect against various attacks, such as those that take advantage of weak passwords.

* Something you know
* Something you have
* Something you are

## Access Control Models

A system controls access to various resources based on the chosen model. Some of the common access control models are:

1. Discretionary Access Control (DAC)
2. Role-Based Access Control (RBAC)
3. Mandatory Access Control (MAC)

**Discretionary Access Control (DAC):**

In DAC, the owner of a resource (like a file or folder) decides who can access it and what they can do with it. This means access is based on the owner’s discretion, and permissions can be easily changed or shared. While flexible, DAC can be less secure because users can accidentally or intentionally give access to unauthorized people.

**Role-Based Access Control (RBAC):**\
RBAC assigns permissions based on a user’s role in an organization. For example, an “admin” might have full access, while a “staff” member has limited access. This approach makes managing permissions easier and more consistent, especially in large organizations, since users inherit access rights based on their job responsibilities.

**Mandatory Access Control (MAC):**\
MAC is the strictest access control model. In this system, access decisions are made by a central authority based on security labels or classifications (like “Confidential” or “Top Secret”). Users cannot change permissions on resources. This model is commonly used in military or government environments where security is a top priority.

## Single Sign-On

<figure><img src="../../.gitbook/assets/7d0fb1602afffa2b2b11739d0abeed48.png" alt="" width="563"><figcaption></figcaption></figure>

SSO allows organisations to authenticate users once before granting them access to the resources required for their work. We can achieve many advantages from this. We will mention a few.

* One strong password: Expecting a user to remember a single strong password is more acceptable than asking them to remember ten different strong passwords.
* Easier MFA: Adding MFA to every different service is a humongous task to accomplish and maintain. With SSO, MFA needs to be enabled and configured once.
* Simpler Support: Support requests like password reset become more straightforward as they are now confined to a single account.
* Efficiency: A user does not need to log in every time they need to access a new service.
