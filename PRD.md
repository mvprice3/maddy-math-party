# Maddy's Math Party — Product Requirements Doc

**Version:** 1.7 · **Date:** 19 Nov 2026 · **Status:** live as **v2** on 19 Nov 2026 (missing-number questions, Beat the Clock test mode, Progress tab for Maddy's mum)

## 1. Summary
A playful website where Maddy (age 6) practises addition and subtraction. It's wrapped in the things she loves — fashion dolls, surprise-ball dolls and squishy dumpling toys — so practice feels like play. Numbers start at up to 12, including 12 (where she is today) and a grown-up can raise the limit as she grows.

## 2. Goals
| Goal | How we'll know |
|---|---|
| Maddy *wants* to play | She asks to play again; finishes rounds without being pushed |
| Builds fluency with + and − | Accuracy and speed improve over weeks (stars per round go up) |
| Grows with her | Grown-up can raise the max number (12 → 15 → 20 → 50 → 100) in seconds |
| Zero frustration | No reading required to play; no "fail" screens; no negative answers |

**Non-goals (v1):** accounts/logins, multiplication, ads, online leaderboards, collecting any personal data.

## 3. User
- **Maddy (6):** early reader, taps more than types, short attention span (5–10 min), loves pink, sparkle, collecting, cute characters.
- **Grown-up (uncle/aunt/parent):** sets difficulty, checks progress, wants it to be safe and simple.

## 4. Themes ("Worlds")
Maddy picks one of **four worlds** each time. On the home screen they're always laid out **2 on top, 2 on the bottom**, centred, on every device. Original artwork only (emoji + drawn characters) — no brand logos or copied characters.

| World | Feel | Counting objects | Stickers to collect |
|---|---|---|---|
| **Dream Doll Studio** | Pink fashion-doll glam | 👗 👠 💄 👛 | dresses, crowns, convertibles, dream houses |
| **Surprise Ball Party** | Surprise-ball dolls, glitter, bows | 🎀 🍼 🎁 💫 | bows, bottles, surprise balls, glitter |
| **Squishy Dumpling Café** | Kawaii squishy dumplings | 🥟 🍡 🥤 🍙 | dumplings, boba, mochi, bao |
| **Callie's Puppy Park** | Dogs! Starring Callie, Maddy's toller, as the world's mascot. Park green + toller ginger | 🐶 🦴 | puppies, bones, tennis balls, frisbees, ducks (tollers love ducks), dog bed, kennel |

Each world has its own mascot, colours and cheer phrases.  Find a way to incorporate "With love from Uncle Matt" where possible to make it feel personal.

**Callie** (Maddy's dog) appears on the home screen, the results screen and in her end-of-round pop-up. **Whenever Callie is shown, her name is shown with her** (a "Callie" name tag, or "Callie says…" on her speech bubble).

## 5. Core features (v1)

### 5.1 Play a round
- A round = **10 questions** (grown-up can set 5 / 10 / 15).
- Question shown big: `7 + 3 = ?`, with **picture counters** underneath (e.g. 7 dumplings + 3 dumplings) when numbers are ≤ 20, so she can count.
- **Read-aloud button** 🔊 speaks the question ("Seven plus three"), auto-read optional.
- Answer by tapping one of **4 big answer bubbles** (multiple choice). Distractors are close numbers (±1, ±2) so it's real practice.
- **Correct:** confetti, happy sound, the world's mascot cheers, +1 star. (Callie does *not* pop up on each answer — her praise is saved for the end of the round, see 5.2.)
- **Wrong:** gentle wobble, "Almost! Try again" — wrong bubble fades out. After 2 misses the answer is shown with counters ("7 and 3 makes 10"), no star, move on.
- **Subtraction never goes below zero.**

### 5.1a Question styles (grown-up setting)
- **Classic** (default): `7 + 3 = ?` — the game exactly as it was.
- **Missing number** (fill in the blank): `7 + ? = 10`, `? + 3 = 10`, `10 − ? = 7`, `? − 3 = 7`. The second number is hidden more often (~70%) because it's the gentler form.
- **Mix of both**: about half classic, half missing number.
- The `?` box moves to wherever the blank is. Answer bubbles are built around the missing number.
- Read-aloud asks naturally: "7 plus *what* makes 10?", "10 take away *what* leaves 7?".
- Picture counters show the unknown part as red ❓ tiles (e.g. 7 dumplings + ❓❓❓). After 2 misses the full sum is shown in pictures and words ("7 + 3 makes 10!").
- Same stars, stickers and Callie praise as classic. The home-screen label and the progress history show which style was played.

### 5.2 End of round
- Stars earned (out of 10) and a **new sticker** for the world's sticker book (1 sticker for finishing, a bonus sparkly one for 8+ stars).
- **Callie's "Well done, Maddy!"** — Maddy's Nova Scotia Duck Tolling Retriever, Callie, pops up with a woof and says "Well done, Maddy!" (on screen and spoken) **only when Maddy succeeds**, i.e. earns at least half the stars in the round. Below that, Callie isn't shown popping up and the screen says "Great try, Maddy!" instead. Make it feel very personal.
- A note on the results screen signed "With love from Uncle Matt".
- "Play again" / "Pick a new world" / "My stickers".

### 5.3 Sticker book
- Grid of stickers per world; locked ones show as grey silhouettes so she has something to chase.
- Saved on the device (browser local storage).

### 5.4 Grown-up settings (behind a "hold for 2 seconds" gate)
- **Numbers up to:** 5, 10, **12 (default — up to and including 12)**, 15, 20, 30, 50, 100. Answers and both numbers stay within this limit, and the limit itself is included (e.g. 7 + 5 = 12 and 12 − 4 can appear).
- **Problem types:** Adding ➕ / Taking away ➖ / Both.
- **Question style:** Classic / Missing number / Mix of both (see 5.1a). Default Classic.
- **Questions per round:** 5 / 10 / 15.
- **Picture counters:** on / off (automatically hidden above 20).
- **Read questions aloud automatically:** on / off. **Sounds:** on / off.
- **Progress:** rounds played, total stars, accuracy over the last 5 rounds.
- **Level-up nudge:** after 2 rounds in a row with 9–10 stars, the grown-up area shows "Maddy is ready for bigger numbers!" with a one-tap "Make it harder" button.
- **Beat the Clock length:** 1 / 2 / 3 / 4 / 5 minutes (default 1). See 5.5.
- **Two tabs:** ⚙️ Settings and 📈 Progress (see 5.6).
- **Reset progress** (also clears Beat the Clock records and Progress history).

### 5.5 Beat the Clock (Test mode)
Requested by Maddy's mum: how many right answers in a set time. The sticker game stays as relaxed practice.
- **Always on the home screen** as "⏱ Beat the Clock" (gold button under the four worlds) showing her best for the current settings, e.g. "Best: 14 · 1 min". Grown-up settings call it "Test mode".
- **Length:** 1 minute by default; grown-up can choose up to 5 minutes.
- **Same difficulty as practice** (numbers up to, adding/taking away, classic/missing number).
- **3, 2, 1, Go!** then sums keep coming. **One tap per sum:** right → quick chime and straight to the next; wrong → the right answer shows for a moment, then the next sum. No second tries, so the score means something.
- Built for speed: no picture counters, no automatic read-aloud (🔊 still available).
- **Timer = Callie running towards a bone 🦴** along a **small, thin track in the top bar** — deliberately not big, to avoid undue pressure. Soft colours that never turn red, no flashing, no ticking numbers for Maddy (a tiny grey "time left" for grown-ups), gentle bone wiggle in the last 10 seconds, no buzzer. The sum and answers stay the biggest things on screen.
- If the device is put away mid-test, the clock pauses. Leaving a test early saves nothing.
- **Results:** "You got 14 right!" + "out of 17 tried". **New record** → 🏆 badge, confetti, Callie pops up: "Well done, Maddy! New record!". Otherwise: "Your best is 16. Try again?" (or "You matched your best!"). Note signed "With love from Uncle Matt".
- **Records are kept per setup** (length + numbers up to + type + style), so changing settings starts a fresh best.
- **No stickers** in Beat the Clock — stickers stay the reward for practice. Records appear as 🏆 trophies on a shelf in the sticker book.

### 5.6 Progress tab (for Maddy's mum)
In the grown-up area, next to Settings.
- **What's measured (from the first round after this update; earlier rounds had no timing):** for every sum — time from appearing to her first tap, whether that first tap was right, the sum itself, adding/taking away, classic/missing number, and the number limit.
- **Accuracy** = % right on first tap. **Speed** = typical (median) seconds per sum. **60-second rule:** sums that took longer than 60 s don't count toward speed (she was probably away from the screen) but still count for accuracy.
- **Headline numbers** for the chosen period (2 weeks / month / all): right first try, typical time per sum, sums answered — with change vs earlier days once there are 4+ play days.
- **Trend graph** appears after **3 play days with 10+ sums each**. One plot per play day; accuracy and seconds per sum; a marker where the number limit changed. Caption: **"One plot per day she played (days with 10+ sums)"**. Before that: "Trends appear after 3 days of play" with 1-of-3 progress dots and today's numbers.
- **By type** (adding, taking away, classic, missing number) and **trickiest sums lately** (tried 2+ times, missed at least once).
- **Beat the Clock scores:** graph with one plot per test at the current settings (gold = new record) and personal-best trophies. Test answers are kept separate from practice charts.
- Practice data only from this device (see 8).

## 6. Design principles
- **Tap targets ≥ 64px**, works on iPad/tablet first, phones and laptops too.
- **No reading needed** to play: icons, pictures, read-aloud.
- **Always encouraging:** no red X, no losing. **No timer in practice** — a timer appears only in Beat the Clock (5.5), and even there it's small and calm.
- Bright, pink-forward palette, rounded bubbly shapes, chunky friendly font.
- Short sessions: a round takes ~3–5 minutes.

## 7. Target devices
Maddy will play on **an iPhone or iPad (Safari)** or **a Windows computer (Microsoft Edge or Chrome)**.

| | iPhone / iPad (Safari) | Windows computer (Edge / Chrome) |
|---|---|---|
| Screen | iPhone: small portrait screen (iPhone SE 375×667 up to Pro Max). iPad: portrait **and** landscape (768×1024 up to 1366). A whole question — sum, counters and 4 answers — fits without scrolling. Respects the notch / home bar. | Laptop/desktop screen, mouse or touchscreen. Layout centred, max ~860px wide. |
| Sound | Sounds and voice must work **even when the ring/silent switch is on silent**, and must start from Maddy's first tap (iOS blocks audio until then). | Works as normal. |
| Voice | British female: Serena (Premium) / Kate (Enhanced) if downloaded, else Martha / Stephanie / Kate. | British female: Edge "Natural" voices (Libby, Sonia, Maisie) — most human; Chrome "Google UK English Female"; fallback Microsoft Hazel / Susan. |
| Feels like an app | "Add to Home Screen" gives a full-screen app with its own icon. | Can be pinned to the taskbar / Start from Edge ("Apps → Install this site as an app"). |
| Emoji | Apple emoji. | Only use emoji that also exist on Windows 10 (avoid newer ones that show as empty boxes). |

Because neither device can open a file stored on Uncle Matt's Mac, the game **must be hosted at a web address** (e.g. a private link) that both can open.

## 8. Technical
- Single static web page (`index.html`): HTML + CSS + vanilla JavaScript, **no install, no server, works offline** once opened.
- Sounds generated in the browser (Web Audio) — no audio files.
- Read-aloud via the browser's built-in speech (Speech Synthesis). **Voice: British, female, as natural/human as possible.** The game automatically picks the best British female voice on the device (preferring "Natural", "Premium" and "Enhanced" voices, and avoiding novelty/robotic ones), with a slightly slower, warm delivery. A grown-up can pick a different voice and test it in settings.
  - Voice quality depends on the device: on iPad/iPhone, download **Serena (Premium)** or **Kate (Enhanced)** under Settings → Accessibility → Spoken Content → Voices → English (UK). On a computer, Microsoft Edge's "Natural" voices (e.g. Libby, Sonia) and Chrome's "Google UK English Female" sound the most human.
- Progress & settings in `localStorage` (per device). No data leaves the device.
- **Updates never wipe progress:** the save name (`maddyMathParty.v1`) never changes; new settings and data are merged in with safe defaults and unknown fields are kept, so stars, stickers and history carry over when the live site is updated. On first load, v1.7 also stores a one-off backup of the old save (`maddyMathParty.v1.backup-before-tracking`), and an unreadable save is copied aside rather than overwritten. The game asks the browser to keep its data (`navigator.storage.persist()`).
- **Safari note:** Safari can clear a website's saved data if the site isn't opened for about 7 days of Safari use. Adding the game to the iPad/iPhone **Home Screen** protects against this.
- New saved data: `log` (one small entry per sum, capped at the latest 4,000), `tests` (Beat the Clock results), `bests` (personal bests per setup), `since` (when tracking started).
- Hosted on GitHub Pages: https://mvprice3.github.io/maddy-math-party/ (public repo `mvprice3/maddy-math-party`).

## 9. Future ideas (v2+)
- Typing answers on a number pad (harder mode) once she's confident.
- Number bonds (e.g. all the pairs that make 10). *(Missing-number problems are now built — see 5.1a.)*
- Dress-up reward: spend stars to dress a doll or decorate a dumpling.
- Adaptive difficulty that focuses on facts she gets wrong most.
- Multiple player profiles (siblings/cousins).

## 10. Success after 1 month
- Plays 3+ times a week without being asked.
- Comfortable with all facts up to 12, starting on 15 or 20.
