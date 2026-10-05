# 🩺 Scribeo

**Bilingual clinical scribe.** Converts Urdu-English doctor-patient conversations into structured medical notes.

## The Problem

Doctors in Pakistan spend hours writing clinical notes in English while speaking Urdu with patients. Existing AI scribes (Abridge, Nuance, Ambience) are built for English-first clinics and fail on Urdu-English code-switching.

## What Scribeo Does

1. **Listen** — Upload or record a doctor-patient conversation
2. **Transcribe** — Whisper large-v3-turbo (via Groq) transcribes the mixed Urdu-English audio
3. **Structure** — An LLM converts the transcript into a formatted SOAP note
4. **Edit & Export** — The doctor edits any section and downloads the final note

## Key Findings From Building This

- Whisper `base` and `small` hallucinate English words when they hear Urdu. `medium` and larger work.
- `task="translate"` drops clinical numbers (dosages, durations). `task="transcribe"` + LLM translation preserves them.
- Groq's hosted `whisper-large-v3-turbo` is ~20x faster than running Whisper locally on CPU, with equal or better accuracy.

## Stack

- **Speech-to-Text:** Groq Whisper large-v3-turbo
- **LLM:** Groq gpt-oss-120b
- **UI:** Gradio
- **Deployment:** Render

## Live Demo

[Add Render link once deployed]

## Limitations

- Tested only on Urdu-English. Other language pairs untested.
- No authentication — not for real patient data.
- For demo purposes only. Always verify with a licensed clinician.

## Author

**Aizaz Ahmad** — AI Developer & Agentic SaaS Product Designer
- GitHub: [aizaz-ahmad-ims](https://github.com/aizaz-ahmad-ims)
- LinkedIn: [add your LinkedIn URL]