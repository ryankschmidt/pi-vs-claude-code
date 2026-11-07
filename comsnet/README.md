---
title: "ComsNet rail"
description: "Ryan-owned socket rail namespace; upstream files remain unchanged."
type: reference
name: comsnet
purpose: "Route fork builders to Dan adoption boundaries while keeping socket delivery separate from Absurd message records."
status: active
created: "2026-10-24"
last_updated: "2026-11-07"
---

# ComsNet rail

This folder is the ComsNet rail home inside Ryan’s fork of Dan’s whole repository. The stock extensions/, scripts/ and specs/ trees stay as upstream wrote them.

## Dan's code: adopt, adapt, don't use

IndyDevDan (YouTube) / disler (GitHub). [Read the adopt/adapt rule card](http://mbp21.tailec334b.ts.net:8129/v/vault/r/01_Projects/workbench/infra/pi-harness/_meta/disler-repos-2026-11-06/READ-FIRST-Adopt-Or-Adapt-Dan.md). Source: /Users/Admin/core-root/vault/01_Projects/workbench/infra/pi-harness/_meta/disler-repos-2026-11-06/READ-FIRST-Adopt-Or-Adapt-Dan.md before using upstream code or lessons.

- **Adopt:** the socket-messaging idea from `pi-vs-claude-code`; ComsNet means only this design and what we build from it, never Seatmail.
- **Adapt:** one host messaging service, one Unix socket per agent, kernel-identified peers; record every message in Absurd with its real sender before acknowledgement. Pi Durable owns the agent run, not the shared message record.
- **Don't use:** the HTTP/SSE hub or ephemeral unrecorded messages; retained upstream files are history, not adopted runtime behavior.

Fork additions stay under `^comsnet/` and are recorded in `throughline-seam.json`; stock upstream files remain unchanged.

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
