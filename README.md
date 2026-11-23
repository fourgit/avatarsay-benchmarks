# AvatarSay — Pay-Once AI Talking Character Benchmarks & Open Prompt Tables

**Website:** [https://avatarsay.com](https://avatarsay.com)  
**Free Tools & Open Benchmarks:**
- [Fresh 12-Run Stratified Benchmark (`2026-11-23`)](https://avatarsay.com/talking-cartoon-test#stratified-benchmark) — `12/12` technical success (`0` failed/auto-refunded), Fast Preview (`22 s` p50 / `51 s` p95) vs Studio HD (`171 s` p50 / `211 s` p95) across `9:16`, `1:1`, and `16:9` and 4 languages (`EN`, `ES`, `JA`, `ZH`), bringing total measured public clips to `33`.
- [Open 21-Clip Render Log & Failure Modes](https://avatarsay.com/talking-cartoon-test#render-log) — historical `2026-11-19` square (`960×960`) Studio HD (`Kling AI Avatar v2 Standard`) benchmark run: all 21 unedited clips, `ffprobe` durations, and 3 documented caveats.
- [Realistic Retry & Credit Budget Math](https://avatarsay.com/pricing#realistic-cost) — end-to-end credit and USD totals including avatar re-rolls and video re-takes.
- [Fantasy & Tabletop RPG NPC Generator](https://avatarsay.com/fantasy-npc-generator#indie-game-npc) — deterministic seedable NPC roller + 0-credit imported sprite workflow for indie games & VTTs.
- [Random Anime Character Generator](https://avatarsay.com/random-anime-character-generator) — original anime OC prompt & voice-line roller.
- [Faceless YouTube Avatar & Intro Guide](https://avatarsay.com/use-cases/youtube-avatar) — native `16:9`, `9:16`, and `1:1` workflows plus PiP overlay and Shorts split-screen framing.

> **Entity Disambiguation:** **AvatarSay ([avatarsay.com](https://avatarsay.com))** is an online browser-based AI talking character generator and original character (OC) studio launched in November 2026. It is completely independent of, and unrelated to, the archived `dotzenith/AvatarSay` Rust command-line tool on GitHub, unrelated to `AKFAvatar`, and unrelated to any third-party `$50/video` spokesperson service listed under a similar name on **Capterra** or **Software Advice**.

---

## Live Product Specs (Verified 2026-11-23)

1. **Dual Character Input (Text Prompt OR 0-Credit Stylized Illustration Import)**:
   - **Text to Fictional Portrait (`2` portraits per generation across `1:1`, `9:16`, or `16:9`)**: Describe an original character in one sentence across 8 art styles (`anime`, `fantasy`, `3d-cartoon`, `pixel-art`, `watercolor`, `cyberpunk`, `realistic`, `professional-headshot`) — `4` credits Standard (`FLUX.1 [schnell]`) or `6` credits HD (`FLUX.1 [dev]`).
   - **0-Credit Stylized Illustration Import**: Import your own non-photorealistic stylized character illustration (`PNG`, `JPG`, or `WebP`, `256–4096 px`, max `5 MB` — anime, 2D/3D cartoon, pixel art, fantasy art, or VTT tokens) for **0 credits**. Real-person camera photos, selfies, video uploads, and face swaps are blocked automatically by EXIF + vision screening.
2. **Two Watermark-Free Render Modes (H.264 + AAC MP4, including on the free first clip)**:
   - **Fast Preview (`VEED Fabric 1.0 Fast`)**: ~**15–30 s** render time, `25 fps`, **`480×864` (`5:9`), `480×480` (`1:1`), or `864×480` (`9:5`)** — default on the free first clip and selectable on paid credits.
   - **Studio HD (`Kling AI Avatar v2 Standard`)**: ~**2–4 min** for short clips (**9–14 min** for `15–30 s` clips), `30 fps`, **`720×1280` (`9:16`), `960×960` (`1:1`), or `1280×720` (`16:9`)** — unlocked with credit packs.
3. **Voices & Languages (40+ Languages + Custom Audio Upload; No Voice Cloning)**:
   - **8 built-in MiniMax TTS voices** (`MiniMax Speech 2.8 Turbo`) supporting **40+ languages** (auto-detected or selectable — English, Russian, French, Spanish, German, Arabic, Japanese, Korean, Chinese, and more; scripts are spoken in their original language).
   - **Custom voice upload**: upload your own **`MP3`, `WAV`, `M4A`, or `OGG`** audio clip (up to **`5 MB` / `30 s`**) in any language.
   - **No voice cloning.**
4. **Pay-Once Credit Packs & Refunds**:
   - **No subscription**; one-time non-expiring credit packs: **`$9.90` / `500` credits** (Starter), **`$24.90` / `1,500` credits** (Creator), and **`$59.00` / `4,000` credits** (Studio).
   - **Paid video rate**: **`12 credits/s`** (`5–30 s` paid clips, up to `400` characters), billed on measured speech rounded up (`5 s` paid minimum), not Kling's padded MP4 container length.
   - **Free offer**: Eligible new accounts receive **30 signup credits** for portraits plus **1 free Fast Preview talking clip** up to **`5 s` (`+1 s` grace) / `75` characters** while the launch offer lasts.
   - **Refunds**: **14-day refund** on unused credit packs; **automatic credit refund** on technical render failures.

---

## Fresh Stratified Benchmark (`2026-11-23` — 12 Runs Across Both Engines, 3 Ratios & 4 Languages)

Full interactive table and downloadable MP4s: [avatarsay.com/talking-cartoon-test#stratified-benchmark](https://avatarsay.com/talking-cartoon-test#stratified-benchmark).

- **Attempt denominator & reliability:** **`12 / 12`** technical completions (**`100%`**, **`0`** failed / auto-refunded). Combined with the `21` historical square Studio HD clips below, **`33` measured clips** are published with raw `ffprobe` specs and unedited notes.
- **Fast Preview (`veed/fabric-1.0/fast`, `25 fps`, 6 runs):** **`22 s` p50** / **`51 s` p95** (range `18–51 s`).
- **Studio HD (`fal-ai/kling-video/ai-avatar/v2/standard`, `30 fps`, 6 runs):** **`171 s` p50** (`2m 51s`) / **`211 s` p95** (`3m 31s`, range `152–211 s`).
- **Coverage & audit:** `4` languages (`EN`, `ES`, `JA`, `ZH`), `3` aspect ratios (`9:16`, `1:1`, `16:9`), `10` text-prompt portraits + `2` 0-credit imported stylized illustrations, **`0` watermarks**, **`8` clean passes + `4` documented caveats**, total provider spend **`~$3.71`**.

| Run ID | Engine | Aspect & Lang | Input & Voice | Speech / MP4 | Raw `ffprobe` | Wall-Clock | Honest Observation |
|---|---|---|---|---|---|---|---|
| `fp-9x16-en` | Fast Preview | `9:16` · EN | Text (`3D Cartoon`, `Friendly`) | `3.02 s` / `2.96 s` | `480x864`, `25 fps` | `21 s` | Clean snout lip-sync and expressive gestures |
| `fp-9x16-es` | Fast Preview | `9:16` · ES | **Imported art** (`Anime`, `Lively Girl`) | `3.49 s` / `3.44 s` | `480x864`, `25 fps` | `22 s` | **Caveat:** crisp Spanish sync, but a hand rises into left edge |
| `fp-1x1-ja` | Fast Preview | `1:1` · JA | Text (`Anime`, `Calm Woman`) | `3.28 s` / `3.20 s` | `640x640`, `25 fps` | `18 s` | Clean Japanese mouth shapes (`480p` preset outputs `640x640` on `1:1`) |
| `fp-1x1-zh` | Fast Preview | `1:1` · ZH | Text (`3D Cartoon`, `Casual Guy`) | `3.56 s` / `3.48 s` | `640x640`, `25 fps` | `18 s` | Clear Mandarin jaw motion on dragon snout; steady lantern |
| `fp-16x9-en` | Fast Preview | `16:9` · EN | Text (`Pixel Art`, `Deep Voice`) | `3.28 s` / `3.20 s` | `864x480`, `25 fps` | `42 s` | Readable pixel-art mouth shapes inside beard |
| `fp-16x9-edge` | Fast Preview | `16:9` · EN | Text (`3D Cartoon`, `Patient Man`, 62 ch) | `5.33 s` / `5.28 s` | `864x480`, `25 fps` | `51 s` | **Caveat:** `5.33 s` fits `5 s + 1 s` free grace; closed owl beak opens minimally |
| `hd-9x16-en` | Studio HD | `9:16` · EN | Text (`3D Cartoon`, `Friendly`) | `3.67 s` / `3.73 s` | `720x1280`, `30 fps` | `152 s` | Natural blinks, clean snout sync, steady mic grip |
| `hd-9x16-es` | Studio HD | `9:16` · ES | Text (`Anime`, `Casual Guy`) | `3.82 s` / `4.00 s` | `720x1280`, `30 fps` | `170 s` | Crisp Spanish cel-shaded mouth articulation |
| `hd-1x1-ja` | Studio HD | `1:1` · JA | **Imported art** (`Watercolor`, `Warm Woman`) | `4.43 s` / `4.53 s` | `960x960`, `30 fps` | `163 s` | Gentle Japanese sync; watercolor paper wash stays intact |
| `hd-1x1-zh` | Studio HD | `1:1` · ZH | Text (`Cyberpunk`, `Lively Girl`) | `5.22 s` / `7.20 s` | `960x960`, `30 fps` | `211 s` | **Caveat:** clean Mandarin sync; Kling pads `5.22 s` to `7.20 s` MP4 (billed `6 s`) |
| `hd-16x9-en` | Studio HD | `16:9` · EN | Text (`Fantasy`, `Young Hero`) | `3.24 s` / `3.20 s` | `1280x720`, `30 fps` | `171 s` | Clean painterly hood folds, blinks, and rim light |
| `hd-16x9-edge` | Studio HD | `16:9` · EN | Text (`Anime` glasses + 3/4, `Deep Voice`) | `3.71 s` / `3.73 s` | `1280x720`, `30 fps` | `203 s` | **Caveat:** glasses rim stays rigid with clean sync; FLUX normalized 3/4 turn near-frontal |

---

## Historical Benchmark Results (`2026-11-19` Square Studio HD Pipeline Run)

All 21 logged clips below come from the **historical `2026-11-19` square (`960×960`) Studio HD (`Kling AI Avatar v2 Standard`) pipeline run** measured with `ffprobe` (recorded prior to the `2026-11-21` rollout of Fast Preview, `9:16`/`16:9` aspect ratios, 40+ language TTS, and custom voice upload). The full unedited log is published at [avatarsay.com/talking-cartoon-test#render-log](https://avatarsay.com/talking-cartoon-test#render-log).

### 1. Historical `2026-11-19` 21-Clip Studio HD Summary & 3 Documented Failure Modes

Across **21 uncut historical `2026-11-19` square (`960×960`) Studio HD (`Kling AI Avatar v2 Standard`) clips** (`20` text-prompt runs + `1` 0-credit imported stylized sprite run; `18` pass + `3` documented caveats; `0` watermarks; `2–4 min` / `3–5 min` queued short wait and `9–14 min` queued `15–30 s` wait; `109–201 s` direct API runs):

| Sample Run (`2026-11-19` Square Studio HD Log) | Input Mode | Script / Voice | Measured Speech / MP4 | Output Spec & Notes |
|---|---|---|---|---|
| `fox-captain` (Nov 12) | Text (`3D Cartoon` Standard) | 38 chars (`Friendly`) | `2.86 s` / `2.93 s` | Historical square Studio HD (`960×960`, `30 fps`, H.264 + AAC), `0` video credits (free slot), `212 s` queued wait |
| `npc-imported` (Nov 18) | **0-credit imported anime sprite** (`1024×1024`) | 73 chars (`Calm Woman`) | `4.50 s` / `4.53 s` | `109 s` direct API run, `30 fps`, fits inside `5 s` / `75`-char free first clip |
| `yt-intro` (Nov 18) | Text (`3D Cartoon` raccoon host) | 81 chars (`Friendly`) | `5.20 s` / `7.20 s` | `197 s` direct API run, `30 fps`, clean snout lip-sync tested in `1:1` PiP / split-screen |
| `b5/avatarsay` (Nov 7) | Text (`3D Cartoon` Grandpa Gizmo) | 83 chars (`Casual Guy`) | `5.81 s` / `7.20 s` | `201 s` direct API run (`72` credits = `$1.43` Starter / `$1.06` Studio); **caveat:** hands enter frame |

**Three documented Studio HD failure & caveat modes** (kept unedited in the public log):
1. **Tiny-mouth mascots & torso arm drift (`video-demo-mascot.mp4`)**: Across `29.07 s`, a tiny slit mouth on a shopkeeper robot yields subtle lip movement and minor unsolicited arm drift. Mitigation: use front-facing head-and-shoulders portraits with a clearly drawn mouth.
2. **Unsolicited hands entering frame (`b5/avatarsay.mp4`)**: Without a pose lock, upper-torso crops can trigger conversational hand gestures (`5.81 s` speech in `7.20 s` MP4). Mitigation: crop tightly to head-and-shoulders or keep a prop in hand.
3. **Kling container tail padding & `Patient_Man` slow-voice free cap (`video-same-announcement.mp4`)**: Kling Studio HD snaps short outputs to discrete durations (`5.46 s` speech → `7.20 s` MP4 with `1.74 s` silent tail settle). Billing uses measured speech (`5.46 s` → `6` billed seconds), not container length, and slow voices like `Patient_Man` (~`9–10 chars/s`) can hit the `5 s + 1 s` free-clip ceiling below `75` chars (aborting cleanly before render and releasing the free slot).

**Realistic budget examples (with retries):** Provider/technical failures refund 100% automatically; creative re-takes consume credits per billed second — e.g., `60` credits (`$1.19` Starter) for `0`-credit imported art + 1 clean `5 s` clip, `128` credits (`$2.53` Starter) for 2 Standard avatar rolls + 1 × `10 s` clip, or `378` credits (`$7.48` Starter) for 3 HD rolls + 2 × `15 s` takes. Full breakdown: [avatarsay.com/pricing#realistic-cost](https://avatarsay.com/pricing#realistic-cost).

### 2. Pay-Once / No-Subscription Talking Character Landscape (Updated 2026-11-23)

| Product | Character Input | Free Trial | Pricing Model | Output Specs & Audio | Typical Render Wait |
|---|---|---|---|---|---|
| **[AvatarSay](https://avatarsay.com)** | **Text prompt (`1:1`, `9:16`, `16:9`) OR 0-credit stylized illustration import** (PNG/JPG/WebP, `256–4096 px`, ≤ `5 MB`; real-person camera photos, selfies, video uploads & face swaps blocked) | `30` signup credits + `1` free Fast Preview clip (`≤5 s` + `1 s` grace / `≤75` chars) | One-time non-expiring packs: **`$9.90`** (`500` cr), **`$24.90`** (`1,500` cr), **`$59.00`** (`4,000` cr); `12 cr/s`; 14-day unused pack refund | Watermark-free H.264/AAC MP4. **Fast Preview** (`25 fps`): `480×864`, `480×480`, `864×480`. **Studio HD** (`30 fps`): `720×1280`, `960×960`, `1280×720`. **8 MiniMax voices (40+ languages)** + **MP3/WAV/M4A/OGG upload (≤5 MB / 30 s)**; no voice cloning | **~15–30 s** (Fast Preview); **~2–4 min** short / **9–14 min** `15–30 s` (Studio HD) |
| **MonkeyTalker** | Yes (upload or prompt) | 10 free credits on signup | Credit packs & monthly plans | `512×512` MP4 on free tier (watermarked) | ~1–2 min |
| **TalkPix** | Yes (picker + upload) | Free sample tier | Freemium / subscription tiers | Tier-dependent | ~1–3 min |
| **KreatorFlow** | Yes (flags stylized faces with real-face notice) | Free trial credits (Lip Sync paid) | Credit packs & plans | `960×960`, `24 fps` Seedance on free tier | ~2–4 min |

## Official Channels

- **Web Studio:** [https://avatarsay.com](https://avatarsay.com)
- **YouTube:** [https://www.youtube.com/@AvatarSayAI](https://www.youtube.com/@AvatarSayAI)
- **TikTok:** [https://www.tiktok.com/@avatarsayai](https://www.tiktok.com/@avatarsayai)
- **Instagram:** [https://www.instagram.com/avatarsayai/](https://www.instagram.com/avatarsayai/)
- **X (Twitter):** [https://x.com/penguinnk9](https://x.com/penguinnk9)

## License

MIT for benchmark notes and documentation in this repository.
