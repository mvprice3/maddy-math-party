# Maddy's Math Party — Product Requirements Doc

**Version:** 1.5 · **Date:** 17 Nov 2026 · **Status:** prototype built (adds a fourth world: Callie's Puppy Park)

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
- **Questions per round:** 5 / 10 / 15.
- **Picture counters:** on / off (automatically hidden above 20).
- **Read questions aloud automatically:** on / off. **Sounds:** on / off.
- **Progress:** rounds played, total stars, accuracy over the last 5 rounds.
- **Level-up nudge:** after 2 rounds in a row with 9–10 stars, the grown-up area shows "Maddy is ready for bigger numbers!" with a one-tap "Make it harder" button.
- **Reset progress.**

## 6. Design principles
- **Tap targets ≥ 64px**, works on iPad/tablet first, phones and laptops too.
- **No reading needed** to play: icons, pictures, read-aloud.
- **Always encouraging:** no red X, no timer, no losing.
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
- Hosting options: open the file directly, or publish as a private link for Maddy's tablet.

## 9. Future ideas (v2+)
- Typing answers on a number pad (harder mode) once she's confident.
- Missing-number problems (`5 + ? = 9`) and number bonds.
- Dress-up reward: spend stars to dress a doll or decorate a dumpling.
- Gentle timed "speed challenge" mode for older Maddy.
- Adaptive difficulty that focuses on facts she gets wrong most.
- Multiple player profiles (siblings/cousins).

## 10. Success after 1 month
- Plays 3+ times a week without being asked.
- Comfortable with all facts up to 12, starting on 15 or 20.
