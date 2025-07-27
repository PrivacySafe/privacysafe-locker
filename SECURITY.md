# Vulnerability Disclosure Policy &amp; Bug Bounty Program
_Last Updated: July 27, 2025_

## <a name="introduction">Introduction</a>

PrivacySafe is a brand of products and services that include hardware and software distributed by Ivy Cyber. Protecting the privacy and security of users is our top priority. If you identify any problems with our hardware, software, or infrastructure, such as security issues, privacy risks, exposed data, or software vulnerabilities, we encourage you to report these issues to us. We provide bug bounty rewards for responsible disclosures from members of the global "white hat" hacking and Open Source Intelligence (OSINT) communities.

We are dedicated to releasing PrivacySafe products and services built upon ethical Free and Open-Source Software (FOSS). Responsible disclosure practices by researchers will result in transparent and honest publishing and [acknowledgement](https://privacysafe.app/security-thanks) after risks to the public, our users, and our team have been resolved or mitigated against.

## [Open Bug Bounty](https://www.openbugbounty.org/bugbounty/privacysafe/)

Our program is listed at Open Bug Bounty, a community of 55K+ security researchers around the world. You should report vulnerabilities there if feasible: 

[https://openbugbounty.org/bugbounty/privacysafe/](https://www.openbugbounty.org/bugbounty/privacysafe/)

The information at that URL refers to this policy. Researchers who submit via Open Bug Bounty can build a reputation for their skills and we will provide positive recommendations for responsible researchers.

## <a name="scope">Scope</a>

This policy applies to:

* Source Code repositories in [https://github.com/privacysafe](https://github.com/privacysafe) and [https://gitlab.com/privacysafe](https://gitlab.com/privacysafe);
* Whitepapers and research articles; and 
* Infrastructure owned and operated by Ivy Cyber or maintained by PrivacySafe projects. This includes websites and public-facing applications.

### <a name="out-of-scope">Out of Scope</a>

This policy does not apply to:

* Archived repositories;
* End-user documentation and educational or "help" materials;
* Support, marketing, and social media channels (e.g., PrivacySafe Social posts);
* Social engineering of our customers and users, our team members, and FOSS contributors;
* Services, applications, and mix networks run by volunteers (e.g., Tor hidden services);
* Assets, equipment, and systems not owned by Ivy Cyber or administered by PrivacySafe projects; and
* [Commonplace Reports](#commonplace-reports) as described in this policy.

If you come across vulnerabilities in systems that do not belong to Ivy Cyber, we urge you to report them to the relevant owner, vendor, or appropriate authority. It is crucial to refrain from engaging in activities such as Denial-of-Service (DoS), actively exploiting networks, or making any physical or electronic attempts against property and/or data centers.

## <a name="disclosure">Disclosure</a>

Please report any **non-sensitive issue unrelated to security or privacy** to [help@privacysafe.net](help@privacysafe.net) and provide all relevant information ([Verify PGP/GPG](https://keys.openpgp.org/search?q=help%40privacysafe.net)).

```
help@privacysafe.net
PGP fingerprint = 7702 BD22 435B 5F3E B00C 1E78 21FB 9DF4 D742 422D

If pasting GPG encrypted data, use paste.debian.net or paste.ubuntu.com
as these do not introduce issues with Tor via Cloudflare.
```

### <a name="security-issues">Security Issues</a>

We ask that you disclose security issues such as vulnerabilities, exploits, and data breaches in a confidential and professional manner. We value reports submitted by experts and amateurs alike and thank you in advance for your commitment to responsible disclosure and non-destructive behavior.

#### <a name="official-channels">Official Channels</a>

Please report security issues to [security@privacysafe.net](security@privacysafe.net) and provide all relevant information ([Verify PGP/GPG](https://keys.openpgp.org/search?q=security%40privacysafe.net)).

```
security@privacysafe.net
PGP fingerprint = 7E3E C7D6 D965 CF1D 8C76 8F80 74AB DBE3 E3FB C689

If pasting GPG encrypted data, use paste.debian.net or paste.ubuntu.com
as these do not introduce issues with Tor via Cloudflare.
```

Before submission, please read through our Open Bug Bounty information: 
[https://openbugbounty.org/bugbounty/privacysafe](https://www.openbugbounty.org/bugbounty/privacysafe/)

**Security Reports must include:**

* A description of the issue;
* A proof-of-concept (PoC) or steps you took to create the issue; and
* Screenshots and/or a video demonstration.

**Whenever possible, please include:**

* Affected software versions; and
* If known, mitigations for the issue.

Our organization follows a **90 day disclosure timeline** as described in this policy. To help us address and resolve the issue, please provide as much detail as possible.

## <a name="our-commitments">Our Commitments</a>

When disclosing a security issue according to this policy, you can expect us to:

* Respond to your report promptly, and work with you to understand and validate your report;
* Let you know if your report qualifies for a bounty reward within five business days;
* Strive to keep you informed about the progress of a vulnerability as it is processed;
* Work to remediate discovered vulnerabilities in a timely manner, within our operational constraints; and 
* Extend [Safe Harbor](#safe-harbor) for your vulnerability research that is related to this policy.

If your report qualifies for a bounty reward, we will:

* Set a risk level of severity and the reward size within five business days;
* Resolve qualifying vulnerabilities within 90 days (1 day for critical, 1-2 weeks for high, 4-8 weeks for medium, and 90 days for low issues);
* Notify you once an issue has been resolved; and 
* Provide a time window for the lifting of restrictions around public disclosure.

## <a name="our-expectations">Our Expectations</a>

When disclosing a security issue, we ask that you:

* Play by the rules, including following this policy and any other relevant agreements. If there is any inconsistency between this policy and any other applicable terms, the terms of this policy will prevail;
* Report any vulnerability you’ve discovered promptly and in good faith;
* Avoid violating the privacy of others, disrupting our systems, destroying data, and/or harming user experience;
* Use only the [Official Channels](#official-channels) to discuss vulnerability information with us;
* Provide us a reasonable amount of time (**at least 90 days** from the initial report) to resolve the issue before you disclose it publicly;
* Perform testing only on in-scope systems, and respect systems and activities which are [Out of Scope](#out-of-scope);
* You should only interact with test accounts you own or with explicit permission from the account holder; and 
* Do not engage in extortion.

If a vulnerability provides unintended access to data, we ask that you:

* Limit the amount of data you access to the minimum required for effectively demonstrating a proof-of-concept (PoC); and 
* Cease testing and submit a report immediately if you encounter any user data during testing, such as Personally Identifiable Information (PII), Personal Healthcare Information (PHI), credit card data, or proprietary information.

## <a name="safe-harbor">Safe Harbor</a>

We consider research conducted under this policy to be:

* Authorized concerning any applicable anti-hacking laws, and we will not initiate or support legal action against you for accidental, good-faith violations of this policy;

* Authorized concerning any relevant anti-circumvention laws, and we will not bring a claim against you for circumvention of technology controls;

* Exempt from restrictions in our terms of service and/or usage policies that would interfere with conducting security research, and we waive those restrictions on a limited basis; and

* Lawful, helpful to the overall security of the Internet, and conducted in good faith.

You are expected, as always, to comply with all applicable laws. If legal action is initiated by a third party against you and you have complied with this policy, we will take steps to make it known that your actions were conducted in compliance with this policy.

If at any time you have concerns or are uncertain whether your security research is consistent with this policy, please submit a report through one of our [Official Channels](#official-channels) before going any further.

* **IMPORTANT:** Please note that Safe Harbor applies only to legal claims under the control of the organization participating in this policy, and that the policy does not bind independent third parties.

## <a name="bounty-rewards">Bounty Rewards</a>

Rewards depend on severity and will be guided by the rules in this policy. Monetary rewards are payable in USD or an equivalent amount in cryptocurrency. If you prefer, you may elect to have your reward donated to a registered charity of your choice that accepts online donations, subject to approval of the charity.

### Reward Scale

* **Critical:** Up to $500 USD or equivalent in cryptocurrency
* **High:** Up to $250 USD or equivalent in cryptocurrency
* **Low or Medium:** Merchandise, digital rewards, social media shout-outs, recommendations, and kudos

Please allow up to one week from the time the report was approved and validated for your bounty reward to be distributed.

### <a name="eligibility">Eligibility</a>
The following requirements must be adhered to in order for any report to qualify for a bounty reward. Not following these requirements can result in your report being rejected or the banning of your further submissions.

* **Report format:** For any report to be considered, you must provide clear instructions on how to reproduce the issue, as well as how it could be exploited (i.e., attack scenario), and what you think the security impact is. This information helps us assess eligibility and appropriate bounty reward.

* **First come, first served:** Only the first person to identify a particular vulnerability will qualify for a bounty reward. Any additional reports will be considered as duplicates and will not qualify.

* **Play it safe:** All testing must be performed on test accounts under your control. Any attacks against other users without provable express consent are not allowed and may result in a ban. If a particular issue is severe enough that a proof-of-concept (PoC) in itself may expose sensitive data (e.g., data of other users), please ask us for help first so we can work together on how to safely demonstrate the bug.

* **Don't disclose too early:** To protect our users, please keep all identified vulnerability details between you and us until we've had a chance to fix the issue. This includes things like posting an obscured video of an issue on social media prior to confirmation of a deployed fix. Though you may think you have concealed critical details, doing so at minimum alerts potentially malicious actors that an issue exists and at worst unintentionally creates early disclosure. Public disclosure prior to us notifying you of the fix may result in a ban. If you have questions regarding the remediation timeline, please inquire on the relevant report.

* **No social engineering:** Bugs that require social engineering to exploit (e.g., tricking someone into clicking a link) may qualify, but please do not actually attempt to socially engineer our customers and users, our team members, FOSS contributors, etc. during your testing. Providing a clear explanation of how social engineering could be used in conjunction with an identified vulnerability is sufficient.

### <a name="commonplace-reports">Commonplace Reports</a>

In addition to the areas defined as [Out of Scope](#out-of-scope) in this policy, the following commonplace reports do not qualify for a bounty reward. Such issues may be disclosed as a git issue at [https://github.com/privacysafe](https://github.com/privacysafe) or [https://gitlab.com/privacysafe](https://gitlab.com/privacysafe) instead.

* Lack of a security feature that is not critical to the system's operation
* Configuration issues that are not relevant to the network or application
* Application Denial-of-Service (DoS) by locking user accounts
* Descriptive error messages or headers (e.g., stack traces, banner grabbing, debug information on a production site)
* Purely technical, public, and non-sensitive network, application, or API information unrelated to a specific exploit
* Disclosure of known public files or directories, (e.g., `robots.txt`)
* Outdated software/library versions
* Lack of security headers, such as the `X-Content-Type-Options` or `X-Frame-Options` headers
* OPTIONS/TRACE HTTP method enabled
* Subdomain takeover, such as a subdomain pointing to a service that is no longer in use
* DNS Zone transfer and configuration issues
* DNSSEC configuration issues
* CSRF on logout
* CSRF on forms that are available to anonymous users
* Cookies with missing or incomplete flags such as `HTTP Only` or `Secure`
* Self-XSS and issues exploitable only through Self-XSS
* XSS that does not allow for the execution of arbitrary code, such as reflected or non-persistent XSS
* Reports resulting from automated scanning utilities without additional details or a PoC demonstrating a specific exploit
* Attacks requiring physical access to a user’s device
* Attacks dependent upon social engineering of our customers and users, our team members, and FOSS contributors
* Username enumeration based on login or "forgot password" pages
* Enforcement policies for brute force, rate limiting, or account lockout
* SSL/TLS best practices
* SSL/TLS attacks such as BEAST, BREACH, Renegotiation attack
* Clickjacking, without additional details demonstrating a specific exploit
* XML-RPC mirroring or reflection without associated exploitation, such as code execution, authentication bypass, or sensitive data leakage
* Mail configuration issues including SPF, DKIM, DMARC settings
* Use of a known-vulnerable library without a description of an exploit specific to our implementation
* Password and account recovery policies
* Presence of autocomplete functionality in form fields
* Publicly-accessible login panels
* Lack of email address verification during account registration or account invitation
* Lack of email address verification password restore
* Session control during email/password changes
