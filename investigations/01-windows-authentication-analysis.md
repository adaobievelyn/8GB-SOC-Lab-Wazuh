# Investigation 01 — Windows Authentication Analysis

## Objective

Examine Windows authentication activity collected by Wazuh and determine what information was available to an analyst when reviewing failed and successful logon events.

The purpose was not simply to confirm that an alert existed, but to inspect the underlying event context and understand what the telemetry actually supported.

## Environment

- Wazuh Manager: Ubuntu Server 22.04
- Endpoint: Windows 11
- Virtualization: VirtualBox
- Host system: 8GB RAM
- Network: Bridged local lab network
- Environment type: Controlled personal SOC lab

## Evidence Observed

Wazuh collected Windows authentication-related security events from the monitored Windows endpoint.

The available evidence included both:

- Failed logon activity
- Successful logon activity

For individual events, Wazuh exposed contextual information such as:

- Agent / endpoint identity
- Event timestamp
- Windows event information
- Authentication result
- Rule description
- Rule level
- Associated rule metadata
- MITRE-linked context where available

One failed-authentication event was described by Wazuh as:

> Logon failure - Unknown user or bad password.

This provided more context than simply observing that "an alert occurred."

## Investigation Process

### 1. Identify the endpoint

I first confirmed that the Windows endpoint was enrolled and actively reporting to the Wazuh Manager.

This established that the events being reviewed were associated with the expected monitored system.

### 2. Review authentication events

I examined Windows security events associated with authentication activity.

The event stream contained both failed and successful logon activity, allowing the authentication behavior to be reviewed in context rather than treating every authentication event as equivalent.

### 3. Inspect event fields

I opened individual security events and reviewed their underlying fields.

Rather than relying only on dashboard counts, I examined information such as the endpoint, authentication result, event description and related metadata.

### 4. Review Wazuh rule context

I inspected the Wazuh rule information associated with relevant events.

Where available, this included:

- Rule description
- Rule severity / level
- Rule groups
- MITRE ATT&CK-related context

This helped distinguish the raw operating-system event from the additional classification and context applied by Wazuh.

### 5. Compare failed and successful activity

Failed and successful authentication events were considered separately.

A failed logon can indicate many different situations, including:

- Mistyped credentials
- Invalid account use
- Administrative testing
- Automated authentication attempts
- Potential unauthorized access attempts

Likewise, a successful logon is evidence that authentication succeeded, but does not by itself prove compromise.

Context is required before assigning security significance.

## Analyst Assessment

The investigation demonstrated that Wazuh was successfully collecting and exposing Windows authentication telemetry from the monitored endpoint.

The important analytical lesson was that authentication events should not be classified as malicious solely because they trigger a security rule.

The event itself establishes what was observed.

Interpretation requires additional context.

For example:

**Observed**

- An authentication attempt occurred.
- Wazuh recorded whether it failed or succeeded.
- The event contained endpoint and authentication context.
- Wazuh associated rule information was available.

**Not established by that evidence alone**

- Who intentionally initiated the activity.
- Whether the activity was malicious.
- Whether a successful login represented account compromise.
- Whether failed attempts constituted a brute-force attack.

Those conclusions would require additional evidence or behavioral context.

## What This Investigation Demonstrates

- Windows authentication-event analysis
- Wazuh event investigation
- Endpoint-focused filtering
- Review of event and rule metadata
- Interpretation of failed versus successful authentication
- MITRE-linked contextual analysis
- Separation of observation from inference

## Evidence Boundary

This was a controlled lab investigation.

The activity should not be described as a confirmed real-world attack or production security incident.

The evidence demonstrates authentication-event investigation and security-telemetry analysis within a Wazuh lab.

## Supporting Evidence

The project evidence includes screenshots of:

- Windows authentication/security events
- Failed-logon event details
- Successful-logon activity
- Wazuh rule metadata
- MITRE-linked rule context
- Windows endpoint security-event dashboards

Supporting screenshots are stored in:

[`../screenshots/`](../screenshots/)

## Related Case Studies

- [Linux Security Telemetry](./02-linux-security-telemetry.md)
- [Controlled Shell Activity](./03-controlled-shell-activity.md)

[Back to Investigation Index](./README.md)
