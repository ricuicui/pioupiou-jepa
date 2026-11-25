<!-- © 2026 Tony dev web. Tous droits réservés. -->

# Pioupiou JEPA

**Pioupiou JEPA** is a small French AI model built on the JEPA idea (*Joint Embedding Predictive Architecture*, proposed by [Yann LeCun](https://openreview.net/forum?id=BZ5a1r-kVsf)). Instead of predicting the next word like an LLM, it learns to predict the *meaning* of the next sentence. It is written in Rust, runs on the CPU only, with no graphics card and no internet, and powers the assistant of the [Ricuicui](https://ricuicui.com) desktop app for professionals.

> **This page presents the model. No code, weights or training data are published here.**
> To use Pioupiou JEPA, download Ricuicui for macOS or Windows: https://ricuicui.com/telecharger

## In short

| | |
|---|---|
| Architecture | JEPA (encoder + predictor of the next sentence's meaning), plus exact programs for some tasks (calculation, planning) |
| Parameters | 49.7 million |
| Size on disk | 324.3 MB |
| Memory used | 542.9 MB |
| Hardware | CPU only, no graphics card |
| Time to understand a request | 0.22 ms (median) |
| Languages | French, English |
| Runs | Locally, inside the Ricuicui app; your data stays on your computer |

## What it does

- Understands office requests: agenda, reminders, letters, emails, calculations, web pages…
- Writes letters and emails from its templates, keeping the exact words of the request.
- Summarises pages by keeping their most useful sentences.
- Calculates and handles dates exactly.
- Splits a multi-step request into steps the app runs in order.
- When unsure, offers a few answers to pick from, or says "I don't know" rather than inventing.

## Measured results

Measured on version 1.5 (24 November 2026), on a Mac mini M6 with 16 GB. Pioupiou JEPA on the CPU; [Qwen3 4B](https://huggingface.co/Qwen/Qwen3-4B) and [Gemma 4 12B](https://ai.google.dev/gemma) in [llama.cpp](https://github.com/ggml-org/llama.cpp) on the GPU. 2,244 tasks in 15 tests, never seen in training.

| | Pioupiou JEPA | Qwen3 4B | Gemma 4 12B |
|---|---:|---:|---:|
| Graphics card | **none** | yes | yes |
| Office requests understood | **99.0%** | 59.0% | 92.0% |
| Median time per request | **0.22 ms** | 214 ms | 505 ms |
| Total time, 2,244 tasks | **3.4 s** | 1 h 12 | 3 h 18 |
| Memory used | **542.9 MB** | 3.8 GB | 7.5 GB |
| Size on disk | **324.3 MB** | 2.55 GB | 6.72 GB |

Of the 15 tests, Pioupiou JEPA clearly wins 5, ties 2 and loses 6.

## Limits

- **A specialist, not a general-purpose model.** No general knowledge, no multi-step reasoning, no maths word problems.
- **Often says "I don't know"** (12% of tasks): that is how it avoids traps.
- **Writing and translation stay limited:** letters only from its templates; translations keep the source word order.

## Links

- Website: https://ricuicui.com
- Download Ricuicui: https://ricuicui.com/telecharger
- Documentation: https://ricuicui.com/documentation

---

## En français

**Pioupiou JEPA** est un petit modèle d'IA français, fondé sur l'idée JEPA de Yann LeCun : au lieu de deviner le mot suivant comme un LLM, il apprend à prévoir le *sens* de la phrase suivante. Il est écrit en Rust et tourne sur le processeur seul, sans carte graphique ni internet. C'est lui qui fait marcher l'assistant de [Ricuicui](https://ricuicui.com), l'appli de travail locale pour les professionnels : vos données restent sur votre ordinateur.

- 49,7 millions de paramètres, 324 Mo sur le disque, 543 Mo de mémoire.
- Comprend 99 % des demandes de bureau (Gemma 4 12B : 92 %), en 0,22 ms.
- Écrit lettres et courriels, résume, calcule, gère les dates, découpe une demande en étapes.
- Dit « je ne sais pas » plutôt que d'inventer.

Cette page présente le modèle : ni code, ni poids, ni données d'entraînement ne sont publiés ici.
Télécharger Ricuicui (Mac et Windows) : https://ricuicui.com/telecharger

## License

All rights reserved. © 2026 Tony dev web. Tous droits réservés.
