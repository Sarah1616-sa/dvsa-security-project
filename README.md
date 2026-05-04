# DVSA Security Project — ICS344

This repository contains the completed DVSA security project for ICS344.  
The project documents ten vulnerabilities found in the DVSA application, including vulnerability analysis, reproduction steps, evidence screenshots, fixes, verification after fixes, presentation slides, and demonstration videos.

## GitHub Repository

Repository URL:

```text
https://github.com/Sarah1616-sa/dvsa-security-project.git
```

## Project Overview

The goal of this project is to analyze, exploit, fix, and verify multiple vulnerabilities in the DVSA application.

Each vulnerability includes:

- Vulnerability description
- Root cause analysis
- Environment and setup
- Reproduction steps
- Evidence and proof
- Fix strategy
- Code/configuration changes
- Verification after fix
- Structured security analysis
- Lessons learned

## Repository Structure

```text
dvsa-security-project/
│
├── .gitattributes
├── README.md
│
├── fixes/
│   ├── Vulnerability-1-Event Injection
│   ├── Vulnerability-2-broken-authentication
│   ├── Vulnerability-3-Sensitive Information Disclosure
│   ├── Vulnerability-4- Insecure Cloud Configuration
│   ├── Vulnerability-5-Broken Access-Control.py
│   ├── Vulnerability-6- Denial of Service (DoS)
│   ├── Vulnerability-7-Over-Privileged Function
│   ├── Vulnerability-8-Logic-Renabilities.py
│   ├── Vulnerability-9-Vulnerable Dependencies
│   └── Vulnerability-10- Unhandled Exceptions
│
├── report/
│   ├── Vulnerability-1-Event Injection
│   ├── Vulnerability-2-broken-authentication Report
│   ├── Vulnerability-3-Sensitive Information Disclosure
│   ├── Vulnerability-4-Insecure Cloud Configuration
│   ├── Vulnerability-5-Broken Access-Control Report
│   ├── Vulnerability-6-Denial of Service (Billing Endpoint Exhaustion)
│   ├── Vulnerability-7-Over-Privileged Function
│   ├── Vulnerability-8-Logic-Renabilities Report.md
│   ├── Vulnerability-9-Vulnerable Dependencies (node-serialize)
│   └── Vulnerability-10-Unhandled Exceptions
│
├── screenshots/
│   └── Evidence screenshots for V1–V10
│
├── slides/
│   └── ICS344_project.pdf
│
└── video/
    ├── V1.mp4
    ├── V10.mp4
    ├── v2befor-fixe.mp4
    ├── v2-after-fixe.mp4
    ├── V4.mp4
    ├── v5-befor fixe.mp4
    ├── v5-after-fixe.mp4
    ├── v6.mp4
    ├── v7.mp4
    ├── v8-befor-fixe.mp4
    ├── v8-after-fix.mp4
    └── v9.mp4
```

## Completed Vulnerabilities

| # | Vulnerability | Report | Fix / Evidence File | Demo Video |
|---|---|---|---|---|
| V1 | Event Injection / Code Injection via API Gateway | `report/Vulnerability-1-Event Injection` | `fixes/Vulnerability-1-Event Injection` | [`video/V1.mp4`](video/V1.mp4) |
| V2 | Broken Authentication | `report/Vulnerability-2-broken-authentication Report` | `fixes/Vulnerability-2-broken-authentication` | [`video/v2befor-fixe.mp4`](video/v2befor-fixe.mp4), [`video/v2-after-fixe.mp4`](video/v2-after-fixe.mp4) |
| V3 | Sensitive Information Disclosure | `report/Vulnerability-3-Sensitive Information Disclosure` | `fixes/Vulnerability-3-Sensitive Information Disclosure` | Evidence screenshots included |
| V4 | Insecure Cloud Configuration | `report/Vulnerability-4-Insecure Cloud Configuration` | `fixes/Vulnerability-4- Insecure Cloud Configuration` | [`video/V4.mp4`](video/V4.mp4) |
| V5 | Broken Access Control | `report/Vulnerability-5-Broken Access-Control Report` | `fixes/Vulnerability-5-Broken Access-Control.py` | [`video/v5-befor fixe.mp4`](video/v5-befor%20fixe.mp4), [`video/v5-after-fixe.mp4`](video/v5-after-fixe.mp4) |
| V6 | Denial of Service / Billing Endpoint Exhaustion | `report/Vulnerability-6-Denial of Service (Billing Endpoint Exhaustion)` | `fixes/Vulnerability-6- Denial of Service (DoS)` | [`video/v6.mp4`](video/v6.mp4) |
| V7 | Over-Privileged Function | `report/Vulnerability-7-Over-Privileged Function` | `fixes/Vulnerability-7-Over-Privileged Function` | [`video/v7.mp4`](video/v7.mp4) |
| V8 | Logic Vulnerability | `report/Vulnerability-8-Logic-Renabilities Report.md` | `fixes/Vulnerability-8-Logic-Renabilities.py` | [`video/v8-befor-fixe.mp4`](video/v8-befor-fixe.mp4), [`video/v8-after-fix.mp4`](video/v8-after-fix.mp4) |
| V9 | Vulnerable Dependencies / node-serialize | `report/Vulnerability-9-Vulnerable Dependencies (node-serialize)` | `fixes/Vulnerability-9-Vulnerable Dependencies` | [`video/v9.mp4`](video/v9.mp4) |
| V10 | Unhandled Exceptions | `report/Vulnerability-10-Unhandled Exceptions` | `fixes/Vulnerability-10- Unhandled Exceptions` | [`video/V10.mp4`](video/V10.mp4) |

