# Logs

## Use Cases of Logs

| Use Case                             | Description                                                                                                                                                                                          |
| ------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Security Events Monitoring           | Logs help us detect anomalous behavior when real-time monitoring is used.                                                                                                                            |
| Incident Investigation and Forensics | Logs are the traces of every kind of activity. It offers detailed information on what happened during the incident. The security team utilizes the logs to perform root cause analysis of incidents. |
| Troubleshooting                      | As the logs also record the errors in systems or applications, they can be used to diagnose issues and helpful in fixing them.                                                                       |
| Performance Monitoring               | Logs can also provide valuable insights into the performance of applications.                                                                                                                        |
| Auditing and Compliance              | Logs play a major role in Auditing and Compliance, making it easier with its capability to establish a trail of different kinds of activities.                                                       |

## Types of Logs

| Log Type         | Usage                                                                                                                                                                                            | Example                                                                                                                                                 |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| System Logs      | The system logs can be helpful in troubleshooting running issues in the OS. These logs provide information on various operating system activities.                                               | <p>- System Startup and shutdown events<br>- Driver Loading events<br>- System Error events<br>- Hardware events</p>                                    |
| Security Logs    | The security logs help detect and investigate incidents. These logs provide information on the security-related activities in the system.                                                        | <p>-Authentication events<br>- Authorization events<br>- Security Policy changes events<br>- User Account changes events - Abnormal Activity events</p> |
| Application Logs | The application logs contain specific events related to the application. Any interactive or non-interactive activity happening inside the application will be logged here.                       | <p>- User Interaction events<br>- Application Changes events<br>- Application Update events<br>- Application Error events</p>                           |
| Audit Logs       | The Audit logs provide detailed information on the system changes and user events. These logs are helpful for compliance requirements and can play a vital role in security monitoring as well.  | <p>- Data Access events<br>- System Change events<br>- User Activity events<br>- Policy Enforcement events</p>                                          |
| Network Logs     | Network logs provide information on the network’s outgoing and incoming traffic. They play crucial roles in troubleshooting network issues and can also be handy during incident investigations. | <p>- Incoming Network Traffic events<br>- Outgoing Network Traffic events<br>- Network Connection Logs - Network Firewall Logs</p>                      |
| Access Logs      | The Access logs provide detailed information about the access to different resources. These resources can be of different types, providing us with information on their access.                  | <p>- Webserver Access Logs<br>- Database Access Logs - Application Access Logs<br>- API Access Logs</p>                                                 |

## Windows Event Logs Analysis

Like other operating systems, Windows OS also logs many of the activities that take place. These are stored in segregated log files, each with a specific log category. Some of the crucial types of logs stored in a Windows Operating System are:

* **Application:** There are many applications running on the operating system. Any information related to those applications is logged into this file. This information includes errors, warnings, compatibility issues, etc.
* **System:** The operating system itself has different running operations. Any information related to these operations is logged in the System log file. This information includes driver issues, hardware issues, system startup and shutdown information, services information, etc.
* **Security:** This is the most important log file in Windows OS in terms of security. It logs all security-related activities, including user authentication, changes in user accounts, security policy changes, etc.

<figure><img src="../../.gitbook/assets/6645aa8c024f7893371eb7ac-1719215860668.png" alt=""><figcaption></figcaption></figure>

Here is a table of some important Event IDs in Windows Operating System.

| Event ID | Description                                        |
| -------- | -------------------------------------------------- |
| 4624     | A user account successfully logged in              |
| 4625     | A user account failed to login                     |
| 4634     | A user account successfully logged off             |
| 4720     | A user account was created                         |
| 4724     | An attempt was made to reset an account’s password |
| 4722     | A user account was enabled                         |
| 4725     | A user account was disabled                        |
| 4726     | A user account was deleted                         |
