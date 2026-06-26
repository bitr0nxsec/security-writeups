# Information Disclosure Assessment (Anonymized Joomla Application)

> **Status:** Responsibly disclosed to the website owner before publication.
>
> This repository documents a low-risk information disclosure issue discovered during reconnaissance of a public Joomla-based web application. The affected organization and domain have intentionally been anonymized.

---

# Summary

While performing passive reconnaissance against a publicly accessible Joomla application, I identified that custom error pages exposed a production debugging interface.

The exposed interface provided significantly more information than intended, including framework metadata, executed SQL queries, request/session information and server-side environment details.

Although no evidence of direct exploitation was found, the exposed debugging information could provide valuable reconnaissance data to an attacker.

No exploitation attempts were performed.

---

# Scope

This assessment consisted only of passive reconnaissance and observation.

Performed activities included:

* Reviewing `robots.txt`
* Directory enumeration using a small wordlist
* Technology fingerprinting
* Manual inspection of HTTP responses
* Reviewing publicly accessible error pages

No authentication bypass, brute force, vulnerability exploitation or destructive testing was performed.

---

# Initial Findings

During reconnaissance several administrative endpoints were identified, including:

* Administrator portal
* phpMyAdmin login interface
* API endpoints
* Public static resources

Most administrative directories correctly returned HTTP 403 or 401 responses.

This is considered good practice and was not reported as a vulnerability.

---

# Technology Fingerprinting

Passive fingerprinting identified the following technologies:

* Joomla CMS
* PHP
* MariaDB

Version information was visible through the exposed debugging interface.

Although public CVEs exist for versions within the detected software range, **version identification alone is not sufficient to conclude exploitability**, therefore no exploitation attempts were made.

---

# Debug Information Exposure

The primary finding was the exposure of a production debugging interface on custom error pages.

The interface revealed information such as:

* Framework version
* PHP version
* Database engine
* Database version
* SQL queries executed during the request
* Session metadata
* Cookie information
* Request variables
* Server variables
* Stack traces
* File paths
* Execution timings

  <img width="1424" height="242" alt="image" src="https://github.com/user-attachments/assets/6e0bf16d-f6d2-4ba2-8fbe-7022f5d72611" />


While none of this immediately resulted in remote code execution or unauthorized access, it provides unnecessary reconnaissance data that could reduce an attacker's effort when identifying potential attack paths.

---

# Security Impact

This issue is classified as an **Information Disclosure** finding.

Potential risks include:

* Easier technology fingerprinting
* Framework version disclosure
* Internal implementation details
* Database query visibility
* Server environment reconnaissance
* Reduced effort required during future attacks

<img width="1865" height="331" alt="image" src="https://github.com/user-attachments/assets/52f65767-4106-4aa2-ae70-b352708e10c1" />


---

# Recommendations

The following mitigations were recommended:

* Disable production debugging interfaces.
* Prevent debugging middleware from loading in production.
* Avoid exposing stack traces to unauthenticated users.
* Return generic error pages for unexpected exceptions.
* Limit publicly available framework metadata.

---

# Responsible Disclosure

The website owner was privately notified before publishing this repository.

The purpose of this repository is educational and to demonstrate a responsible disclosure workflow rather than to expose a specific organization.

No exploitation was performed and no sensitive data was intentionally accessed.

---

# Skills Demonstrated

* Passive Reconnaissance
* Web Enumeration
* HTTP Analysis
* Technology Fingerprinting
* Information Disclosure Identification
* Responsible Disclosure
* Technical Documentation
