# Maddy's Math Party — Project Memory

Read this (and CLAUDE.md) at the start of every session.

## What this is
A math practice website for Maddy (6, niece) — addition & subtraction, themed around fashion dolls, surprise-ball dolls and squishy dumplings. Starts at numbers up to and including 12; a grown-up can raise the limit as she grows.

## Files
- `PRD.md` — product requirements doc (goals, features, future ideas).
- `index.html` — the whole game (HTML + CSS + vanilla JS, no install). Open it in any browser.
- `icon-180.png`, `icon-512.png` — app icon (Callie on pink) for iPhone/iPad "Add to Home Screen" and Windows.
- `manifest.webmanifest` — lets Edge on Windows install it as an app.
- `README.md` — GitHub front page with the play link.
- `.gitignore` — keeps Mac `.DS_Store` files out of git.
- `MEMORY.md` — this file.

## Where it lives
- **Play link (anyone can open):** https://mvprice3.github.io/maddy-math-party/
- **Code (public GitHub repo):** https://github.com/mvprice3/maddy-math-party — branch `main`; GitHub Pages serves the repo root of `main`.
- To update the live game: commit and push to `main`; Pages rebuilds in ~1 minute.

## Progress log
### Session 1 — 17 Nov 2026
- Wrote the PRD.
- Built v1 of the game in `index.html`:
  - Home: "Hi Maddy!", 3 worlds — **Dream Doll Studio**, **Surprise Ball Party**, **Squishy Dumpling Café**, each with its own hand-drawn SVG mascot, colours, counting emoji and cheers.
  - Rounds of 10 questions, 4 big multiple-choice answer bubbles, picture counters (rows of 5, crossed-out for take-away), read-aloud 🔊, confetti + chime sounds.
  - Wrong answer → gentle "try again"; 2 misses → shows the answer with explanation and a Next button.
  - End of round: stars + 1 new sticker (2 if 8+ stars). Sticker book with grey silhouettes for locked stickers (15 per world).
  - Grown-up settings behind a "hold for 2 seconds" gate: max number (5–100, default 11 → changed to 12, see below), add/subtract/both, questions per round, counters, auto-read, sound; progress stats; "ready for bigger numbers" nudge after 2 rounds of 9+ stars.
- Tested in the browser: home, play, wrong/reveal flow, full round → results, sticker book, settings, phone width (no horizontal scroll).

### Session 1 (cont.) — PRD v1.1 prototype
- Matt updated the PRD with two personal touches; both are built:
  - **Callie** — Maddy's Nova Scotia Duck Tolling Retriever (ginger coat, white blaze/chest/paws, pink collar, heart tag), drawn as an original SVG. She pops up from the bottom-right with a "woof woof" on every correct answer, saying **"Well done, Maddy!"** (spoken aloud too). Also on the home screen ("Woof! Pick a world, Maddy!" — tap her to say hi) and on the results screen.
  - **"With love from Uncle Matt"** — home screen footer, a handwritten-style love note on every results screen (rotating messages, special one for a perfect round), sticker book footer ("Every sticker is a little hug from Uncle Matt"), and spoken at the end of each round.
- Callie hides before the next question loads so she never covers an answer button.
- PRD bumped to v1.1.

### Session 1 (cont.) — PRD v1.2 changes (Matt's feedback)
- **Callie's "Well done, Maddy!" only at the end of a successful round** (≥ half the stars). Removed her pop-up from every correct answer — the world mascot cheers per answer instead. Below half: title "Great try, Maddy!", no Callie pop-up, encouraging note + spoken "Great try, Maddy!".
- **Callie's name always shown with her**: orange "🐾 Callie" name tag under her picture (home, results note) and "🐾 Callie says…" on her pop-up bubble.
- **Voice: British, female, more human.** The game now scores the device's voices and auto-picks the best en-GB female one (prefers Edge "Natural", Apple "Premium"/"Enhanced", Google UK English Female, Serena/Kate/Martha/Libby/Sonia; avoids male and novelty/robotic Apple voices like Flo, Shelley, Sandy, Grandma). Slightly slower and warmer (rate .92, pitch 1.05). Grown-up settings now have a **Voice picker + ▶︎ Test button** and a tip on downloading better voices.
- On Matt's Mac, auto-pick chose **Martha (en-GB)**. Serena/Kate aren't installed there.
- Tested: no Callie on a mid-round correct answer; no Callie on a failed round; Callie appears after a successful round; name tags show; voice picker lists voices.

