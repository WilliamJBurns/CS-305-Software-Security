# CS 305: Software Security

## Artemis Financial Vulnerability Assessment

This repository contains my completed vulnerability assessment report for CS 305: Software Security at Southern New Hampshire University. The report documents a manual code review, an automated dependency analysis, and a recommended mitigation plan for the Artemis Financial application.

**Project artifact:** [Artemis Financial Vulnerability Assessment Report](./CS%20305%20Project%20One%20-%20William%20Burns.docx)

## Portfolio Reflection

### 1. Client and Software Requirements

Artemis Financial is a financial-services company that provides customized planning for savings, retirement, investments, and insurance. The client wanted to evaluate the security of its web-based application as part of a modernization effort. The application uses Java and Spring Boot to provide REST API functionality and includes database connectivity. Because it may handle sensitive financial information, protecting communications, controlling access, and identifying weaknesses in application code and third-party libraries were central requirements. My role was to assess the existing software and recommend ways to reduce its security risks.

### 2. Identifying Vulnerabilities and the Value of Secure Coding

I approached the assessment systematically by examining seven security areas: input validation, APIs, cryptography, client/server interactions, code errors, code quality, and encapsulation. Through manual inspection, I documented ten concerns, including hardcoded database credentials, excessive database privileges, missing visible access controls, and insufficient input validation. I also used OWASP Dependency-Check to assess the application's dependencies. The scan reviewed 38 dependencies (20 unique components) and reported 252 vulnerability entries across 11 vulnerable dependencies. Combining these methods helped me identify issues in both the application's own code and the libraries it relies on.

Secure coding matters because a single weakness can expose sensitive information, allow unauthorized changes, or interrupt service. For a financial-services company, good security practices help protect customer information, maintain trust, and reduce operational and reputational risk.

### 3. Challenges and Lessons from the Assessment

One of the most challenging parts was interpreting the dependency scan and deciding how to prioritize a large number of reported findings. Automated results require context: a reported vulnerability does not automatically prove that an application can be exploited in its particular configuration. Manual review was equally important for finding application-specific problems that dependency scanning would not detect. For example, I identified missing request validation without incorrectly labeling it as SQL injection when the reviewed input was not used in an SQL statement. This reinforced the importance of explaining what the code actually does rather than assuming every potential risk is an exploitable vulnerability.

### 4. Security Layers and Future Mitigation Decisions

In my mitigation plan, I recommended multiple layers of protection: HTTPS/TLS for communications, authentication and authorization for sensitive API operations, protected storage for credentials, least-privilege database access, stronger input validation, safer exception handling, and more restrictive upload limits. I also recommended upgrading outdated Spring Boot, Spring Framework, Tomcat, and other dependencies to supported versions. These are proposed improvements documented in my report, not changes I implemented in Project One.

For future assessments, I would combine manual code review with automated dependency scanning, CVE records, vendor advisories, and tests. I would prioritize fixes according to severity, potential exploitability, exposure, and business impact, then confirm that updates do not introduce compatibility or security regressions.

### 5. Verifying Functionality and Security

Project One focused on identifying vulnerabilities and recommending remediation rather than refactoring the application, so I did not perform or document post-refactoring validation in this project. I evaluated security through source-code inspection and an OWASP Dependency-Check report. After implementing the proposed fixes in a future development phase, I would run unit, integration, and API tests to verify expected functionality; test relevant access controls and HTTPS configuration; review the modified code; and rerun Dependency-Check to verify that vulnerable versions were no longer present. Any remaining scan results would need further investigation rather than being assumed resolved.

### 6. Useful Tools, Resources, and Practices

The most useful tools and resources were Java source-code review, Maven, OWASP Dependency-Check 12.2.2, and the vulnerability information referenced in the scan, including CVE records and vendor advisories. I also relied on practices such as least-privilege access, defense in depth, secure credential handling, input validation, careful error handling, and dependency maintenance. These are approaches I can apply to future software development and security reviews.

### 7. What This Project Demonstrates to Employers

I would share this vulnerability assessment report to demonstrate that I can inspect an existing codebase, recognize security risks, interpret automated testing results, and explain concrete remediation steps. The report includes ten manual findings, a review of vulnerable third-party dependencies, and a detailed mitigation plan. It shows my ability to connect technical weaknesses to real-world risks and communicate recommended improvements in a structured, professional document.
