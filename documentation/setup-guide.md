# Setup and import checklist

1. Import `workflows/cadvin-property-assistant.n8n.json` into a test n8n instance.
2. Review node parameters and expressions for compatibility with your n8n version.
3. Create your own WhatsApp Trigger OAuth and HTTP bearer credentials in n8n.
4. Configure the WhatsApp Cloud API phone-number ID in the `WA - Send Response` node. The exported ID is a placeholder.
5. Configure your OpenRouter and Groq API credentials.
6. Replace the placeholder CRM URL with an endpoint you are authorized to use, and confirm its request schema and create/update behavior.
7. Verify webhook subscriptions, Graph API version, and messaging permissions.
8. Configure and test the PIN-code lookup tool.
9. Test text, interactive button/list replies, voice notes, duplicate delivery events, interruptions during structured flows, lead completion, and CRM failures using synthetic data.
10. Review logging and data retention before handling real customer information.

## Important

This repository is a portfolio artifact, not a hosted or one-click production deployment. It intentionally excludes credentials, client-specific identifiers, pinned execution data, and live CRM configuration. You must add your own configuration and validate the workflow in a test environment before production use.