### Session 1 (cont.) — PRD v1.3: iPhone, iPad and Windows
- **Target devices: iPhone, iPad (Safari) and a Windows computer (Edge/Chrome).** Added a "Target devices" section to the PRD (§7).
- iPhone/iPad: safe-area padding for notch/home bar; sounds play even with the silent switch on (`navigator.audioSession.type = 'playback'`, Safari 16.4+); sound + speech are unlocked on Maddy's first tap (iOS blocks audio until a tap); "Add to Home Screen" meta tags + Callie app icon.
- Layout: compact play screen on phones (max-width 699 & max-height 820); 4 answers in one row on wide screens (iPad, Windows); trimmed layout for wide-but-short screens. Measured: whole question incl. all 4 answers fits on iPhone SE in Safari (375×548), iPhone 15 (390×664), iPad landscape (1024×690), iPad portrait (820×1100), Windows laptop (1366×620). No sideways scrolling anywhere.
- Windows 10 emoji safety: swapped emoji newer than Emoji 12 (🫧→💫, 🪩→🎊, 🪞→👒, 🧋→🥤) — they'd show as empty boxes on Windows 10. All emoji now ≤ Emoji 12.
- **Not yet verified on a real iPhone/iPad** (silent-switch sound, first-tap unlock, voices) — needs a hosted link to test.
- **Hosting is now required**: iPhone/iPad/Windows can't open a file on Matt's Mac. → Solved with GitHub Pages (see below).

### Session 1 (cont.) — iPhone voice not playing (fix attempt)
- Matt: no voice on his iPhone, even after downloading Kate. Couldn't test on a real iPhone (no iOS simulator on this Mac), so fixed the known Safari/iPhone speech pitfalls:
  1. First question is now spoken **inside Maddy's tap** (iOS blocks speech not started by a tap; it used to be delayed 350 ms by a timer).
  2. Removed the blank "unlock" utterance and only call `speechSynthesis.cancel()` when something is actually speaking (Safari can drop speech queued straight after cancel).
  3. **Silent-voice fallback:** if a voice doesn't start within 2 s or errors, it's marked as bad on this device (`localStorage` key `maddyMathParty.badVoices`) and the next-best voice is tried (up to 2 retries). Some downloaded Enhanced/Premium voices are known to be silent in Safari.
- Grown-up settings → Voice: ▶︎ Test now shows a live status line ("✔ Speaking with Kate…", "… X didn't start — trying another voice", "✖ …"), the number of voices found, a "Can't hear the voice?" checklist (silent switch, media volume, close/reopen Safari after downloading voices, check Kate in iPhone Settings) and a "Re-check skipped voices" button.
- Likely phone-side cause to check: **silent switch** — Safari speech is often muted on silent even though game sounds play.
- Tested on Mac: fallback works when a voice is forced silent. **Still needs confirming on Matt's iPhone.**

