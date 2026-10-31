# Workflow architecture

## Inbound message path

`WA - Trigger` receives WhatsApp events. Voice messages pass through media URL retrieval, audio download, Groq transcription, and transcript merging. Text and transcribed messages converge at `WA - Normalize Incoming`.

`WA - Duplicate Check` and `WA - Is Duplicate?` prevent repeated processing. Valid messages proceed through conversation-state loading and routing.

## AI and response path

`AI - Property Agent` uses an OpenRouter chat model, simple conversation memory, and an Indian PIN-code lookup tool. `WA - Action Router` routes messages into normal response, AI-response, lead-completion, or no-op handling. `AI - Format AI Response` prepares free-text replies, and `WA - Send Response` sends the WhatsApp message.

## Structured enquiry flows

The workflow uses deterministic state logic for four enquiry types:

- Buy Land
- Construction Only
- Land + Construction
- Commercial Plot

It collects relevant requirements progressively, using WhatsApp buttons, lists, and text answers. Conversation state is maintained per WhatsApp sender.

## Lead and CRM path

The export includes early-capture and qualified-lead mapping/push paths, create/update routing, and push-result logging. The CRM endpoint is replaced with a placeholder in this public export. Configure and test it against an authorized CRM before use.

## Language and voice support

The AI instructions specify English, Malayalam, and Manglish responses. Voice notes are transcribed using Groq Whisper (`whisper-large-v3`) before entering the normal message path.

## Security boundary

Credential objects, webhook identifiers, pinned execution data, client CRM host, and the phone-number ID have been removed or replaced. The exported workflow still requires fresh credentials and IDs to be configured in your own n8n instance.