## Report Structure

Each report follows the required vulnerability report structure:

1. Goal and Vulnerability Summary
2. Why This Works / Root Cause
3. Environment and Setup
4. Reproduction Steps
5. Evidence and Proof
6. Fix Strategy / Probable Mitigation
7. Code / Config Changes
8. Verification After Fix
9. Structured Operation and Security Analysis
10. Takeaway / Lessons Learned

## Vulnerability Summary

### V1 — Event Injection / Code Injection via API Gateway

This vulnerability involves unsafe handling of input through API Gateway and backend logic.  
The report documents the injection behavior, proof of exploit, applied fix, and after-fix verification.

Related files:

- Report: `report/Vulnerability-1-Event Injection`
- Fix/evidence: `fixes/Vulnerability-1-Event Injection`
- Demo video: [`video/V1.mp4`](video/V1.mp4)

---

### V2 — Broken Authentication

This vulnerability affects the DVSA `/order` API authentication flow.  
The backend trusted decoded JWT payload claims without properly verifying the token signature.  
This allowed a normal user to modify JWT claims and impersonate another user.

Fix summary:

- Enabled Cognito authorizer on the API Gateway `/order` POST method.
- Rejected forged JWT tokens before they reached the backend Lambda function.
- Verified that valid user tokens still worked normally.

Related files:

- Report: `report/Vulnerability-2-broken-authentication Report`
- Fix/evidence: `fixes/Vulnerability-2-broken-authentication`
- Before-fix video: [`video/v2befor-fixe.mp4`](video/v2befor-fixe.mp4)
- After-fix video: [`video/v2-after-fixe.mp4`](video/v2-after-fixe.mp4)

---

### V3 — Sensitive Information Disclosure

This vulnerability involves exposure of sensitive information through application responses, code, logs, or configuration.  
The report includes before-fix evidence, the fix strategy, and after-fix verification.

Related files:

- Report: `report/Vulnerability-3-Sensitive Information Disclosure`
- Fix/evidence: `fixes/Vulnerability-3-Sensitive Information Disclosure`
- Screenshots: `screenshots/`

---

### V4 — Insecure Cloud Configuration

This vulnerability involves insecure cloud configuration that allowed unintended or unauthorized behavior.  
The report includes cloud configuration evidence, unauthorized action proof, and after-fix verification.

Related files:

- Report: `report/Vulnerability-4-Insecure Cloud Configuration`
- Fix/evidence: `fixes/Vulnerability-4- Insecure Cloud Configuration`
- Demo video: [`video/V4.mp4`](video/V4.mp4)

---

### V5 — Broken Access Control

This vulnerability affects privileged order workflow actions in the DVSA backend.  
A normal user could attempt to invoke a sensitive `complete` action through the public `/order` API.

Fix summary:

- Added authorization checks before allowing the `complete` action.
- Required admin authorization before invoking `DVSA-ORDER-COMPLETE`.
- Verified that normal users receive an unauthorized response while normal order viewing still works.

Related files:

- Report: `report/Vulnerability-5-Broken Access-Control Report`
- Fix/evidence: `fixes/Vulnerability-5-Broken Access-Control.py`
- Before-fix video: [`video/v5-befor fixe.mp4`](video/v5-befor%20fixe.mp4)
- After-fix video: [`video/v5-after-fixe.mp4`](video/v5-after-fixe.mp4)

---

### V6 — Denial of Service / Billing Endpoint Exhaustion

