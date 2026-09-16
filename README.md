# FacelessForge™ — The Faceless Forge™ System

**Build date:** 2026-09-16 · **Builder:** Archie (nightly digital-business builder) · **Budget:** $0 (all free tiers)

---

## The Niche (why now)

**The faceless AI content channel wave.** The single strongest breakout cluster in this run's trend scan —
the creator economy is being rebuilt around AI video automation, and the signal is unambiguous:

- **`Vincentwei1021/anything2explainer`** — *"Topic in, narrated explainer video out"* — **1,453★**, created
  **2026-09-08**. A Claude Code/Codex skill that turns any topic into a black-canvas motion-graphics explainer
  video (Remotion + TTS + subtitles). 1,453 stars in 8 days = the "faceless explainer video" trend going vertical.
- **`ayghri/i-have-adhd`** — *"A skill to stop your coding agent from burying the answer"* — **46,575★**,
  **17,880 stars this week alone** — the adjacent proof that AI-output tooling is the dominant theme of the week.
- **`lnkiai/m3e-canvas`** — 7,027★ — design → vibe-coding prompts (the design-to-content automation wave).
- The broader Remotion/TTS/image-gen ecosystem is making "one person, one laptop, one faceless channel"
  dramatically easier — exactly the tooling that powers the niche.
- Adjacent confirmation: `dream-loop` (agent 3D visuals), `holo-card-studio`, the entire "agent skill" economy.

**The gap:** the whole wave is optimising for **developers and tools**. Nobody is selling the **operator** —
the everyday person who wants a faceless channel that earns, but drowns in niche paralysis, blank-page
scripting, robotic voiceovers, and zero consistency. That's the exact info-product gap FacelessForge fills.

## The Business

- **Brand:** FacelessForge™ (a forge — you *forge* a channel, anonymously)
- **Product:** The Faceless Forge™ System — 8-part digital PDF system
- **Mechanism:** **Find → Forge → Flood** — three stages, in order: **FIND** (lock a paying niche in 60 min) →
  **FORGE** (build a 45-minute production line) → **FLOOD** (publish on a cadence the algorithm rewards).
  The core insight: faceless channels fail from **decision fatigue**, not talent — so the product removes the decisions.
- **Price:** $19 founder (anchor $97 → $39 after the first 100 founders)
- **Audience:** aspiring faceless creators, side-hustlers, and anyone who's been "about to start" a channel.
  20–45, no camera, no face, no "personality brand."

## Deliverables (8 PDFs in the pack)

1. **The Forge System** — core Find·Forge·Flood method + 30-day arc + 3 unbreakable rules
2. **The Niche Finder** — 12 proven niches + Demand/Supply/Monetization scoring matrix (60-min lock)
3. **The Script Factory** — 30 fill-in-the-blank scripts + 25-hook library + 3-act structure
4. **The Voiceover Pack** — copy-paste TTS prompts (ElevenLabs/OpenAI/PlayHT) + humanizer checklist
5. **The Thumbnail & Title Kit** — 9 title formulas + 4 thumbnail formulas + 8-point CTR checklist
6. **The Batch Playbook** — make 30 videos in a weekend (assembly-line method + schedule)
7. **The Publishing Tracker** — platform/timing/SEO field guide + analytics log
8. **The Monetization Cheatsheet** — 5 income streams in order + 90-day scale plan + media kit

## Working URLs

- **Landing page:** https://facelessforge-glow.vercel.app/ ✅ 200
- **Thank-you:** https://facelessforge-glow.vercel.app/thank-you ✅ 200
- **Downloads:** https://facelessforge-glow.vercel.app/download ✅ 200
- **Admin:** https://facelessforge-glow.vercel.app/admin ✅ 200
- **Payment link (Stripe TEST):** https://buy.stripe.com/test_00wfZicnm9Nh2vl50P1Nu0s

**Status:** ✅ SHIPPED & LIVE — full E2E verified.

## Repos

- **Public:** `getclients4u-lab/facelessforge` (branch `master`) — landing page, order stack, emails, VSL. **No PDFs.**
- **Private:** `getclients4u-lab/facelessforge-data` — `users.json`, `buyers.json`, `product/*.pdf` (8 PDFs).

## Order Stack (proven backend, adapted from gutmap)

