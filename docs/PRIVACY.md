# Privacy and Data Handling

HypBot is designed to use Discord-native facts without creating a second copy of private conversation content.

## Data the private bot can use

- Stable Discord IDs needed for configured server resources
- Role and channel state
- Join, leave, voice, and profile-change events
- Audit-log actor and reason when Discord supplies them
- Message edit or deletion metadata without the message body
- Private runtime and verification records

## Data the public repository does not contain

- Message content
- Direct messages
- Bot tokens or encrypted credentials
- Real server, user, channel, role, message, or application IDs
- Member names or private logs
- IP addresses or tracking links
- Machine-local secret or state folders

Discord app events do not provide member IP addresses. The project does not claim to collect or infer them.

## Retention principle

Operational records are kept only where they support server administration, runtime health, verification, or recovery. A new server requires an explicit decision about destinations, access, retention, and enabled event families.

## Public package

This repository is a sanitized case study. It contains no live Discord configuration and cannot access a server.

