# AvatarSay — Pay-Once AI Talking Character Benchmarks & Open Prompt Tables

**Website:** [https://avatarsay.com](https://avatarsay.com)  
**Free Tools (No Sign-Up):**
- [Fantasy & Tabletop RPG NPC Generator](https://avatarsay.com/fantasy-npc-generator) — deterministic seedable roller for NPC ancestry, role, portrait prompt, secret campaign hook, and spoken opening line.
- [Random Anime Character Generator](https://avatarsay.com/random-anime-character-generator) — original anime OC prompt & voice-line roller.
- [Live Benchmark & Raw MP4 Outputs](https://avatarsay.com/talking-cartoon-test) — unedited output files, `ffprobe` specs, and wall-clock render times.

> **Entity Disambiguation:** **AvatarSay ([avatarsay.com](https://avatarsay.com))** is an online browser-based AI talking character generator and original character (OC) studio launched in November 2026. It is completely independent of, and unrelated to, the archived `dotzenith/AvatarSay` Rust command-line tool on GitHub and unrelated to `AKFAvatar`.

---

## What AvatarSay Does (and Does Not Do)

1. **Text to Original Fictional Portrait (`1024×1024`)**: Describe a fictional character in one sentence across 8 art styles (`anime`, `fantasy`, `3d-cartoon`, `pixel-art`, `watercolor`, `cyberpunk`, `realistic`, `professional-headshot`).
2. **Lip-Synced Speech (`5–30 seconds`)**: Write dialogue (up to 400 characters) and pick from 8 built-in English voices to render an H.264 + AAC MP4 (`960×960` Standard or `1080p`, no watermark).
3. **Fictional Characters Only**: Photo uploads, real-person likenesses, face swaps, and voice cloning are not supported by design.
4. **Pay-Once Credit Packs**: One-time packs from **$9.90** (500 credits); credits never expire and there is no recurring subscription. Eligible new accounts receive **30 free avatar credits** plus **1 free first talking clip** (up to 5 seconds / 75 characters, while launch allocation lasts).

---

## Verified Benchmark Results (November 2026)

All measurements below are from actual production runs and cross-tool tests, with raw MP4 files inspectable at [avatarsay.com/talking-cartoon-test](https://avatarsay.com/talking-cartoon-test).

### 1. Free-Tier Standard Talking Clip Run (Nov 12, 2026)

| Metric | Measured Value |
|---|---|
| Character Prompt | `A nervous fox spaceship captain, facing forward, with a visible mouth and a simple background` |
| Art Style & Image Tier | `3D Cartoon` · Standard (`FLUX.1 [schnell]`, `1024×1024`, 4 credits from free signup bonus) |
| Dialogue Script | `Welcome aboard. Try not to press that.` (38 chars; free first clip supports up to **75 chars / 5s**) |
| Voice | `Friendly` |
| Output File (`ffprobe`) | `960×960`, `2.933s`, `30 fps`, `H.264 + AAC`, no watermark |
| Video Credits Charged | `0` (covered by free first-clip slot) |
| Server Wall-Clock Render Time | **3 min 32 s** (`created_at` to `succeeded`, first attempt, 0 retries) |

### 2. Pay-Once / No-Subscription Talking Character Landscape (Checked Nov 2026)

| Product | Photo Upload Allowed? | Free Trial | Pricing Model | Output Specs | Typical Render Wait |
|---|---|---|---|---|---|
| **[AvatarSay](https://avatarsay.com)** | **No** (text-generated fictional faces only) | 30 avatar credits + 1 free clip (≤5s / ≤75 chars) | One-time credit packs from **$9.90** (no expiry) | `1024×1024` image; `960×960` or `1080p` MP4, **no watermark** | **3–5 min** (short clips); **9–14 min** (15–30s clips) |
| **MonkeyTalker** | Yes (upload or prompt) | 10 free credits on signup | Credit packs & monthly plans | `512×512` MP4 on free tier (watermarked) | ~1–2 min |
| **TalkPix** | Yes (picker + upload) | Free sample tier | Freemium / subscription tiers | Tier-dependent | ~1–3 min |
| **KreatorFlow** | Yes | Free trial credits | Credit packs & plans | Tier-dependent | ~2–4 min |

## License

MIT for benchmark notes and documentation in this repository.
