# SAST

## Code Review

**Manual vs Automated Code Review**

Code reviews are often done through a combination of manual analysis and automated tools for the best results. Both approaches have advantages that need to be considered when deciding what is best at each stage of the development lifecycle.

On the one hand, manual code reviews have the advantage of a human evaluating the code, which allows for a thorough analysis and more precise results. However, since an application often has thousands and thousands of lines of code, the task can quickly become overwhelming for the reviewer, leading to some vulnerabilities being missed because of fatigue.

On the other hand, automated tools excel at finding common vulnerabilities almost instantly, saving loads of time to the reviewer. Automated tools will also perform consistently, no matter the size of the code base, so they won't miss vulnerabilities as a human could do, as long as they have predefined rules to match them. If the tool has no rules configured for a specific type of vulnerability, they are likely to miss those.

Another important aspect to compare is cost. The cost of a manual review will often be higher, as a reviewer must spend lots of time tracing vulnerabilities through the code. Automated tools will perform their analysis almost instantly.

For these reasons, you will typically want to run automated tests early in the development lifecycle to take care of all the low-hanging fruits with lower costs and have manual reviews spaced periodically or when important project goals are met to take care of complex vulnerabilities that the automated tools may not be able to detect.

## SAST in the Development Cycle

<figure><img src="../../../.gitbook/assets/8d4c2f1e6b6b61d8e13d8e0c4597773e.png" alt=""><figcaption></figcaption></figure>
