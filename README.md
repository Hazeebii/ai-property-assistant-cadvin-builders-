# AI Property Assistant — Cadvin Builders

An AI-powered WhatsApp property enquiry assistant built with n8n. It guides prospective customers through property and construction enquiries, answers general questions, handles voice notes, and captures structured lead details.

## Key capabilities

- WhatsApp Cloud API message handling
- Guided enquiry flows for Buy Land, Construction Only, Land + Construction, and Commercial Plot
- AI-powered responses using OpenRouter (`openai/gpt-4o-mini`)
- English, Malayalam, and Manglish conversation support
- Voice-note retrieval and transcription using Groq Whisper (`whisper-large-v3`)
- Conversation state and message de-duplication
- Indian PIN-code lookup
- Lead details formatted for a future/available CRM integration

## Architecture overview

1. Receive WhatsApp messages.
2. Detect voice notes, retrieve media, and transcribe audio when applicable.
3. Normalize inbound messages and distinguish customer messages from delivery-status events.
4. Drop duplicate or unsupported events.
5. Load per-sender conversation state.
6. Route menu selections and structured questions through deterministic state logic.
7. Invoke the AI agent for general property questions or interruptions.
8. Format and send the WhatsApp response.
9. Persist conversation state.

See [`documentation/architecture.md`](documentation/architecture.md) and [`documentation/setup-guide.md`](documentation/setup-guide.md).

## Repository contents

- `workflows/cadvin-property-assistant.n8n.json` — sanitized n8n workflow export
- `documentation/architecture.md` — workflow architecture and behaviour
- `documentation/setup-guide.md` — import and configuration notes
- `screenshots/` — selected workflow and WhatsApp screenshots

## Technology stack

n8n, WhatsApp Cloud API, OpenRouter, Groq Whisper, JavaScript Code nodes, and the Indian Postal PIN-code API.

## Important implementation notes

- This repository contains a workflow export, not a turnkey hosted service. You must configure your own n8n instance, WhatsApp app, API credentials, and provider settings.
- Credential references in the export are n8n credential IDs/names only; credentials themselves are not included.
- The workflow's CRM endpoint and mapping should be reviewed and configured for the target CRM before production use. Do not assume CRM persistence succeeds merely because the conversation finishes.
- Test with non-sensitive sample data before connecting real customer conversations.

## Security

Never commit access tokens, API keys, exported credentials, real customer phone numbers, private property records, or production `.env` files. Use placeholders and synthetic examples in public repositories.

## License

No license is specified. All rights remain with their respective owners unless a license is added.
