# Blucks AI — Multimodal Sports Analytics

Ask questions about games in plain English and get answers grounded in real match data and footage. Blucks AI combines structured game data, video transcripts, and Gemini Flash in a multimodal RAG pipeline, so responses cite what actually happened instead of what the model guesses.

**Stack:** Python · Gemini Flash · RAG · FFmpeg · Flask · React · TypeScript · Google Cloud

---

## Highlights

- **Multimodal RAG.** Retrieves relevant match context from structured game data and video transcripts, then grounds Gemini Flash's answer in it — enabling natural-language analysis across historical records and footage.
- **~83% faster inference.** Chunking game footage into timestamped 30-second segments cut per-segment latency from **~4.1s to ~0.7s**.
- **Evaluation harness.** 50+ test queries targeting ambiguous stats and missing context, used to add prompt guardrails that improved response consistency on hallucination-prone edge cases.

## How it works

```
game footage ──► 30-second timestamped segments ──► Gemini Flash
structured game data + transcripts ──► retrieval
                                            │
user question ──────────────────────────────┤
                                            ▼
                  grounded answer + timestamped clips
```

1. **Segment.** Footage is split into timestamped 30-second chunks, so the model only processes the part of the game that matters.
2. **Retrieve.** For each question, the most relevant game data, transcript passages, and segments are pulled as context.
3. **Answer.** Gemini Flash answers using only the retrieved context and returns commentary with start/end timestamps.
4. **Clip.** FFmpeg trims each returned moment into its own video clip.

### Example questions

```
Show every home run in this game.
Which plays in the 7th inning changed the score?
```

## Guardrails

The evaluation harness targets cases where LLMs tend to hallucinate:

- Conflicting or ambiguous statistics
- Incomplete transcripts
- Ambiguous player references
- Questions the available context can't answer

Prompt guardrails make the model return an empty result instead of inventing a moment when nothing matches.

## Running locally

Requirements: Docker, a Gemini API key, and a Google Cloud project (Storage + Firestore).

```bash
# backend/.env
GEMINI_API_KEY=your_key_here

docker-compose -f docker-compose.dev.yml build
docker-compose -f docker-compose.dev.yml up
```
