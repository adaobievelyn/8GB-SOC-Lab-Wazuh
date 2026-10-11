# Wazuh Investigation Case Studies

This directory contains investigation notes from the 8GB SOC Lab.

The purpose of these case studies is to show how I used the Wazuh environment after deployment: examining endpoint telemetry, filtering security events, reviewing authentication activity, interpreting rule context, and investigating controlled security activity.

These are not production incidents. All activity described here occurred inside a controlled personal lab.

## Investigation Cases

### 1. Windows Authentication Analysis

[Read the case study](./01-windows-authentication-analysis.md)

Reviewed Windows authentication telemetry in Wazuh, including failed and successful logon activity, event metadata, rule descriptions and available MITRE-linked context.

### 2. Linux Security Telemetry

[Read the case study](./02-linux-security-telemetry.md)

Reviewed Linux endpoint security telemetry, including authentication/session-related events and host activity collected through the Wazuh agent.

### 3. Controlled Shell Activity

[Read the case study](./03-controlled-shell-activity.md)

Generated controlled listener/shell activity over port 4444 inside the lab, confirmed the connection at the host level, and used Wazuh event views and filters to examine the surrounding security telemetry.

## Investigation Method

Across these cases, I used a simple evidence-first process:

1. Generate or identify known activity.
2. Locate the relevant endpoint in Wazuh.
3. Filter the event stream to reduce unrelated telemetry.
4. Inspect the underlying event and rule fields.
5. Compare what happened on the endpoint with what Wazuh recorded.
6. Separate direct observations from interpretation.
7. Avoid assigning malicious intent unless the evidence supports it.

## Evidence Boundaries

These case studies demonstrate hands-on experience with:

- Wazuh security-event investigation
- Windows and Linux endpoint telemetry
- Authentication-event analysis
- Wazuh event filtering
- Rule and event-context review
- Controlled security testing
- Evidence-based analyst reasoning

They do not represent:

- A production SOC environment
- Enterprise-scale Wazuh administration
- Authorship of Wazuh built-in rules
- Malware analysis
- A real-world external intrusion
- Proof that every observed event is malicious

The lab was designed for controlled learning, security monitoring and investigation.

## Related Project

Return to the main project:

[8GB SOC Lab — Multi-Endpoint Wazuh SIEM Under Hardware Constraints](../README.md)
