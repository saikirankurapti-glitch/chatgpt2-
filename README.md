# GenQuantaa Academy Chatbot

A responsive, static website that embeds the **existing n8n chatbot workflow** using the official `@n8n/chat` frontend widget. No database or separate AI API key is required in the frontend.

## Quick start

Open `index.html` through a local HTTP server or deploy the repository to Vercel. For local development:

```bash
python -m http.server 3000
```

Then visit http://localhost:3000.

## n8n configuration

The chat widget connects to:

```text
https://genquantaa.app.n8n.cloud/webhook/a8ab8ab0-47a4-4353-9fd5-2edff4d02882/chat
```

In n8n:
1. Open your workflow, and check that **Chat Trigger** is configured for **Embedded Chat**.
2. In **Allowed Origins (CORS)**, add your deployed website domain (and `http://localhost:3000` for local testing), or use `*` for public testing if appropriate.
3. Make sure the workflow is **active/published** and the Chat Trigger is connected to a node that returns chat responses.
4. Verify that the production webhook URL above is still correct; if it changes, update `webhookUrl` inside `index.html`.

**Note:** If your workflow is set to **Hosted Chat** instead of **Embedded Chat**, switch to Embedded Chat first. The exact webhook must be a Chat Trigger-compatible endpoint. Browser/CORS or workflow configuration issues may prevent answers until n8n is configured.

## Deploy to Vercel

1. In Vercel select **Add New → Project**.
2. Import GitHub repository `saikirankurapti-glitch/chatgpt2-`.
3. Framework preset: **Other**. No build command needed. Output directory: leave default.
4. Click **Deploy**.
5. Add the resulting domain under n8n Chat Trigger allowed origins.

## Tech stack

- HTML, CSS and minimal JavaScript
- Official `@n8n/chat` frontend widget loaded from jsDelivr
- Existing n8n production Chat Trigger webhook

There are no API keys or credentials in the page. The webhook is publicly visible to browser visitors, as expected for embedded public chat. Add rate limits / abuse safeguards at the workflow or gateway layer for production use.
