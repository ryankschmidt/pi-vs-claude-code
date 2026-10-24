---
title: "ComsNet rail"
description: "Ryan-owned socket rail namespace; upstream files remain unchanged."
type: reference
status: active
created: "2026-10-24"
last_updated: "2026-10-24"
---

# ComsNet rail

This folder is the ComsNet rail home inside Ryan’s fork of Dan’s whole repository. The stock extensions/, scripts/ and specs/ trees stay as upstream wrote them.

## Kept, changed and dropped — Oct 16, 2026, 10:08 PM PDT

Source: /Users/Admin/core-root/vault/01_Projects/workbench/infra/throughline/_meta/absurd-durable-rail-study-2026-10-22/handoff-2026-10-24/_agents/Dan-Code-Keep-Thread.json (keep_change_drop_excerpt.text). The following quoted block is byte-identical to that extracted span:

Kept:
- The message envelopes: prompt, response and ping, with their correlation and target.
- The agent-facing tools for send, ask and list peers.
- Peer-to-peer messaging, with no forced parent-and-child hierarchy.

Changed:
- **Topology.** Agents no longer open each other's sockets in a shared folder. Each agent talks only to its host service, on one socket the launcher hands it.
- **Identity.** Dan's code accepts whoever opens the socket file. Yours reads the kernel's peer credentials on every connection and matches them to the supervisor's registry.
- **Durability.** Dan's in-memory pending replies and inbound queue are removed. Every message is in Absurd before it is acknowledged.
- **Delivery.** A message wakes the receiver's turn, and nothing polls.

Dropped, with the files kept as history:
- The HTTP-and-SSE hub server and its client extension.
- The hub's discovery files and its auth token.
- The peer ping, keepalive and discovery loops.
- Both polling and blocking tools: `coms_get` and `coms_await`.

Traffic between devices uses ThroughLine pairing over Tailscale instead of the hub. ThroughLine's current injected messaging tools keep running until the new rail passes its identity, delivery, restart and Mac-adapter checks. Only then are they removed.

Ryan’s following approval, Oct 16, 2026, 10:18 PM PDT: “Yes you got it right.” (Transcript-attributed; original app sender identity was not recovered.)

Build order: /Users/Admin/core-root/vault/01_Projects/workbench/infra/throughline/plans/pi-durable-integration-2026-10-16/Coms-Changes.json; status: file-level-build-order-not-implemented. Its later shared-helper amendment governs, not a second private helper.
