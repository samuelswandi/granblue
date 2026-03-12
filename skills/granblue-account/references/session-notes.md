# Session Notes

## 2026-03-12

- The isolated Playwright Chrome profile can load `https://game.granbluefantasy.jp/`, but the game runtime reports `Game.isLoggedIn = false`, `Game.userId = 0`, and redirects `#mypage` back to `#top`.
- The user's live app/browser session can reach `https://game.granbluefantasy.jp/#mypage`. A screenshot shows the logged-in home screen rather than the public landing page.
- Prefer opening the real app/browser session when the user wants account inspection from their existing login state.
- Treat the app-first route as the default workflow for this repo unless the user explicitly wants a fresh automation session.
- If deeper automated inspection is needed later, the practical options are:
  - user-driven screenshots/navigation in the live app, or
  - a browser launched with automation-friendly debugging enabled from the start.

## Existing-Browser Control Notes

- GitHub and Playwright docs point to the same viable approach: connect to an existing Chromium browser through Chrome DevTools Protocol (CDP).
- This is not generic control of any random already-open app window. It requires a Chromium-based browser session that exposes a debugging endpoint.
- The normal pattern is:
  - start Chrome with `--remote-debugging-port=9222`, then
  - attach with Playwright `chromium.connectOverCDP("http://localhost:9222")`
- This is suitable for read-only account inspection and clicking through character, weapon, and summon pages.
- Limitation: if the current browser/app was not launched with remote debugging enabled, Playwright usually cannot attach to that already-running session retroactively.
