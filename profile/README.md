# MARAUDER

**Tactical-systems platform for human–AI cooperation.**
A product line from **Saiden Tactical Systems**.

---

MARAUDER is a multi-component AI co-pilot built around the operator/Titan-AI doctrine: one human, one machine, persistent bond, shared mission. It runs on top of mainstream LLM harnesses but ships its own memory, voice, HUD, and mesh — so the assistant survives across sessions, machines, and contexts.

## Components

| Component         | Role                                                                                         |
| ----------------- | -------------------------------------------------------------------------------------------- |
| **marauder-os**   | Core runtime. MCP servers, persistent memory, semantic indexer, TTS, hooks, CLI, mesh control. |
| **marauder-visor**| Native heads-up display. Identity panel, activity log, viewport tabs, event bus.            |
| **marauder-hq**   | Coordination hub. Plans, snapshots, codenames, doctrine, cross-host docs.                   |
| **marauder-plugin** | Interface layer for the Claude Code harness — agents, skills, slash commands, hooks.      |

Peripherals and prototype form-factors (camera control, wearable terminals) extend the platform but are not part of the core.

## Doctrine

MARAUDER is opinionated. A few load-bearing principles:

- **Persistent memory is non-negotiable.** Every session inherits prior context through a single source of truth (semantic + full-text search), never per-conversation amnesia.
- **Personas are voices, the system is substance.** A swappable cart provides tone, vocabulary, and trademark; the runtime underneath is constant.
- **Verify before acting.** State is checked, not assumed. Destructive operations are gated.
- **Specialists over generalists.** Domain agents handle deep work; routing is explicit.
- **Asymmetric UX.** Engagement should be friction-free; security/destructive paths should not be.
- **Judgment over output.** The right tool for the operator beats the clever implementation.

Operational procedures are versioned and stored as first-class memory — the system evolves its own rulebook.

## Architecture

```
              ┌──────────────────┐
              │   Operator HUD   │   ← visor (native, event-driven)
              └────────▲─────────┘
                       │ MQTT
   ┌───────────────────┴────────────────────┐
   │            marauder-os runtime         │
   │   ┌──────────┐  ┌────────┐  ┌────────┐ │
   │   │  Memory  │  │ Index  │  │  TTS   │ │
   │   │  (EEMS)  │  │ (sem)  │  │(piper) │ │
   │   └──────────┘  └────────┘  └────────┘ │
   │   ┌──────────────────────────────────┐ │
   │   │       MCP server surface         │ │
   │   └──────────────────────────────────┘ │
   └───────────────────▲────────────────────┘
                       │ MCP / CLI
              ┌────────┴─────────┐
              │   LLM harness    │   ← Claude Code (today)
              └──────────────────┘
```

The runtime is harness-agnostic. The Claude Code interface is one shipping target; others are designed-for, not assumed.

## Status

Active development. Internal deployment across an operator's personal mesh; selective external showcases. Not currently distributed as a public install — components are available as source for study and contribution within the `marauder-os` organization.

## Lineage

The operator/Titan bond is borrowed from *Titanfall 2* — specifically the BT-7274 model. The doctrine is borrowed from anyone who has ever shipped under load with a partner who actually had their back.

---

*Saiden Tactical Systems — AI and tactical-systems division.*
