# VYRA Studio V3 — Two-page Claude prototype

## Pages
- `index.html`: prompt, mode, reference URL, optional file picker and voiceover preference.
- `result.html`: ONE Claude-generated creative plan, revision box, and TXT export.
- Full-screen loading overlay waits for a real API response.

## Cloudflare Pages deployment
1. Push **the contents of this folder** to a private Git repository.
2. In Cloudflare Dashboard > Workers & Pages > Pages, connect the repository as a Pages project. Set framework preset to None and output directory to the repository root (or configure build output to the folder containing `index.html`). Cloudflare Pages Functions are in `functions/api/generate.js`.
3. Set a server-side secret named `ANTHROPIC_API_KEY` in Pages project settings (for the relevant environment). Redeploy.
4. Open the deployed Pages URL and enter a prompt. The `/api/generate` endpoint will call Anthropic.
5. Optionally set `CLAUDE_MODEL` to an Anthropic model identifier available on your account.

## What is and is not real
- Claude API calls are real after correct deployment and API key configuration. This code has not been tested against a live API key.
- Claude returns one structured *creative plan*, not video, image, or audio files. The 'Download' button downloads a TXT plan.
- The file picker does not upload files to Claude; reference URLs are not fetched or inspected.
- No authentication, user accounts, admin dashboard, billing or video rendering are implemented.
- Projects live only in the current browser tab's sessionStorage; they are not synced or persisted on a server.

## Security
- Never place the Anthropic key in browser HTML/JS, GitHub, or chat. Use Cloudflare secrets.
- **Do not publicly launch this API without authentication, abuse controls and rate limiting.** Each call may incur costs.
- Claude API usage is billed separately from a Claude chat subscription.

## Local preview
Open `index.html` to inspect the design. Actual AI calls only work when deployed with the Pages Function and secret.
