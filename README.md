# Spider King

Spider King is a protocol-first reverse engineering skill for turning hostile web clients into stable, pure-protocol Python collectors.

It is built for targets protected by dynamic signatures, rotating cookies, transport wrappers, GraphQL, WebSocket streams, protobuf or binary envelopes, encrypted responses, session-bound contracts, bootstrap challenges, WebAssembly helpers, and other browser-facing anti-collector tricks.

## What This Skill Does

Spider King helps recover the real business protocol behind hostile web applications and deliver a collector that runs locally without hidden browser dependencies.

The skill is optimized for:

- Finding the real request path instead of trusting page hints
- Identifying the true changing state behind “browser-only” behavior
- Rebuilding dynamic state offline with Python-first delivery
- Recovering structured transports such as GraphQL, WebSocket, protobuf, msgpack, and custom envelopes
- Rebuilding local decode chains for encrypted, compressed, or obfuscated responses
- Handling stateful session flows such as pairing, login bootstrap, heartbeats, frame sequencing, and media-key derivation

## Core Principles

Spider King follows a few non-negotiable rules:

- Trust the wire, not the page text
- Treat transport shape as part of the protocol contract
- Validate suspicious helpers with fixed inputs before trusting their names
- Keep browser tooling limited to reconnaissance and evidence gathering
- Never ship browser automation as the final solution when protocol recovery is possible
- Prefer pure Python delivery, with only minimal local JS or WASM helpers when truly necessary

## Typical Targets

This skill is a good fit when a site or app shows symptoms like:

- A visible endpoint that does not match the real network request
- A `sign`, `token`, or `m` value that changes after wrapper code runs
- A public page that still needs bootstrap keys, cookies, or encrypted envelopes
- Response data that only becomes useful after decoding, decompression, protobuf parsing, or glyph mapping
- A long-lived WebSocket stream that depends on auth, subscribe, heartbeat, ack, reconnect, or frame ordering
- A login or pairing flow that returns refs, public keys, client IDs, or session seeds before business frames become readable
- Media metadata that is visible, but actual media replay or decryption needs a separately derived secret

## Workflow

Spider King works in a protocol-recovery loop:

1. Identify the real request path
2. Classify the real moving parts
3. Locate the canonical mutation point
4. Rebuild the moving parts offline
5. Prove repeatable local replay
6. Deliver a stable Python collector

## Repository Layout

- `SKILL.md` - main skill definition and operating doctrine
- `references/` - reusable reverse-engineering playbooks and routing references
- `scripts/` - helper scripts for scaffolding, protocol diffing, crypto fingerprinting, and environment checks
- `agents/` - agent integration configuration

## Delivery Standard

A job is not considered complete until the final path is local, explicit, and testable.

Acceptable delivery shapes include:

- Pure Python collector
- Python plus minimal local JS helper
- Python plus minimal local WASM helper
- Python plus local bootstrap executor

Not acceptable:

- Browser-driven replay as the final collector
- “Works only in my browser profile”
- Hidden CDP, Playwright, or Selenium dependencies as the real runtime

## Best Use Cases

Spider King is especially useful for:

- Building protocol collectors for difficult public-data targets
- Recovering GraphQL or WebSocket business flows
- Replaying encrypted or wrapped APIs without browser automation
- Porting hostile browser-side logic into maintainable Python collectors
- Turning one-off reverse wins into reusable methodology

## Goal

When a target looks browser-only, Spider King asks three questions first:

1. What is the real request?
2. What is the real changing state?
3. Can that state be rebuilt locally?

Most hard targets collapse once those three questions are answered honestly.
