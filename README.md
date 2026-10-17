# Agent Council — iPhone GitHub Pages PWA (connection fix)

## Publish / update
1. Extract this ZIP.
2. Upload and replace **all files and folders** in the GitHub repository root, including `index.html`, `sw.js`, `manifest.webmanifest`, and `icons/`.
3. In GitHub: **Settings → Pages → Deploy from a branch → main → /(root)**.
4. Wait for deployment to finish. On iPhone, remove the old Home Screen shortcut, open the published HTTPS site in Safari, then **Share → Add to Home Screen** to refresh the icon and cached app.

## Connect free OpenRouter models
1. Create an OpenRouter API key at https://openrouter.ai/keys.
2. In Agent Council's Connections panel, paste the key.
3. Tap **Test API key**. The app sends a short test request using OpenRouter's documented `openrouter/free` router.
4. If the test succeeds, Live mode is enabled. The built-in cloud agents use `openrouter/free` by default so old invalid model IDs are migrated automatically. Their individual role prompts differ, but OpenRouter chooses the underlying free model for each request; these are not separate guaranteed model families.
5. If the test fails, the app shows the API error. HTTP 401 usually means the key is invalid/revoked; 402 can indicate balance/account restrictions; 429 means a rate limit. Free-model availability is not guaranteed and free usage is rate-limited.

## Important
- Demo mode produces simulated responses. Live mode is required for real model responses. Entering a key switches to Live mode; the Test API key button also enables Live mode.
- Free models can be temporarily unavailable or rate limited. Test again later if the API reports a provider/rate-limit error.
- Ollama is a separate local connection. `localhost` on an iPhone refers to the iPhone, not your Mac/PC. Use a reachable LAN address and appropriate network/CORS configuration.
- This static app stores the API key in browser local storage. Do not use it on a shared device; a secure backend proxy is safer for a production app. Never commit API keys to GitHub.
- GitHub Pages hosts static files only; it does not run a private server.
