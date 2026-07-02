# Ask-Me chatbot Worker

Serverless proxy that holds the Anthropic API key and answers questions about Jinn using `kb.md` as context. Deployed independently of GitHub Pages — this folder is never served by the site itself.

## Deploy

```bash
cd worker
npm install -g wrangler   # if you don't have it
wrangler login
wrangler secret put ANTHROPIC_API_KEY   # paste your Anthropic API key when prompted
wrangler deploy
```

`wrangler deploy` prints the Worker's URL, e.g. `https://portfolio-chat.<your-subdomain>.workers.dev`.

## Wire it up to the site

Copy that URL into `ASK_ENDPOINT` in `index.html`'s "ASK CHATBOT" `<script>` block (currently a placeholder), then commit and push.

## Updating the knowledge base

Edit `kb.md` and redeploy with `wrangler deploy` — no code changes needed. Keep it in sync with `index.html` if you update your bio/experience/projects there.

## Config notes

- `ALLOWED_ORIGIN` in `wrangler.toml` restricts CORS to `https://jinnlk.github.io`. Update it if you ever move the site.
- The `RATE_LIMITER` binding caps each visitor IP to 10 requests/60s. If your Cloudflare account doesn't have the Rate Limiting API enabled, `wrangler deploy` will fail on that binding — just delete the `[[unsafe.bindings]]` block in `wrangler.toml`; `index.js` already checks for the binding's presence before using it.
- Guardrails (staying on-topic, declining unrelated questions) live in the `SYSTEM_PROMPT` in `index.js`, not in a separate config.
