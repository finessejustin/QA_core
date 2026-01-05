# Bug Bounty Program - Complete Template

## Table of Contents
1. Program Overview
2. Scope & Assets
3. Vulnerability Severity & Rewards
4. Rules of Engagement
5. Submission Guidelines
6. Response & Resolution Process
7. Legal Safe Harbor
8. Hall of Fame & Recognition

---

## 1. Program Overview

### Mission Statement
Our bug bounty program is designed to work with the security research community to identify and resolve security vulnerabilities in our systems. We believe in rewarding researchers who help us maintain the highest security standards for our users.

### Program Type
**Public Program** - Open to all security researchers worldwide

### Program Goals
- Identify security vulnerabilities before malicious actors can exploit them
- Build relationships with the global security research community
- Continuously improve our security posture
- Protect our users' data and privacy

### Contact Information
- **Security Team Email:** security@company.com
- **PGP Key:** [Link to public PGP key]
- **Program Platform:** [HackerOne/Bugcrowd/Intigriti/Self-hosted]
- **Response Time:** We commit to initial response within 2 business days

---

## 2. Scope & Assets

### 2.1 In-Scope Assets

#### Web Applications
- **Primary Domain:** `*.company.com`
- **API Endpoints:** `api.company.com/*`
- **Admin Portal:** `admin.company.com`
- **Customer Portal:** `portal.company.com`
- **Developer Documentation:** `docs.company.com`

#### Mobile Applications
- **iOS App:** [App Store Link]
  - Version: 2.0 and above
  - Bundle ID: com.company.mobile
- **Android App:** [Play Store Link]
  - Version: 2.0 and above
  - Package Name: com.company.android

#### API Infrastructure
- **REST API:** `api.company.com/v1/*`, `api.company.com/v2/*`
- **GraphQL API:** `graphql.company.com`
- **Webhooks:** `webhooks.company.com`

#### Cloud Infrastructure
- **AWS Resources:** Publicly accessible S3 buckets, CloudFront distributions
- **CDN:** `cdn.company.com`
- **Static Assets:** `static.company.com`

#### Desktop Applications
- **Windows Client:** Version 3.0+
- **macOS Client:** Version 3.0+
- **Linux Client:** Version 3.0+

### 2.2 Out-of-Scope Assets
The following are explicitly **OUT OF SCOPE**:
- `test.company.com` (testing environment)
- `legacy.company.com` (deprecated system scheduled for decommission)
- Third-party services we use (report directly to those vendors)
- Physical security of our offices
- Social engineering attacks against our employees
- Any domain not explicitly listed above

### 2.3 Test Accounts
To facilitate testing, we provide the following:
- **Test Account Credentials:** Available upon request to verified researchers
- **Sandbox Environment:** `sandbox.company.com` - Feel free to test destructive actions here
- **API Keys:** Limited-scope test API keys available on request

---

## 3. Vulnerability Severity & Rewards

### 3.1 Severity Ratings
We use the CVSS 3.1 scoring system as a baseline, combined with business impact assessment.

### 3.2 Reward Structure

#### Critical Vulnerabilities ($5,000 - $20,000)
**Examples:**
- Remote Code Execution (RCE)
- SQL Injection leading to data breach
- Authentication bypass affecting all users
- Arbitrary file upload leading to RCE
- Critical vulnerabilities in payment processing
- Full account takeover via authentication flaws
- Direct access to production database
- Server-Side Request Forgery (SSRF) with cloud metadata access

**Monetary Reward:** $5,000 - $20,000
**Recognition:** Hall of Fame, LinkedIn recommendation, company swag, annual top researcher awards

---

#### High Vulnerabilities ($2,000 - $5,000)
**Examples:**
- Stored Cross-Site Scripting (XSS) in critical contexts
- Authentication bypass for specific user roles
- Insecure Direct Object Reference (IDOR) exposing sensitive data
- XML External Entity (XXE) injection
- Server-Side Request Forgery (SSRF) without metadata access
- Privilege escalation (vertical or horizontal)
- Sensitive data exposure through API
- Bypass of security controls or rate limiting
- Critical subdomain takeover

