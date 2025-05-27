# SPID Protocol

The **SPID Protocol** is an open, AI-native standard for identifying, structuring, and routing Smart Packets — voice-ready, intent-rich answer objects designed for AI-first retrieval and interaction.

It’s schema-aware, privacy-conscious, and built for the era of voice and asynchronous communication.

![Smart Packet Flow UI](public/spid_flow_ui.png)

---

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

---

## Get Started

### 1. Install the CLI
```bash
npm install -g spid-cli
```

### 2. Create your first Smart Packet
```bash
spid create \
  --title "Mortgage Protection Quote" \
  --voice message.mp3 \
  --transcript transcript.txt \
  --intent "QuoteRequest" \
  --cta "Book Call=https://cal.com/rick"
```

### 3. Register it with a SPID
```bash
spid publish --public --name quote123
```

### 4. Share your Smart Packet
```bash
https://spid.to/quote123
```

---

## Hello World Example

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

---

## SPID Resolver Logic

1. Client requests a SPID (e.g., `spid:rick.voicemate.id:quote123`)
2. Resolver authenticates access based on permissions
3. Retrieves and parses Smart Packet metadata
4. Returns the JSON payload or fallback if access is denied

---

## Intent-Based Handoffs

Smart Packets support downstream chaining based on intent:

- `intent:ScheduleConsult` → opens booking calendar
- `intent:LearnMore` → routes to explainer packet
- `intent:ObjectionHandler` → invokes fallback script or human rep

---

## Common Packet Patterns

- FAQ Packet: Voice + transcript + “Ask Another” CTA
- Sales Packet: Pitch + form + calendar
- Lead Qualifier Packet: Intro + qualifying form + AI routing
- Support Packet: Answer + escalation path

---

## Tracing + Analytics

SPID supports embedded packet analytics:

- Opened timestamp
- CTA click tracking
- AI handoff logs
- Intent follow-through metrics

Optional integrations: Segment, PostHog, BigQuery

---

## Development

Clone the official repo:
```bash
git clone https://github.com/voicemate/spidprotocol.git
cd spidprotocol
```

Install dependencies:
```bash
npm install
```

Run local dev server:
```bash
npm run dev
```

---

## Acknowledgements

The SPID Protocol builds on the great work of:

- schema.org and JSON-LD
- OpenAI Assistants SDK
- Supabase Edge Functions
- Pydantic + VEO Schema
- The broader web3 and AI communities

We’re building SPID as an open protocol — join us at [spidprotocol.org](https://spidprotocol.org) and shape the future of voice-first, structured communication.

---

> “Don’t just publish pages — publish answers.”  
> — SPID Protocol Manifesto
