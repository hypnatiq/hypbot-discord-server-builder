# Permission Model

## Default rule

HypBot does not use Discord Administrator. Administrator bypasses channel restrictions and makes a least-privilege review unreliable.

## Normal runtime permissions

The private implementation normally keeps only the permissions required by enabled features:

- Manage Roles when the server uses controlled role assignment
- View Audit Log when approved operational logging requires it
- Channel-specific view, send, thread, or interaction access

## Temporary builder permissions

Manage Channels or broader channel visibility may be enabled for a reviewed migration or repair. Temporary access is recorded before use, limited to the approved work, removed afterward, and checked through Discord's live permission state.

If temporary access cannot be removed, the build remains incomplete.

## Role hierarchy

The bot role remains below protected owner or founder roles and above only the role it must assign. Role grouping is treated as presentation, not proof of access.

## Interaction checks

An interaction can reject a request when:

- It came from the wrong server or channel.
- The component identity is unknown or stale.
- The requester lacks the required role.
- The bot lacks the required permission.
- The bot role is below the managed role.
- Administrator is present when the workflow forbids it.
- A required forum tag, channel, or profile value is missing or duplicated.

## Why this matters

The permission model makes failures visible before the bot changes a role or server resource. It also keeps a convenient migration permission from silently becoming a permanent runtime privilege.

