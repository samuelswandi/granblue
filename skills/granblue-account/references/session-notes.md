# Session Notes

## 2026-03-12

- The isolated Playwright Chrome profile can load `https://game.granbluefantasy.jp/`, but the game runtime reports `Game.isLoggedIn = false`, `Game.userId = 0`, and redirects `#mypage` back to `#top`.
- The user's live app/browser session can reach `https://game.granbluefantasy.jp/#mypage`. A screenshot shows the logged-in home screen rather than the public landing page.
- Prefer opening the real app/browser session when the user wants account inspection from their existing login state.
- Treat the app-first route as the default workflow for this repo unless the user explicitly wants a fresh automation session.
- If deeper automated inspection is needed later, the practical options are:
  - user-driven screenshots/navigation in the live app, or
  - a browser launched with automation-friendly debugging enabled from the start.
