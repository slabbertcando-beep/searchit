# SearchIT

A responsive, full-stack web search application with a clean search interface, live web results, category tabs, Namibia-first region selection, recent searches, dark mode, voice input (browser permitting), and optional AI-generated answers.

## Requirements
- Node.js 20 or newer
- npm
- Internet access for live search

## Run locally
1. Extract this folder.
2. Open a terminal in the project folder.
3. Run `npm install`.
4. Run `npm run dev`.
5. Open `http://localhost:5173`.

The Express API runs on port 8787 and Vite proxies `/api` requests to it during development.

## Enable AI answers (optional)
1. Copy `.env.example` to `.env`.
2. Add your own OpenAI API key to `OPENAI_API_KEY`.
3. Restart the server.

Keep the API key on the server. Do not put it in frontend code or commit your `.env` file.

## Production build
Run `npm run build`, then `npm start`. The Express server serves the built frontend and API on port 8787 (or the `PORT` environment variable).

## Search provider and limitations
Live search is retrieved server-side from DuckDuckGo's HTML search endpoint. Search results and availability are subject to that provider's access, layout, rate limits, and terms. It is not an independent search index like Google's. Category searches use the provider's category endpoints and may return different result coverage. For a commercial/public launch, replace the HTML adapter in `server/index.js` with a supported search API such as Brave Search or another provider, and review its licensing and rate limits.

AI answers are optional and require an OpenAI API key with API billing configured. Regular web search does not require an API key.

## Install on Android (PWA)
Once deployed over HTTPS, open the SearchIT website in Chrome on Android, tap the three-dot menu, then choose **Install app** or **Add to Home screen**. SearchIT includes a web app manifest, icons, and a service worker. Search queries still require an internet connection.

## Deploy on Render
The repository includes `render.yaml`. Push this folder to a GitHub repository, then create a Render Blueprint from that repository or create a Node web service with build command `npm install && npm run build` and start command `npm start`. Set `OPENAI_API_KEY` as a Render environment variable to enable AI answers. Do not commit secrets.
