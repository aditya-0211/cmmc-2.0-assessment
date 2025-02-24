# CMMC 2.0 Level 1 Compliance Assessment Report: Michael Scott Paper Company

## Project Overview

This report summarizes the assessment of Michael Scott Paper Company's (MSPC) compliance with CMMC 2.0 Level 1 requirements. The assessment evaluated various aspects of MSPC's IT infrastructure and policies against the controls defined in CMMC 2.0 Level 1. The assessment was conducted by Aditya Deshpande, UID: 120333590.

## Key Findings

*   **Access Control:**
    *   Authorized access control is generally met with policies for user authentication and least privilege.
    *   Transaction and function control is met through the use of AppArmor.
    *   External connections are not adequately controlled due to an inactive firewall and unrestricted network connectivity.
    *   Control of public information is not met, as the website allows unrestricted file uploads.
*   **Identification and Authentication:**
    *   User identification is met using the `/etc/passwd` file.
    *   Authentication is met through PAM and SSH, but password authentication is enabled for SSH.
*   **Media Protection:**
    *   Media disposal requirements are met through the MSPC-Media-Destruction-Policy, which includes physical destruction and data wiping.
*   **Physical Protection:**
    *   Physical access to systems is limited to authorized individuals.
    *   Visitors are escorted and monitored.
    *   Physical access logs are not maintained.
    *   Management of physical access devices lacks sufficient detail.
*   **Systems and Communications Protection:**
    *   Boundary protection is inadequate due to an inactive firewall and lack of defined rules in iptables.
    *   Public-access system separation is not applicable as the system has no public-facing services.
*   **System and Information Integrity:**
    *   Flaw remediation processes are not evident, with no vulnerability scanning software detected.
    *   Malicious code protection is met through the use of ClamAV.
    *   Malicious code protection mechanisms are updated regularly.
    *   Periodic system scans are performed, but real-time scanning of files from external sources is not enabled.

## Critical Vulnerabilities

*   **High:** Unrestricted external connections due to inactive firewall (AC.L1-3.1.20)
*   **High:** Uncontrolled public file uploads on the company website (AC.L1-3.1.22)
*   **Medium:** Lack of physical access logs (PE.L1-3.10.4)
*   **Medium:** Inadequate management of physical access devices (PE.L1-3.10.5)
*   **Medium:** Lack of real-time scanning of externally sourced files (SI.L1-3.14.5)
*   **Low:** SSH Password Authentication enabled

## Exploitation Path (Potential)

1.  An attacker could upload a malicious file to the MSPC website due to the lack of upload restrictions.
2.  The attacker could exploit the unrestricted network connections to gain unauthorized access to internal systems.
3.  Without physical access logs, unauthorized physical access attempts may go unnoticed.
4.  Lack of real-time scanning could allow malicious files to be executed, compromising the system.

## Key Recommendations

*   **Activate and configure the firewall** with strict rules to limit incoming and outgoing traffic (AC.L1-3.1.20, SC.L1-3.13.1).
*   **Implement a login mechanism and file validation** on the website to control file uploads (AC.L1-3.1.22).
*   **Establish and maintain physical access logs** (PE.L1-3.10.4).
*   **Develop a detailed policy** for managing physical access devices (PE.L1-3.10.5).
*   **Configure ClamAV** to perform real-time scans of files from external sources (SI.L1-3.14.5).
*   **Disable SSH Password Authentication** and use key-based authentication.
*   **Implement vulnerability scanning** to identify and remediate system flaws (SI.L1-3.14.1).

## Conclusion

The assessment revealed several areas where Michael Scott Paper Company does not fully meet CMMC 2.0 Level 1 requirements. Implementing the recommendations outlined in this report will significantly improve MSPC's security posture and ensure compliance with CMMC Level 1.
