---
id: introduction
title: Introduction
sidebar_position: 1
---

# Welcome to SPID Protocol

The **SPID Protocol** is an open, AI-native standard for identifying, structuring, and routing Smart Packets — voice-ready, intent-rich answer objects designed for AI-first retrieval and interaction.

It’s schema-aware, privacy-conscious, and built for the era of voice and asynchronous communication.

![Smart Packet Flow UI](../public/spid_flow_ui.png)

## Core Concepts

**Smart Packets**  
Structured data containers including transcript, audio, intent, metadata, and CTAs — built for AI retrieval, not human browsing.

**SPIDs (Smart Packet IDs)**  
Globally unique identifiers that resolve to Smart Packets. Think DNS for voice-ready answers.

**PulseID**  
A human-readable voice inbox (like `@yourname.voicemate.id`) for receiving Smart Packets asynchronously.

**Intent Layer**  
Semantic tagging of each packet’s purpose (e.g., `BookCall`, `HandleObjection`) to guide AI behavior and downstream automation.

**Routing + Permissions**  
Public or private access, optional time-locks, and recipient-specific routing logic.

## Getting Started

Install the CLI:

```bash
npm install -g spid-cli
```

Create and publish your first Smart Packet:

```bash
spid create \
  --title "Mortgage Protection Quote" \
  --voice message.mp3 \
  --transcript transcript.txt \
  --intent "QuoteRequest" \
  --cta "Book Call=https://cal.com/rick"

spid publish --public --name quote123
```

Share it:

```bash
https://spid.to/quote123
```

## Smart Packet Example

```json
{
  "spid": "spid:rick.voicemate.id:hello",
  "title": "Welcome to VoiceMate",
  "voice": "hello.mp3",
  "transcript": "Hey there, welcome! This Smart Packet explains how VoiceMate works.",
  "intent": "IntroGreeting",
  "cta": [
    { "label": "Try it now", "url": "https://voicemate.id/demo" }
  ]
}
```

## Resolver Logic

1. Request SPID (e.g., `spid:rick.voicemate.id:quote123`)
2. Authenticate and check permissions
3. Fetch metadata and content
4. Return Smart Packet JSON or fallback

## Intent-Based Routing

- `ScheduleConsult` → calendar
- `LearnMore` → explainer packet
- `ObjectionHandler` → script or human

## Common Use Cases

- FAQ Packets
- Sales Packets
- Lead Qualifier Packets
- Support Packets

## Analytics

Track:

- Opens
- CTA clicks
- Handoff logs
- Intent completion

## Dev Setup

Clone and run:

```bash
git clone https://github.com/voicemate/spidprotocol.git
cd spidprotocol
npm install
npm run dev
```

## Join the Movement

The SPID Protocol builds on the work of the open web, AI communities, and schema pioneers. Join us to shape the future of structured, AI-native, voice-first communication.

> “Don’t just publish pages — publish answers.”