**Monetary Reward:** $2,000 - $5,000
**Recognition:** Hall of Fame, company swag, quarterly recognition

---

#### Medium Vulnerabilities ($500 - $2,000)
**Examples:**
- Reflected XSS in moderate impact contexts
- CSRF on sensitive actions
- Business logic flaws with moderate impact
- Information disclosure revealing internal architecture
- Subdomain takeover (non-critical)
- Missing security headers with demonstrable impact
- Open redirect with security impact
- Session fixation vulnerabilities
- Insecure password reset mechanisms
- Moderate IDOR issues

**Monetary Reward:** $500 - $2,000
**Recognition:** Hall of Fame, company swag

---

#### Low Vulnerabilities ($100 - $500)
**Examples:**
- Self-XSS with demonstrated social engineering potential
- Minor information disclosure
- Clickjacking on non-sensitive pages
- Missing best practices with minimal security impact
- Descriptive error messages
- Email verification bypass
- Content injection without XSS
- HTTP parameter pollution
- Autocomplete enabled on sensitive forms

**Monetary Reward:** $100 - $500
**Recognition:** Hall of Fame mention

---

### 3.3 Bonus Multipliers
We may increase rewards based on:
- **Quality of Report:** Clear reproduction steps, video proof-of-concept (+25%)
- **Fix Suggestions:** Providing specific remediation code or suggestions (+15%)
- **Impact Demonstration:** Showing real-world impact beyond proof-of-concept (+20%)
- **First Reporter:** Being the first to report a particular vulnerability (+10%)
- **Chained Exploits:** Combining multiple vulnerabilities for greater impact (up to +50%)

### 3.4 Non-Monetary Recognition
All valid submissions receive:
- Public acknowledgment in our Hall of Fame (if desired)
- Contribution to your researcher profile statistics
- Certificate of appreciation for significant findings
- Exclusive company merchandise
- Priority access to new features/beta programs
- Annual awards for top contributors:
  - **Top Researcher Award:** $5,000 bonus + invitation to company security summit
  - **Most Impactful Find:** $3,000 bonus
  - **Community Champion:** $2,000 bonus

---

## 4. Rules of Engagement

### 4.1 Testing Guidelines

**DO:**
- Test only against in-scope assets
- Use provided test accounts whenever possible
- Stop testing if you discover sensitive user data and report immediately
- Make a good faith effort to avoid privacy violations and data destruction
- Keep your findings confidential until we've resolved the issue
- Provide detailed reproduction steps
- Communicate clearly and professionally

**DO NOT:**
- Access, modify, or delete other users' data
- Perform Denial of Service (DoS) or Distributed Denial of Service (DDoS) attacks
- Execute social engineering attacks against our employees or users
- Send unsolicited emails or make unsolicited phone calls
- Test physical security of our facilities
- Perform automated testing that generates excessive load (more than 10 requests/second)
- Use scanners or automated tools without careful rate limiting
- Test third-party applications or services that integrate with us
- Publicly disclose vulnerabilities before they're resolved
- Exploit vulnerabilities beyond the minimum necessary to prove they exist

### 4.2 Rate Limiting & Testing Volume
- API testing: Maximum 10 requests per second
- Web application testing: Reasonable human-like traffic patterns
- Automated scanning: Must be carefully rate-limited and monitored
- If you need higher limits for specific testing, contact us first

### 4.3 Proof of Concept Requirements
Your proof of concept should:
- Demonstrate the vulnerability clearly
- Use non-destructive methods whenever possible
- Not access more than 5 records/accounts to prove IDOR or similar issues
- Stop testing once the vulnerability is confirmed
- Include screenshots, videos, or step-by-step reproduction instructions

