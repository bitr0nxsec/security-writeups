# Business logic loyalty
Writeups and notes related to cybersecurity, web security, and business logic vulnerabilities.


# Business Logic Vulnerability – Loyalty Point Validation Flaw

## Overview

While interacting with a real-world ecommerce platform, I discovered a business logic vulnerability related to the platform’s loyalty/reward point system.

The issue allowed reward points to be granted incorrectly after a canceled/pending checkout session, resulting in unintended discount accumulation on future purchases.

The platform name has been intentionally omitted for responsible disclosure and ethical reasons.

---

## Discovery Process

The vulnerability was discovered unintentionally while testing different checkout/payment flows during a purchase attempt.

### Initial Observation

After:

* creating an account,
* receiving initial signup reward points,
* and initiating a checkout session,

I noticed inconsistent behavior involving:

* canceled orders,
* pending payment sessions,
* and loyalty point allocation.

The platform appeared to incorrectly count a canceled/pending order as a valid completed order for reward progression.

---

## Vulnerable Logic

The backend reward system granted additional loyalty points even though:

* the original order was never successfully completed,
* and the transaction state should not have qualified for reward issuance.

This resulted in:

* extra reward points being added to the account balance,
* which could then be redeemed as monetary discounts during checkout.

### Potential Impact

If repeatable at scale, this flaw could potentially allow:

* artificial loyalty point farming,
* unintended discount accumulation,
* and financial abuse of the reward system.

This demonstrates a business logic vulnerability affecting transactional integrity rather than a traditional technical exploit such as XSS or SQL injection.

---

## Security Concepts Involved

* Business Logic Vulnerabilities
* Reward System Abuse
* Transaction State Validation
* Session/Checkout Logic
* Server-Side Validation Failures

---

## Ethical Handling

The issue was not intentionally abused beyond minimal confirmation of the vulnerability.

After confirming the inconsistent backend behavior, no further attempts were made to scale or automate the issue.

The platform identity remains undisclosed for ethical and responsible reasons.

---

## What I Learned

This experience taught me:

* how real-world vulnerabilities can emerge from flawed business logic,
* the importance of server-side validation,
* and how observation and curiosity can reveal impactful security weaknesses even without advanced exploitation techniques.

It also reinforced the importance of ethical decision-making in cybersecurity research.
