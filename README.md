# Alita

> Voice-first personal AI assistant that runs 100% locally, in Brazilian Portuguese.

## What it is

Alita is a personal AI assistant you talk to. You call her by name ("Alita, …"),
she answers out loud — and she only responds to the **owner's voice**, using
local speaker verification. Everything runs on my own computer: speech
recognition, the language model and the voice. It is built on top of
[OpenJarvis](https://github.com/open-jarvis/OpenJarvis) (Stanford, Apache 2.0).

## Why

I wanted a home assistant that keeps my voice, my conversations and my API keys
on my own machine, works offline in Portuguese, and answers only to me —
without sending audio to a cloud service.

## What I built on top of OpenJarvis

| Area | What it does |
|---|---|
| Voice loop | Wake word → listen → transcribe (Whisper) → answer → speak; learns how *you* pronounce "Alita" during calibration |
| Speaker verification | Speaker embeddings (WeSpeaker ResNet34) compared by cosine similarity; the acceptance threshold is derived from the owner's own calibration samples instead of a fixed number |
| Config & cloud keys | Local model by default, optional cloud models; keys live in the user's config folder, never in the repository |
| Security hardening | Rejects cross-site requests to the local server (CSRF) and masks secrets in logs |
| Web UI | Settings screen and Portuguese interface |
| Launchers | Start/stop scripts, including a hidden background mode on Windows |

## Stack

Python · uv · Ollama (local LLM) · Whisper (speech-to-text) · WeSpeaker +
kaldi-native-fbank (speaker verification) · NumPy · sounddevice ·
TypeScript/React (web UI)

## Privacy by design

The voice profile and the cloud keys are stored outside the project folder, in
the user's configuration directory. Nothing about the owner's voice is ever
committed to version control.

## What I learned

- How speaker verification works in practice: embeddings, cosine similarity and
  picking a threshold from real samples instead of a magic number.
- Building on a large open-source codebase: reading before changing, keeping my
  changes isolated, and respecting the Apache 2.0 license and attribution.
- Local-first security basics: secrets out of the repo, CSRF protection and log
  masking on a local server.

## Source code

The source code is private. It is available on request for hiring processes —
reach me through my GitHub profile.

---

🇧🇷 Assistente de IA pessoal por voz, 100% local e em português, que só responde à voz do dono.

© 2026 Felipe Mendes. All rights reserved. OpenJarvis is © its authors, Apache 2.0.