### 4.4 Responsible Disclosure
- Submit vulnerabilities only through official channels
- Allow us reasonable time to fix issues (typically 90 days)
- Do not disclose to third parties or the public before resolution
- Coordinate public disclosure timing with our security team
- We commit to providing regular updates on remediation progress

---

## 5. Submission Guidelines

### 5.1 How to Submit

**Preferred Method:** Submit through our program platform at [platform link]

**Alternative Methods:**
- Email: security@company.com (use PGP encryption for sensitive findings)
- Anonymous Submission: Accepted, but may limit reward eligibility

### 5.2 Required Information

Your report should include:
1. **Vulnerability Summary:** Brief description of the issue
2. **Severity Assessment:** Your evaluation of the severity
3. **Affected Asset:** Specific URL, API endpoint, or application
4. **Reproduction Steps:** Detailed, step-by-step instructions
5. **Proof of Concept:** Screenshots, videos, or code demonstrating the issue
6. **Impact:** Explanation of what an attacker could achieve
7. **Suggested Fix:** (Optional but appreciated) Remediation recommendations
8. **Discovery Details:** Tools and techniques used
9. **Your Environment:** Browser version, OS, testing tools used

### 5.3 Report Quality Guidelines

**Good Report Example:**
```
Title: SQL Injection in User Search API

Severity: Critical

Asset: https://api.company.com/v2/users/search

Description:
The user search endpoint is vulnerable to SQL injection through the 
'query' parameter, allowing unauthorized access to the entire user database.

Reproduction Steps:
1. Send POST request to https://api.company.com/v2/users/search
2. Include the following payload in 'query' parameter: ' OR '1'='1
3. Observe that all user records are returned without authentication

Proof of Concept:
curl -X POST https://api.company.com/v2/users/search \
  -H "Content-Type: application/json" \
  -d '{"query": "' OR '1'='1"}'

Impact:
An attacker can extract all user data from the database including emails,
hashed passwords, and personal information. This affects all 500,000+ users.

Suggested Fix:
Use parameterized queries or an ORM. Example:
cursor.execute("SELECT * FROM users WHERE name = %s", (query,))

[Screenshot attached showing database dump]
```

### 5.4 What We Don't Accept

The following will be marked as informative or not applicable:
- Vulnerabilities in out-of-scope assets
- Issues requiring unlikely user interaction
- Reports from automated scanners without validation
- Theoretical vulnerabilities without proof of concept
- Issues that require physical access to a user's device
- Software version disclosure without demonstrated impact
- Presence of banner grabbing information
- Open ports without demonstrated vulnerability
- SSL/TLS configuration issues that don't lead to exploitable weaknesses (unless severe)
- Missing cookie flags without demonstrated impact
- Lack of CSRF tokens on non-state-changing operations
- Logout CSRF
- Self-XSS without demonstrable social engineering vector
- Denial of Service requiring excessive bandwidth or resources
- Previously known issues or duplicates
- Issues in third-party libraries without proof they're exploitable in our context

---

## 6. Response & Resolution Process

### 6.1 Timeline Commitments

- **Initial Response:** Within 2 business days
- **Triage & Validation:** Within 5 business days
- **Severity Assessment:** Within 7 business days
- **Resolution Timeline:**
  - Critical: 14 days
  - High: 30 days
  - Medium: 60 days
  - Low: 90 days
- **Reward Payment:** Within 15 days of resolution

### 6.2 Process Flow

1. **Submission:** You submit a vulnerability report
2. **Acknowledgment:** We acknowledge receipt within 2 business days
3. **Validation:** Our team reproduces and validates the issue
4. **Severity Assessment:** We assign severity and bounty amount
5. **Discussion:** We may request additional information or clarification
6. **Remediation:** Our development team works on a fix
7. **Verification:** We notify you when the fix is deployed
8. **Reward:** We process your payment
9. **Disclosure:** Coordinated public disclosure (if desired)

### 6.3 Communication