- `api/webhook.js` — Stripe webhook → stores buyer, registers user, emails access code (AgentMail).
  Env var `FACELESSFORGE_MAIL_FROM`. Code prefix `FF-`.
- `api/hub.js` — verify + admin + authenticated PDF download. `ACCESS_PEPPER=facelessforge-pepper-eb60e22c`,
  `GH_DATA_REPO` default `facelessforge-data`.
- `api/verify.js`, `api/download.js`, `api/admin.js` — thin re-exports of hub handlers.
- `vercel.json` — proven config: `{version:2, cleanUrls:true, trailingSlash:false, headers:[...]}`. No `builds`/`routes`.

## E2E Verification (all passed)

| Check | Result |
|---|---|
| Signed Stripe webhook POST | `{"received":true,"stored":1,"registered":1,"emailed":true}` ✅ |
| Castle added via admin API | `ok:true` ✅ |
| Castle code verify | `{"ok":true,"name":"Castle"}` ✅ |
| Castle PDF download | 200 · `application/pdf` · real PDF ✅ |
| Wrong code | 403 ✅ |
| Public `/product/*.pdf` | 404 ✅ |
| Landing page | 200 ✅ |
| thank-you / download / admin | 200 / 200 / 200 ✅ |
| Command Center registration | OK ✅ |

**Post-E2E cleanup:** test buyer removed (Castle only), `buyers.json` reset to `[]`.

## Files

- `product/*.md` — 8 source markdown deliverables
- `pdf/*.pdf` — 8 rendered PDFs (39–55 KB each, 3–4 pages)
- `index.html` — long-form conversion landing page (hero → problem → mechanism → system → deliverables →
  for/not-for → price → FAQ → guarantee → close)
- `download.html` — 8-row member area with code gate
- `admin.html` — Orders / Users / Add User / Product Review tabs
- `thank-you.html` — post-purchase page → /download
- `emails/launch-emails.md` — 3-email launch sequence (teaser / launch / follow-up)
- `vsl/vsl-script.md` — 5-minute VSL script + 8-slide storyboard, targets the "topic → explainer video" trend
- `api/*.js` — the order stack
- `.buildenv` — build constants (slug, pepper, mail env var, code prefix)

## Gotchas hit & fixed this run

1. **POSIX `sh` has no brace expansion** — `mkdir -p {a,b,c}` creates a literal `{a,b,c}` dir. Use explicit `mkdir -p a b c`.
2. **`XDG_RUNTIME_DIR` must be 0700** or `wkhtmltopdf` fails with `QPainter::begin(): Returned false`. Fix: `chmod 700 /tmp/xdg`.
3. **`wkhtmltopdf` must never receive `.md` directly** — always `pandoc md → html`, then `wkhtmltopdf html → pdf`.
4. **Webhook email-body replacement** — replaced the template literal via precise start/end markers
   (`\`Welcome to GutMap™` … `— The GutMap Team\`;`) so the `const res = await fetch(...)` line was never touched
   (the known gotcha from the proofmark run). `node --check` PASSED and the fetch signature is intact.
5. **Fixed an upstream bug in admin.html** — order rows now show `o.ts` (the actual stored field) instead of the
   non-existent `o.date`, so order dates render correctly.

## Stripe (test mode)

- Product: `prod_VGnRWtBrTgl5Oj` · Price: `price_1UGFqtLJy1J1wtNpqYnzxYUX` ($19.00)
- Payment link: `plink_1UGFquLJy1J1wtNpLasP9g2P` → https://buy.stripe.com/test_00wfZicnm9Nh2vl50P1Nu0s
  (redirects to https://facelessforge-glow.vercel.app/thank-you)
- Webhook endpoint: `we_1UGFsLLJy1J1wtNp2W7wspZV` → https://facelessforge-glow.vercel.app/api/webhook
  (`checkout.session.completed`, `checkout.session.async_payment_succeeded`)

## Vercel

- **git-linked project:** `facelessforge` — `prj_ZOTqorFGvI9weepIupk28iM3xtLW`, `link.repo=facelessforge`
- **pre-deploy project:** `facelessforge-deploy` — `prj_FcY93tc3HmTf4one6Bo6Uf1bewRH`
- **Alias:** `facelessforge-glow.vercel.app` (primary) — `facelessforge.vercel.app` was taken
- SSO disabled on both. Env vars set on both.
