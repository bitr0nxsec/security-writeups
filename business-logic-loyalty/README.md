


# Business Logic Vulnerability | Loyalty Point Validation Flaw

## Overview

While interacting with a real-world website, I discovered a business logic vulnerability related to the website's loyalty/reward point system.

The issue allowed reward points to be earned incorrectly after a canceled/pending checkout session, resulting in unintended discount duplication on future purchases.

The platform name will not be mentioned for responsible disclosure and ethical reasons.

---

## Discovery Process

The vulnerability was discovered unintentionally while testing trying to get my previous checkout session back after a failed purchase attempt.

### Initial Observation

After:

creating an account
receiving initial signup reward points
and initiating a checkout session

I noticed inconsistent behavior involving:

canceled orders
pending payment sessions
and loyalty points granted without proper verification

The platform appeared to incorrectly count a canceled/pending order as a valid completed order for rewarding.

---

## Vulnerable Logic

The backend reward system granted additional loyalty points even though:

The original order was never successfully completed.
And the failed transaction should not have qualified for rewarding loyalty points.

This resulted in:

extra reward points being added to the account balance.
Wich could then be redeemed as discounts during checkout.

### Potential Impact

If repeatable at through lots of accounts, this flaw could potentially allow:

* artificial loyalty point farming,
* unintended discount accumulation,
* and financial abuse of the reward system.

---

## Security Concepts Involved

Business Logic Vulnerabilities
Reward System Abuse
Transaction State Validation
Session/Checkout Logic
Server-Side Validation Failures

---

## Ethical Handling

The issue was not intentionally abused beyond a minimal PoC.

After confirming the inconsistent backend behavior, no further attempts were made to scale or automate the issue.

The platform identity remains undisclosed for ethical and responsible reasons.

---

## What I Learned

This experience taught me:

how real-world vulnerabilities can emerge from flawed business logic,
the importance of server-side validation,
and how observation and curiosity can reveal impactful security weaknesses even without advanced exploitation techniques.

It also reinforced the importance of ethical decision-making in cybersecurity research.
