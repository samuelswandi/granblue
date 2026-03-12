---
name: granblue-account
description: Track Granblue Fantasy account progress in this repo. Use when Codex needs to review the user's GBF account, document findings, keep a living account-state file, recommend next progression goals, or work from the user's live browser/app session instead of an isolated Playwright profile.
---

# Granblue Account

Prefer the user's live browser or app session over an isolated Playwright profile. The cloned Playwright Chrome profile can reach Granblue but has been redirected back to `#top` instead of entering the logged-in account.

## Workflow

1. Start from the live session first.
   - Prefer the user's existing app or real Chrome session when the goal is to inspect account progress.
   - Open `https://game.granbluefantasy.jp/#mypage` in the real app/browser if the user asks for the non-isolated path.
2. Fall back carefully.
   - Use isolated Playwright only when the user explicitly wants an automation sandbox or is willing to log in there manually.
   - Do not assume the isolated session can reuse the live app login state.
3. Document every pass.
   - Update `/Users/mac/Documents/adhoc/granblue/docs/account-state.md`.
   - Keep technical access notes in `references/session-notes.md`.
4. Separate evidence from inference.
   - Record only what is visible from screenshots, live pages, or explicit user statements as facts.
   - Label progression advice and account valuation as judgment calls.

## Account Review Checklist

For each element, capture:

- Main party and notable bench units
- Main summons and key sub summons
- Weapon grid direction and obvious gaps
- Visible power markers such as rank, AP/EP, currencies, and party strength when available
- Immediate next upgrades and longer-term goals

Use the six-element order in `/Users/mac/Documents/adhoc/granblue/docs/account-state.md`:

- Fire
- Water
- Wind
- Earth
- Light
- Dark

## Value Assessment

Use `references/evaluation-rubric.md` when the user asks for account value or what to do next.

Keep the judgment simple:

- `Early`: mostly starter grids, weak summon base, limited roster depth
- `Mid`: one or more coherent element teams/grids, some modern units/summons, clear upgrade path
- `Advanced`: multiple mature elements, strong summon coverage, efficient event/farm readiness
- `High-end`: broad endgame coverage, premium summon depth, flexible team building across content

## References

- Read `references/session-notes.md` for access behavior and app-first notes.
- Read `references/evaluation-rubric.md` for valuation heuristics and progression priorities.
