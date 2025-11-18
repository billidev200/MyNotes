---
icon: network-wired
---

# Secure Network Architecture

Network Segmentation

Common Secure Network Architecture

| <p>Zone<br></p>                     | <p>Explanation<br></p>                                                                                                                                       | <p>Examples<br></p>                                  |
| ----------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------- |
| <p>External<br></p>                 | <p>All devices and entities outside of our network or asset control.<br></p>                                                                                 | <p>Devices connecting to a web server<br></p>        |
| <p>DMZ (demilitarized zone)<br></p> | <p>Separates untrusted networks or devices from internal resources.<br></p>                                                                                  | <p>BYOD, remote users/guests, public servers<br></p> |
| <p>Trusted<br></p>                  | <p>Internal networks or devices. A device may be placed in the trusted zone if there is no confidential or sensitive information. <br></p>                   | <p>Workstations, B2B<br></p>                         |
| <p>Restricted<br></p>               | <p>Any high-risk servers or databases. <br></p>                                                                                                              | <p>Domain controllers, client information<br></p>    |
| <p>Management<br></p>               | <p>Any devices or services dedicated to network or other device management. This zone is less commonly seen and can be grouped with the audit zone. <br></p> | <p>Virtualization management, backup servers<br></p> |
| <p>Audit<br></p>                    | <p>Any devices or services dedicated to security or monitoring. This zone is less commonly seen and can be grouped with management.<br></p>                  | SIEM, telemetry                                      |
