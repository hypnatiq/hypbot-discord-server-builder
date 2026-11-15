# Architecture

## Design goal

HypBot is designed around one owner-controlled Discord application with an explicit profile for every approved server. A profile owns that server's identity, feature switches, role and channel references, logging destinations, panel records, and acceptance evidence.

Unknown servers fail closed. The application never falls back to another profile.

## Main components

### Profile boundary

Each server profile identifies only the server resources that belong to that server. Operations select one profile before they read or change Discord state.

### Inventory and planning

A read-only inventory records the current categories, channels, roles, applications, permissions, member assignments, and preserved history. A planned change is compared with that inventory before a mutation begins.

### Staged builder

The builder prepares new controls privately. Existing member access and channel history remain in place until the owner reviews the staged result and authorizes the live batch.

### Interaction handlers

Buttons, commands, polls, modals, and context actions validate the active server, channel, user permissions, and component identity before they act. Repeated requests are handled safely where the workflow is intended to be idempotent.

### Operational logging

Human and server activity goes to a private administrator log. Runtime and workflow health goes to a separate private bot log. Message edit and deletion events retain Discord-native metadata without copying the message body.

### Verification

Verification checks the observable server state instead of trusting configuration alone. It checks roles, permissions, channels, topics, overrides, panel identity, interaction results, temporary-access removal, and active runtime state.

### Recovery

Recovery favors disabling the bot, restoring a recorded snapshot, or accepting a narrowly verified current state. Normal recovery does not delete Discord history.

## Trust boundaries

- Discord remains the authority for live server state.
- The private project folder remains the authority for source and profiles.
- Credentials remain outside source files and public documentation.
- A local test does not prove live Discord state.
- A copied transfer package is not accepted until the receiving computer verifies it.

## Public limitation

This repository explains the design without publishing the private implementation, live identifiers, or operational data. It cannot be run as a replacement HypBot instance.

