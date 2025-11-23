# Security Misconfiguration

Security misconfigurations include:

* Poorly configured permissions on cloud services, like S3 buckets.
* Having unnecessary features enabled, like services, pages, accounts or privileges.
* Default accounts with unchanged passwords.
* Error messages that are overly detailed and allow attackers to find out more about the system.
* Not using [HTTP security headers](https://owasp.org/www-project-secure-headers/).

**Common Patterns**

* Default credentials or weak passwords left unchanged
* Unnecessary services or endpoints exposed to the internet
* Misconfigured cloud storage or permissions (S3, Azure Blob, GCP buckets)
* Unrestricted API access or missing authentication/authorisation
* Verbose error messages exposing stack traces or system details
* Outdated software, frameworks, or containers with known vulnerabilities
* Exposed AI/ML endpoints without proper access controls

**How To Prevent It**

* Harden default configurations and remove unused features or services
* Enforce strong authentication and least privilege across all systems
* Limit network exposure and segment sensitive resources
* Keep software, frameworks, and containers up to date with patches
* Hide stack traces and system information from error messages
* Audit cloud configurations and permissions regularly
* Secure AI endpoints and automation services with proper access controls and monitoring
* Integrate configuration reviews and automated security checks into your deployment pipeline
