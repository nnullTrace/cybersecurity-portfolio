# Phishing & Blocked Outbound Connection

## Overview
Simulated SOC L1 investigation of a phishing email leading to a blocked outbound connection.

## Scenario
An employee received a phishing email impersonating a delivery service. The email contained a shortened URL. The user attempted to access the link, triggering a firewall alert.

## Investigation Steps
1. Alert review
2. URL analysis
3. IP reputation check
4. Log correlation

## Outcome
- Classified as True Positive
- Escalated to L2

## Skills Used
- SIEM analysis
- Threat intelligence (browserleaks)
- Phishing detection
