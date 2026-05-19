# Incident Report 01 — Failed Windows Login Attempts

## Summary

Multiple failed login attempts were generated on the Windows endpoint and detected in Wazuh. This test confirmed that the Windows Wazuh agent is forwarding Security event logs to the Wazuh manager.

## Environment

- Wazuh Server: Ubuntu Server
- Endpoint: Windows endpoint with Wazuh agent
- Log Source: Windows Security Logs
- Detection Platform: Wazuh

## Event Details

- Event Type: Failed Windows logon
- Windows Event ID: 4625
- Endpoint: Windows agent
- Time Detected: [REDACTED]
- Source IP: [REDACTED]
- User Account: [REDACTED]

## Test Performed

Failed login attempts were intentionally generated on the Windows endpoint in a controlled lab environment. After confirming that Windows Event Viewer recorded the failed logon events, the Wazuh dashboard was filtered by agent and event ID to locate the corresponding events.

## Investigation

The failed logon events were first verified locally in Windows Event Viewer under Windows Logs → Security. The same activity was then located in Wazuh by filtering for Windows Event ID `4625`.

This confirmed the following:

- Windows generated the failed login event.
- The Wazuh agent collected the event.
- The Wazuh manager received the event.
- The Wazuh dashboard displayed the event after filtering.

## Impact

No unauthorized access occurred. This was a controlled test. In a real environment, repeated failed logins could indicate password guessing, brute-force activity, or unauthorized access attempts.

## Recommendation

- Monitor repeated failed login attempts.
- Review affected user accounts.
- Enable account lockout policies.
- Use strong passwords.
- Implement multi-factor authentication where possible.
- Investigate source IP addresses for repeated authentication failures.

## Status

Closed — Lab simulation.