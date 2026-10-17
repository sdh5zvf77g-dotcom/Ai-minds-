# Agent Council — GitHub Pages PWA

A mobile-friendly progressive web app based on the supplied Agent Council HTML, with your supplied blue brain image used for the iPhone icon. Includes an installable web-app manifest, offline app-shell caching, custom agent creation, and a public OpenRouter model-ID refresh helper.

## Publish to GitHub Pages
1. Create or open a GitHub repository.
2. Upload **all files and folders** in this package, keeping the `icons/` folder.
3. In **Settings → Pages**, choose **Deploy from a branch**, select your branch (usually `main`) and folder `/ (root)`, then Save.
4. Open the published HTTPS URL in Safari on your iPhone.
5. Tap **Share → Add to Home Screen**. If offered, enable **Open as Web App**, then tap Add.

## Connect models
- Choose **Live** in Backend.
- For OpenRouter, add an API key and set each agent's model ID to an ID available to your account. Use **Refresh OpenRouter model list** while online to fetch current public IDs; it does not verify account access or pricing.
- For Ollama, set the Ollama URL to an address reachable from the device. `http://localhost:11434` only refers to the device running the browser; on an iPhone, use a reachable Mac/PC LAN address and configure Ollama/network access appropriately. Browsers can block insecure cross-origin requests, so a secure HTTPS reverse proxy may be needed.
- Add custom agents using **+ Add agent**. Current built-in provider choices are OpenRouter and Ollama.

## Important limits and security
- This is a client-side app, not a secure multi-user service. API keys are stored in browser local storage by the existing app design. Anyone with access to that browser profile may be able to use them. Avoid shared/public devices; for stronger security, add a backend proxy and do not expose provider keys in client code.
- OpenRouter provides access only to models it lists and your account can use. This is not automatic access to every AI agent worldwide; separate providers may require their own API integration and credentials.
- GitHub Pages hosts static files only. It does not run a private server or proxy.
- Demo mode is simulated and does not contact real AI models. Live mode requires valid provider credentials, model IDs, connectivity and provider support.
- The service worker caches the app shell for reopening offline. Real model calls and model-list refresh require internet access.