This vulnerability involves possible billing endpoint exhaustion or denial-of-service behavior.  
The report documents how the endpoint could be abused, the evidence collected, and the applied mitigation.

Related files:

- Report: `report/Vulnerability-6-Denial of Service (Billing Endpoint Exhaustion)`
- Fix/evidence: `fixes/Vulnerability-6- Denial of Service (DoS)`
- Demo video: [`video/v6.mp4`](video/v6.mp4)

---

### V7 — Over-Privileged Function

This vulnerability involves excessive permissions assigned to a function or backend component.  
The report documents the over-privilege issue, the least-privilege fix, and after-fix access verification.

Related files:

- Report: `report/Vulnerability-7-Over-Privileged Function`
- Fix/evidence: `fixes/Vulnerability-7-Over-Privileged Function`
- Demo video: [`video/v7.mp4`](video/v7.mp4)

---

### V8 — Logic Vulnerability

This vulnerability affects the DVSA order workflow.  
The application allowed unsafe order updates during or after payment because backend workflow rules were enforced too late.

Fix summary:

- Rejected shipping updates when `orderStatus >= 120`.
- Rejected cart/item updates when `orderStatus >= 120`.
- Rejected duplicate billing when `orderStatus >= 120`.
- Added DynamoDB conditional checks to prevent race-condition issues.

Related files:

- Report: `report/Vulnerability-8-Logic-Renabilities Report.md`
- Fix/evidence: `fixes/Vulnerability-8-Logic-Renabilities.py`
- Before-fix video: [`video/v8-befor-fixe.mp4`](video/v8-befor-fixe.mp4)
- After-fix video: [`video/v8-after-fix.mp4`](video/v8-after-fix.mp4)

---

### V9 — Vulnerable Dependencies / node-serialize

This vulnerability involves an insecure dependency, `node-serialize`.  
The report documents the vulnerable dependency behavior, exploit evidence, code changes, and verification after mitigation.

Related files:

- Report: `report/Vulnerability-9-Vulnerable Dependencies (node-serialize)`
- Fix/evidence: `fixes/Vulnerability-9-Vulnerable Dependencies`
- Demo video: [`video/v9.mp4`](video/v9.mp4)

---

### V10 — Unhandled Exceptions

This vulnerability involves unsafe or verbose error handling.  
The report documents stack trace/error exposure, the fix, and verification that safe error responses are returned after mitigation.

Related files:

- Report: `report/Vulnerability-10-Unhandled Exceptions`
- Fix/evidence: `fixes/Vulnerability-10- Unhandled Exceptions`
- Demo video: [`video/V10.mp4`](video/V10.mp4)

## Screenshots

The `screenshots/` folder contains evidence images for all vulnerabilities from V1 to V10.

The screenshots include:

- Before-fix vulnerability evidence
- Exploit proof
- Code/configuration evidence
- Cloud logs or API responses
- After-fix verification evidence

Screenshot groups:

| Vulnerability | Screenshot Evidence Type |
|---|---|
| V1 | Code before/after, logs, payload evidence, after-fix verification |
| V2 | JWT/authentication evidence, forged token accepted/rejected, Cognito authorizer proof |
| V3 | Sensitive data/code/payload/result evidence, before and after proof |
| V4 | Cloud configuration before/after screenshots, unauthorized upload evidence |
| V5 | Broken access control evidence, rejected action after fix, route/admin-check proof |
| V6 | DoS before/after screenshots, billing/code evidence |
| V7 | Code before/after, unauthorized action evidence, denied access verification |
| V8 | Race/workflow evidence, protected workflow after fix, DynamoDB condition proof |
| V9 | Vulnerable dependency evidence, code before/after, after-fix result |
| V10 | Stack trace evidence, code before/after, safe error verification |

## Fixes

The `fixes/` folder contains fix notes, configuration evidence, command evidence, and code snippets for each vulnerability.

Current fix files:

```text
fixes/Vulnerability-1-Event Injection
fixes/Vulnerability-2-broken-authentication
fixes/Vulnerability-3-Sensitive Information Disclosure
fixes/Vulnerability-4- Insecure Cloud Configuration
fixes/Vulnerability-5-Broken Access-Control.py
fixes/Vulnerability-6- Denial of Service (DoS)
fixes/Vulnerability-7-Over-Privileged Function
fixes/Vulnerability-8-Logic-Renabilities.py
fixes/Vulnerability-9-Vulnerable Dependencies
fixes/Vulnerability-10- Unhandled Exceptions
```