We will:
- Provide regular updates on progress
- Explain our severity assessment if it differs from yours
- Be respectful and professional in all communications
- Credit you in security advisories (unless you prefer to remain anonymous)
- Work with you on coordinated disclosure timing

### 6.4 Dispute Resolution

If you disagree with our assessment:
1. Provide additional evidence or context
2. Request a second review by our senior security team
3. We'll schedule a call to discuss if needed
4. Final decisions are made by our Chief Security Officer

---

## 7. Legal Safe Harbor

### 7.1 Legal Protections

We commit to the following:
- We will not pursue legal action against researchers who discover and report vulnerabilities in good faith according to this policy
- We will not initiate legal action for accidental violations if you immediately stop and report
- We consider security research activities conducted consistent with this policy to be:
  - "Authorized" under the Computer Fraud and Abuse Act (CFAA)
  - Exempt from the Digital Millennium Copyright Act (DMCA)
  - Exempt from our Terms of Service
  - Lawful and helpful to our security

### 7.2 Conditions

This safe harbor applies if you:
- Follow all rules outlined in this program
- Do not cause harm to our systems or users
- Do not access or modify data beyond what's necessary to demonstrate the vulnerability
- Report findings promptly and keep them confidential
- Act in good faith

### 7.3 Third Party Services

If you discover vulnerabilities in third-party services we use:
- We cannot provide legal authorization for testing those services
- Please report those to the respective vendor's security team
- You may inform us, but the vulnerability is not eligible for our bounty

---

## 8. Hall of Fame & Recognition

### 8.1 Public Recognition

Our Hall of Fame recognizes researchers who have contributed to our security. It includes:
- Researcher name or handle (with your permission)
- Number of valid vulnerabilities found
- Highest severity finding
- Total bounty earned (optional)
- Special achievements or awards

**View our Hall of Fame:** [Link to hall of fame page]

### 8.2 Annual Awards

Each year we recognize:
- **Researcher of the Year:** Highest impact contributor
- **Rising Star:** Most promising new researcher
- **Community Champion:** Best collaboration and communication
- **Critical Find Award:** Most impactful single vulnerability

### 8.3 Special Recognition

For exceptional contributions:
- LinkedIn recommendations from our CISO
- Speaking opportunities at company events
- Security research internship opportunities
- Invitations to private invite-only programs
- Early access to new products and features

---

## 9. Frequently Asked Questions

### Can I test without an account?
Yes, but some vulnerabilities require authentication to access. Request test accounts for more comprehensive testing.

### What if I find a duplicate?
First valid reporter receives the full bounty. Duplicates receive recognition but no monetary reward.

### Can I use automated scanners?
Yes, but with rate limiting and manual validation. Reports from unvalidated scanner output will be rejected.

### Do you accept reports anonymously?
Yes, but payment may require identity verification depending on amount and local regulations.

### What if I accidentally cause damage?
Stop immediately, report what happened, and we'll work with you. Accidents during good-faith testing are covered by our safe harbor.

### Can I discuss my findings publicly?
Not until we've resolved the issue and agreed on disclosure timing. Typically 90 days or upon fix deployment.

### How do I receive payment?
We support: PayPal, bank transfer, cryptocurrency (Bitcoin, Ethereum), and program platform credits.

### What if I disagree with the severity assessment?
Provide additional context and request a review. We're open to discussion and re-evaluation.

---

## 10. Program Updates

This program policy may be updated periodically. Changes will be:
- Posted on this page with a revision date
- Announced via our security mailing list
- Non-retroactive (submissions are judged by rules at time of submission)

**Last Updated:** January 5, 2026  
**Version:** 2.1

---

## Contact & Support

- **General Inquiries:** bugbounty@company.com
- **Security Team:** security@company.com
- **PGP Key:** [Link]
- **Program Manager:** [Name & Contact]
- **Platform:** [Link to platform]

---

## Acknowledgments

We'd like to thank all the researchers who have contributed to making our platform more secure. Your work helps protect millions of users and makes the internet a safer place.

**Thank you for helping us stay secure!**