### Session 1 (cont.) — Published on GitHub + GitHub Pages
- Matt isn't on a paid GitHub plan, so Pages needs a **public** repo (Pages from a private repo requires GitHub Pro). Matt chose **public**.
- Created `mvprice3/maddy-math-party` (public), pushed everything (game, icons, manifest, PRD, MEMORY, CLAUDE.md, README), turned on GitHub Pages from `main` /.
- Commits use Matt's GitHub noreply email (`…+mvprice3@users.noreply.github.com`) so his real email isn't in public history. Git name/email set for this repo only (no global git identity on his Mac).
- Checked live: page, icon and manifest load; a full round plays; progress and stickers save (localStorage works on the real web address, unlike the local file preview).
- Fixed a timing bug found on the live site: Callie's end-of-round pop-up (scheduled 0.9s after results) appeared on the home screen if Maddy tapped "New world" quickly. Now cancelled when she leaves the results screen.
- Still to do: try it on a real iPhone/iPad/Windows machine (sound on silent, first-tap unlock, voice quality).

### Session 1 (cont.) — PRD v1.5: fourth world, Callie's Puppy Park
- Matt asked for a **dog-themed fourth world** → **Callie's Puppy Park**. Callie is the world's mascot (with her "🐾 Callie" name tag on the play screen too), counters 🐶 + 🦴, park-green + toller-ginger colours, dog cheers ("Pawsome!", "Woof-tastic!", "Fetch-tastic!"…), 15 dog stickers (all Emoji ≤12 so they work on Windows 10; includes 🦆 because tollers are duck dogs).
- Home screen shows the 4 world cards **always as a centred 2×2 grid** (Matt didn't like a lone left-aligned card on the second row). Short screens get a tighter home layout so all four show without scrolling on laptops (1366×657), iPad and normal iPhones; only iPhone SE with Safari toolbars needs a small scroll.
- Fix: Callie's pop-up now disappears when Maddy leaves the results screen (it used to follow her to the sticker book).
- Tested: home on phone + iPad, a Puppy Park round (7 + 5 = 12 fits on iPhone SE), stickers awarded, Callie at the end, sticker book shows the new section.

### Session 1 (cont.) — PRD v1.4: up to and including 12
- Matt: the range should go **up to 12, including 12** (not "below 12"). Default max is now 12; the options are 5, 10, 12, 15, 20, 30, 50, 100 (11 removed). Anyone with 11 saved on their device is moved up to 12 automatically.
- Note: CLAUDE.md still says "below 12" — that's Matt's file; the PRD/game now follow his newer instruction (12 included).

## Key decisions
- **Single static HTML file**, no frameworks/server — easy to open on a tablet, works offline (font loads from Google Fonts but falls back to a rounded system font).
- **Original artwork only** (emoji + our own SVG drawings). Themes are *inspired by* Barbie / LOL Surprise / squishy dumplings but use no brand names, logos or characters — keeps it safe if ever shared publicly.
- **Multiple choice, not typing** — easier for a 6-year-old; typing mode is a v2 idea.
- **No timer, no red X, no losing** — always encouraging.
- **Subtraction never goes negative**; answers always stay within the chosen max.
- Progress saves in the browser's `localStorage` → it's **per device/browser**. Clearing site data resets it.
- Difficulty is raised by a grown-up (not automatically) — the app only *suggests* levelling up.

- Personal touches (Callie, Uncle Matt) are central to the brief — keep them prominent in any future change. The user is Uncle Matt; Callie is Maddy's dog.

## Learnings / takeaways
- Picture counters in rows of 5 (ten-frame style) help early counting; they auto-hide above 20.
- Read-aloud uses the browser's built-in voice — works on iPad/Chrome/Safari with no setup.
- Voice quality depends entirely on what's installed on the device. Browser voices can't be made truly human from code; the biggest win is downloading Serena (Premium) / Kate (Enhanced) on the iPad, or using Edge's Natural voices. A fully human voice would need recorded audio clips or a paid text-to-speech service (breaks the "no audio files / works offline" rule, so not done).
- "Success" for a round = at least half the stars (easy to change: `success` in `finishRound`).

## Ideas for next time
- v2 ideas in PRD §9: number-pad typing mode, missing-number problems, dress-up rewards, adaptive practice of tricky facts, multiple profiles.
