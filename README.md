# AvatarSay — Pay-Once AI Talking Character Benchmarks & Open Prompt Tables

**Website:** [https://avatarsay.com](https://avatarsay.com)  
**Free Tools & Open Benchmarks:**
- [Open 21-Clip Render Log & Failure Modes](https://avatarsay.com/talking-cartoon-test#render-log) — all 21 unedited Kling AI Avatar v2 Standard clips, `ffprobe` durations, and 3 documented caveats.
- [Realistic Retry & Credit Budget Math](https://avatarsay.com/pricing#realistic-cost) — end-to-end credit and USD totals including avatar re-rolls and video re-takes.
- [Fantasy & Tabletop RPG NPC Generator](https://avatarsay.com/fantasy-npc-generator#indie-game-npc) — deterministic seedable NPC roller + 0-credit imported sprite workflow for indie games & VTTs.
- [Random Anime Character Generator](https://avatarsay.com/random-anime-character-generator) — original anime OC prompt & voice-line roller.
- [Faceless YouTube Avatar & Intro Guide](https://avatarsay.com/use-cases/youtube-avatar) — framing `960×960` clips in `16:9` PiP overlays and `9:16` Shorts split-screens.

> **Entity Disambiguation:** **AvatarSay ([avatarsay.com](https://avatarsay.com))** is an online browser-based AI talking character generator and original character (OC) studio launched in November 2026. It is completely independent of, and unrelated to, the archived `dotzenith/AvatarSay` Rust command-line tool on GitHub, unrelated to `AKFAvatar`, and unrelated to any third-party `$50/video` spokesperson service listed under a similar name on **Capterra** or **Software Advice**.

---

## What AvatarSay Does (and Does Not Do)

1. **Dual Character Input (Text Prompt OR 0-Credit Stylized Illustration Import)**:
   - **Text to Fictional Portrait (`2 × 1024×1024`)**: Describe an original character in one sentence across 8 art styles (`anime`, `fantasy`, `3d-cartoon`, `pixel-art`, `watercolor`, `cyberpunk`, `realistic`, `professional-headshot`) — `4` credits Standard (`FLUX.1 [schnell]`) or `6` credits HD (`FLUX.1 [dev]`).
   - **0-Credit Stylized Illustration Import**: Import your own non-photorealistic stylized character illustration (`PNG`, `JPG`, or `WebP`, `256–4096 px`, max `5 MB` — anime, 2D/3D cartoon, pixel art, fantasy art, or VTT tokens) for **0 credits**. Real-person camera photos, selfies, video uploads, and face swaps are blocked automatically by EXIF and vision screening.
2. **Lip-Synced Speech (`960×960` Square MP4, Zero Watermark)**: Write dialogue (`5–30 seconds` paid, up to `400` characters) and pick from 8 built-in English voices (`MiniMax speech-2.8-turbo` + `Kling AI Avatar v2 Standard`). Output is strictly **`960×960` square (`1:1`), `30 fps`, H.264 + AAC MP4 with zero watermark** (including on the free first clip). Native `1080p`, `16:9`, and `9:16` exports, custom audio uploads, and voice cloning are not supported.
3. **Pay-Once Credit Packs**: One-time packs from **$9.90** (500 credits); credits never expire and there is no recurring subscription. Billing charges **`12 credits/s`** on measured speech rounded up (`5 s` paid minimum), not Kling's padded MP4 container length. Eligible new accounts receive **30 free avatar credits** plus **1 free first talking clip** (`≤ 5 s` speech + `1 s` grace, up to `75` characters, while launch allocation lasts).

---

## Verified Benchmark Results (November 2026)

All measurements below come from actual production and direct API runs measured with `ffprobe`, published in full at [avatarsay.com/talking-cartoon-test#render-log](https://avatarsay.com/talking-cartoon-test#render-log).

### 1. 21-Clip Measured Pipeline Summary & 3 Documented Failure Modes

Across **21 uncut Kling AI Avatar v2 Standard clips** (`20` text-prompt runs + `1` 0-credit imported stylized sprite run; `18` pass + `3` documented caveats; `0` watermarks; `3–5 min` queued short / `9–14 min` queued long wait, `109–201 s` direct API runs):

| Sample Run | Input Mode | Script / Voice | Measured Speech / MP4 | Output Spec & Notes |
|---|---|---|---|---|
| `fox-captain` (Nov 12) | Text (`3D Cartoon` Standard) | 38 chars (`Friendly`) | `2.86 s` / `2.93 s` | Unscaled `960×960`, `30 fps`, H.264 + AAC, `0` video credits (free slot), `212 s` queued wait |
| `npc-imported` (Nov 18) | **0-credit imported anime sprite** (`1024×1024`) | 73 chars (`Calm Woman`) | `4.50 s` / `4.53 s` | `109 s` direct API run, `30 fps`, fits inside `5 s` / `75`-char free first clip |
| `yt-intro` (Nov 18) | Text (`3D Cartoon` raccoon host) | 81 chars (`Friendly`) | `5.20 s` / `7.20 s` | `197 s` direct API run, `30 fps`, clean snout lip-sync for `16:9` PiP or `9:16` split-screen |
| `b5/avatarsay` (Nov 7) | Text (`3D Cartoon` Grandpa Gizmo) | 83 chars (`Casual Guy`) | `5.81 s` / `7.20 s` | `201 s` direct API run (`72` credits = `$1.43` Starter / `$1.06` Studio); **caveat:** hands enter frame |

**Three documented failure & caveat modes** (kept unedited in the public log):
1. **Tiny-mouth mascots & torso arm drift (`video-demo-mascot.mp4`)**: Across `29.07 s`, a tiny slit mouth on a shopkeeper robot yields subtle lip movement and minor unsolicited arm drift. Mitigation: use front-facing head-and-shoulders portraits with a clearly drawn mouth.
2. **Unsolicited hands entering frame (`b5/avatarsay.mp4`)**: Without a pose lock, upper-torso crops can trigger conversational hand gestures (`5.81 s` speech in `7.20 s` MP4). Mitigation: crop tightly to head-and-shoulders or keep a prop in hand.
3. **Kling container tail padding & `Patient_Man` slow-voice free cap (`video-same-announcement.mp4`)**: Kling snaps short outputs to discrete durations (`5.46 s` speech → `7.20 s` MP4 with `1.74 s` silent tail settle). Billing uses measured speech (`5.46 s` → `6` billed seconds), not container length, and slow voices like `Patient_Man` (~`9–10 chars/s`) can hit the `5 s + 1 s` free-clip ceiling below `75` chars (aborting cleanly before Kling and releasing the free slot).

**Realistic budget examples (with retries):** Provider/technical failures refund 100% automatically; creative re-takes consume credits per billed second — e.g., `60` credits (`$1.19` Starter) for `0`-credit imported art + 1 clean `5 s` clip, `128` credits (`$2.53` Starter) for 2 Standard avatar rolls + 1 × `10 s` clip, or `378` credits (`$7.48` Starter) for 3 HD rolls + 2 × `15 s` takes. Full breakdown: [avatarsay.com/pricing#realistic-cost](https://avatarsay.com/pricing#realistic-cost).

### 2. Pay-Once / No-Subscription Talking Character Landscape (Checked Nov 2026)

| Product | Character Input | Free Trial | Pricing Model | Output Specs | Typical Render Wait |
|---|---|---|---|---|---|
| **[AvatarSay](https://avatarsay.com)** | **Text prompt OR 0-credit stylized illustration import** (PNG/JPG/WebP ≤ 5 MB; real-person camera photos blocked) | 30 avatar credits + 1 free clip (≤5s / ≤75 chars) | One-time credit packs from **$9.90** (no expiry) | `1024×1024` image; strictly **`960×960` square** (`30 fps` H.264 + AAC MP4), **0 watermarks** | **3–5 min** (short clips); **9–14 min** (15–30s clips) |
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
