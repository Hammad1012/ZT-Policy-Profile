**Section 1** - ZTA Component Definitions
- **The Policy Engine** is the component responsible for making access decisions. Its main function is to evaluate every access request based on defined security policies and contextual information. This includes factors such as user identity, device status, location, time of request, and risk level. After analyzing all relevant data, the Policy Engine determines whether access should be granted, denied, or granted with certain conditions. It does not enforce the decision itself its sole responsibility is to make the final, logical determination.
- **The Policy Administrator** is the component responsible for communicating the Policy Engine's decision to the rest of the system. Its main function is to take the verdict produced by the Policy Engine and translate it into direct instructions. This includes actions such as issuing session tokens, establishing access credentials, or sending a signal to block and terminate a session entirely. After receiving the decision, the Policy Administrator passes those instructions along to the enforcement layer. It does not make decisions itself; its sole responsibility is to carry out and communicate the final verdict.
- **The Policy Enforcement** Point is the component responsible for physically controlling access to a protected resource. Its main function is to act as the gatekeeper that every access request must pass through before reaching the target system. This includes sitting directly in front of resources such as databases, applications, or network segments, and either opening or closing access based on the instructions it receives. After getting direction from the Policy Administrator, the Policy Enforcement Point acts immediately on those instructions. It does not make or communicate decisions itself  its sole responsibility is to enforce the final outcome

**Section 2** - Core Principle Application
- **Verify Explicitly** is the principle that requires every single access request to be fully checked and confirmed before any access is given. This means that no user, device, or network connection is automatically trusted just because it was trusted before or because it is coming from inside the organization. Every request must prove itself every single time.

  In the case of the Golden State Water Treatment Facility's HR Employee PII Database, the Policy Engine enforces this principle by checking the geographic location of every access request that comes in. For example, if an HR employee tries to access the database and their request is coming from an IP address outside of California or from a completely unrecognized location, the Policy Engine will deny access immediately. This is true even if the username and password being used are completely correct and valid. The Policy Engine does not just check the credentials and stop there  it evaluates the location as a separate and required signal before making its final decision. If the location does not match what is expected, the Policy Engine determines that the request cannot be trusted and issues a deny decision without the access ever reaching the database.

**Section 3** - Simplified Policy Table

| **Policy Requirement (Signal)** | **Condition to be Met by User** | **Action if Condition is Met** |
|---|---|---|
| User Identity | The user must be a confirmed HR Department employee at the Golden State Water Treatment Facility and must successfully verify their identity through Multi-Factor Authentication (MFA) at the time the request is made. | Grant Access |
| Device Posture | The device being used must be registered and recognized by the facility's device management system, running an updated and fully patched operating system, with endpoint security software that is active and up to date. | Grant Access |
| Network Context | The access request must be coming from inside the facility's internal network or through an approved and active VPN connection that can be traced back to a California-based location. | Grant Access |

**Section 4** - Submission Details & Documentation

# Git Repository Metadata

Filename: ZT-Policy-Profile.md

Commit Message: 
