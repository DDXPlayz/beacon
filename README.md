# Beacon

Log a good deed with a reflection, earn badges, keep a streak.

**[Live → beacon-two-omega.vercel.app](https://beacon-two-omega.vercel.app/)**

---

## What it is

A small personal tracker for deeds rather than habits. You record what you did
and write a short reflection on it; the app keeps a streak, awards points,
levels you up, and unlocks badges against four kinds of requirement — total
deeds, streak length, points and level. Twelve badges, from *On Fire* at a
three-day streak upward.

Everything lives in `localStorage` under one key. No account, no server, no
analytics, nothing leaves the browser.

**It is one file.** `src/BeaconApp.tsx` is 1,722 lines and holds the data
model, the badge rules, the state and every screen. That is a fair criticism of
it; it was built in one pass and never split.

---

## Why it exists

Habit trackers measure consistency, which is easy to count and easy to game. A
deed is not a habit — it is a thing you chose to do once, and the useful record
is *what it was and why*, not that a box got ticked. So the reflection is
required rather than optional, and the streak is a side effect of writing
rather than the point of the app.

---

## Stack

React 18, TypeScript, Vite, Tailwind, shadcn/ui (49 components vendored),
deployed on Vercel.

**The shell was scaffolded with Lovable** — layout, component library and
initial wiring. The badge system, the state model and the screens are written
on top of it.

---

## Getting started

```bash
git clone https://github.com/DDXPlayz/beacon.git
cd beacon
npm install
npm run dev
```

```bash
npm run build
npm run preview
```

No environment variables, no backend.

---

## Status & verification

**Status:** live, complete, not under active development. No tests.

| Claim | How it was checked |
|---|---|
| Live at `beacon-two-omega.vercel.app` | HTTP 200, checked 2026-11-21 |
| Builds from a bare clone | `npm install && npm run build` — **run, passes** |
| 12 badges across 4 requirement types | counted in the `BADGES` array; types are `deeds`, `streak`, `points`, `level` |
| Nothing leaves the browser | one `localStorage` key, no `fetch`, no backend |
| The shipped `TODO` is gone | `index.html` carried `<!-- TODO: Set the document title to the name of your application -->` in production; removed |

**Not verified:** no tests; the badge-unlock logic has not been exercised
against a constructed history. The storage key is `gooddeeds_user_data`, left
over from `good-deeds-journey`, which this project supersedes — renaming it
would discard the saved data of anyone already using the deployed app, so it
stays.

---

## Credits

Written by **Dhruva Goyal**. Scaffolded with Lovable. shadcn/ui components and
lucide icons are MIT.

Supersedes [`good-deeds-journey`](https://github.com/DDXPlayz/good-deeds-journey),
kept private as history.

---

## Licence

[MIT](LICENSE).