Note: Some fix files are notes or command/configuration evidence even when they do not have a file extension.  
The V5 and V8 fix files use `.py` extensions, but they may contain command/script notes as well as code evidence.

## Reports

The `report/` folder contains the final vulnerability reports.

Current report files:

```text
report/Vulnerability-1-Event Injection
report/Vulnerability-2-broken-authentication Report
report/Vulnerability-3-Sensitive Information Disclosure
report/Vulnerability-4-Insecure Cloud Configuration
report/Vulnerability-5-Broken Access-Control Report
report/Vulnerability-6-Denial of Service (Billing Endpoint Exhaustion)
report/Vulnerability-7-Over-Privileged Function
report/Vulnerability-8-Logic-Renabilities Report.md
report/Vulnerability-9-Vulnerable Dependencies (node-serialize)
report/Vulnerability-10-Unhandled Exceptions
```

## Presentation Slides

The project presentation is available as a PDF file:

- [ICS344 Project Slides PDF](slides/ICS344_project.pdf)

The current repository contains the PDF version of the slides only.  
The PowerPoint file is not currently included in the repository.

## Demo Videos

The `video/` folder contains demonstration videos for the vulnerabilities.

| File | Vulnerability | Type | Size |
|---|---|---|---:|
| [`V1.mp4`](video/V1.mp4) | V1 | General demo | 18.76 MB |
| [`V10.mp4`](video/V10.mp4) | V10 | General demo | 35.90 MB |
| [`v2befor-fixe.mp4`](video/v2befor-fixe.mp4) | V2 | Before-fix demo | 26.07 MB |
| [`v2-after-fixe.mp4`](video/v2-after-fixe.mp4) | V2 | After-fix demo | 5.99 MB |
| [`V4.mp4`](video/V4.mp4) | V4 | General demo | 152.91 MB |
| [`v5-befor fixe.mp4`](video/v5-befor%20fixe.mp4) | V5 | Before-fix demo | 6.69 MB |
| [`v5-after-fixe.mp4`](video/v5-after-fixe.mp4) | V5 | After-fix demo | 9.43 MB |
| [`v6.mp4`](video/v6.mp4) | V6 | General demo | 12.79 MB |
| [`v7.mp4`](video/v7.mp4) | V7 | General demo | 148.48 MB |
| [`v8-befor-fixe.mp4`](video/v8-befor-fixe.mp4) | V8 | Before-fix demo | 18.26 MB |
| [`v8-after-fix.mp4`](video/v8-after-fix.mp4) | V8 | After-fix demo | 7.23 MB |
| [`v9.mp4`](video/v9.mp4) | V9 | General demo | 13.57 MB |

## Git LFS

This repository uses Git LFS for video files.

The `.gitattributes` file tracks:

```text
*.MOV filter=lfs diff=lfs merge=lfs -text
*.mp4 filter=lfs diff=lfs merge=lfs -text
*.MP4 filter=lfs diff=lfs merge=lfs -text
```

The following video files are tracked with Git LFS:

```text
video/V1.mp4
video/V10.mp4
video/V4.mp4
video/v2-after-fixe.mp4
video/v2befor-fixe.mp4
video/v5-after-fixe.mp4
video/v5-befor fixe.mp4
video/v6.mp4
video/v7.mp4
video/v8-after-fix.mp4
video/v8-befor-fixe.mp4
video/v9.mp4
```

## Opening Binary Files

Some files in this repository are binary files and may not open inside the VS Code text editor.

Examples:

- `.mp4` video files
- `.pdf` slide file

If VS Code shows a message such as:

```text
The file is not displayed in the text editor because it is either binary or uses an unsupported text encoding.
```

that does not mean the file is broken.

Use the appropriate application instead:

- Open videos with a video player or through GitHub download/preview.
- Open the slide PDF with a PDF viewer, browser, or GitHub preview.

## Tools Used

The project used the following tools and services:

- AWS Console
- AWS CloudShell
- Amazon API Gateway
- AWS Lambda
- Amazon Cognito
- Amazon DynamoDB
- Amazon SQS
- Browser DevTools
- curl
- jq
- Python 3
- Visual Studio Code
- Git
- GitHub
- Git LFS

## Security Notes

- Sensitive tokens and credentials are redacted.
- Full JWT values are not exposed in reports or screenshots.
- Testing was performed in the DVSA lab/project environment.
- The project is for educational security analysis and mitigation.
- All documented fixes were verified with after-fix testing.

## Current Repository Status

At the time of the latest update:

```text
Branch: main
Status: clean
Remote: origin/main
State: up to date
Untracked files: none
Modified files: none
Unpushed commits: none
```