# DVSA Vulnerability Discovery and Remediation Project

## Course Information

* **Course:** ICS-344 Information Security
* **Institution:** King Fahd University of Petroleum and Minerals (KFUPM)
* **Term:** 252

## Project Overview

This project documents the discovery, exploitation, analysis, remediation, and verification of security vulnerabilities in the **OWASP Damn Vulnerable Serverless Application (DVSA)**. The application was deployed in a controlled AWS environment for educational purposes only.

The goal of this work is to study real security weaknesses in a serverless architecture and demonstrate how they can be identified, exploited safely in a lab setting, fixed correctly, and verified after remediation.

## Serverless Architecture Context

DVSA is a serverless cloud application deployed on AWS. Its architecture includes:

* **Frontend:** Amazon S3-hosted static website
* **API Layer:** Amazon API Gateway
* **Backend Logic:** AWS Lambda
* **Data Layer:** Amazon DynamoDB
* **Supporting Services:** IAM, S3, CloudWatch, and related AWS resources

## Assigned Vulnerabilities

This repository section focuses on the following assigned vulnerabilities:

* **Vulnerability #2:** Broken Authentication
* **Vulnerability #5:** Broken Access Control
* **Vulnerability #8:** Logic Vulnerabilities

## Repository Structure

```text
README.md
vulnerability-2-broken-authentication/
vulnerability-5-broken-access-control/
vulnerability-8-logic-vulnerabilities/
```

Each vulnerability folder contains:

* `README.md`  full write-up for the vulnerability
* `screenshots/`  screenshots used as visual proof
* `exploit/`  payloads, commands, and reproduction artifacts
* `fix/`  remediation details and code/configuration changes
* `evidence/`  proof before and after remediation

## Documentation Method

For each assigned vulnerability, the documentation follows a consistent structure:

1. Goal and vulnerability summary
2. Root cause
3. Environment and setup
4. Reproduction steps
5. Evidence and proof
6. Fix strategy
7. Code or configuration changes
8. Verification after fix
9. Security analysis
10. Lessons learned

## Ethical Use Notice

DVSA is intentionally vulnerable and must only be used in a **non-production AWS environment** for legal educational purposes. This repository is part of an academic course project and must not be used for malicious activity.
