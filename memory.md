# PORTFOLIO MEMORY — agent handoff file

> **Purpose:** single source of truth so any future agent can pick up exactly where the last one stopped.
> **Rule:** UPDATE this file every time you change `portfolio.html`, `admin.html`, or the CSS. Keep the card-link table in sync.
> **Last updated:** 2026-09-12 (UTC) — decoupled project links, fixed broken anchor, added this file.

---

## 1. Owner (DO NOT CHANGE personal information)

- **Name:** Christopher Victor Chinedu
- **Role:** Web Developer
- **Based:** Ilorin, Nigeria
- **Field:** Pharmacy and Technology
- **Focus:** HTML, CSS, JavaScript, Digital Solution
- **Interests:** Technology, Healthcare and Innovation
- **Goal:** Building useful digital solution
- **Phone/WhatsApp:** +2347079057773 → `https://wa.me/2347079057773`, `sms:+2347079057773`, `tel:+2347079057773`
- **Portrait:** `assets/images/port.png` (keep path, forward slashes)

Typos in prose may be fixed (e.g. "wed" → "web"), but facts, names, numbers, and project descriptions stay as the owner wrote them.

---

## 2. File inventory

| File | Role |
|---|---|
| `portfolio.html` | Public portfolio (single page). Edit here for live changes. |
| `pages/portfolio-file.css` | All styles. Mobile-first + breakpoints. |
| `admin.html` | Local-only CMS (PIN `1234`, front-end gate — NOT real security). Saves to `localStorage` key `cvc_admin_v1`. Cannot write files; use Export JSON / Copy snippet, then edit `portfolio.html` by hand. Keep OUT of public hosting. |
| `assets/images/port.png` | Owner portrait. |
| `memory.md` | This file. |

No build step, no dependencies, no CDN. Everything is vanilla HTML/CSS/JS with **inline SVG icons only** (zero emoji policy).

---

## 3. Design system

- **Palette (CSS vars):** `--brown:#7a2e1f` `--brown-dark:#4a1e16` `--brown-light:#b3684a` `--cream:#f8ebd1` `--bisque:#ffe4c4` `--cornsilk:#fff8dc` `--wheat:#f5deb3` `--ink:#231612` `--muted:#5b6470`
- **Favicon:** inline SVG data-URI (`<link rel="icon">` + `apple-touch-icon`), brown rounded square, bisque "CV". `theme-color #7a2e1f`.
- **Project thumbs:** 11 gradient classes, all brand-anchored (dark brown → accent → bisque/cornsilk): `thumb-bio, thumb-company, thumb-e1, thumb-geo, thumb-video, thumb-bolt, thumb-food, thumb-cart, thumb-fuel, thumb-news, thumb-music`.
- **Breakpoints:** base = mobile single-column; `min-width:480px` (buttons inline, form padding); `min-width:768px` (hero row, about 2-col, projects 2-col); `min-width:1024px` (projects 3-col); `max-width:600px` (hamburger + off-canvas nav); `max-width:360px` hardening; `prefers-reduced-motion` disables animation/tilt.
- **Tap targets:** ≥44px site-wide (footer links and socials included).

---

## 4. Feature inventory (how things work)

1. **Lock screen:** fullscreen overlay on load, live clock/date, swipe-LEFT (touch), drag-left (mouse), draggable knob (>60% of track), Tap button, `←`/`Enter`/`Space` keys. Slides away via `.unlocked`. `sessionStorage.portfolioUnlocked` persists across anchor nav; cleared on full reload (re-locks).
2. **Header/nav:** sticky glass. Desktop nav ALWAYS visible (`visibility:visible`). Mobile (`≤600px`) nav is off-canvas (`translateY(-140%)` + `visibility:hidden`) until `.open` via hamburger. Active link via IntersectionObserver.
3. **Hero:** badge, name, role, tagline, CTAs, stats (8 skills / 11 projects / 3 focus), portrait with glow + floating badges + mouse parallax.
4. **About:** 4 cards (Story / What I Do / Drives Me / Quick Facts).
5. **Skills (8 bars, `data-progress` driven):** HTML 85, CSS 90, UI/UX 90, Responsive 80, JavaScript 55, Python 80, Tailwind 80, Average 80. Average = (85+90+90+80+55+80+80)/7 = 560/7 = **80**.
6. **Projects (11 cards):** each card is a whole-card `<a class="project-card" data-tilt>` with `id="project-<slug>"` + `data-project="<slug>"` + `<!-- PROJECT n/11 -->` comment. See §6 table — each link is INDEPENDENT.
7. **Contact:** chips (WhatsApp / Call / location) + form. Submit → **Send via WhatsApp** (`wa.me` + `encodeURIComponent`, opens new tab); **Or send as SMS** (`sms:` URL, iOS `&body=` vs Android `?body=`). No backend.
8. **Footer:** 4 columns + bottom bar with auto-year + back-to-top button + toast.
9. **3D tilt:** vanilla JS on `[data-tilt]` (portrait, about, project cards, lock card) + glare span; pointer-only, skipped on touch/`prefers-reduced-motion`.

---

## 5. Change log

- **2026-09-11:** Full revamp (3 subagents): lock screen, glass header + hamburger, hero/stats, footer, 4 empty project slots, scroll-reveal, skill bars, toast, responsive system.
- **2026-09-11:** Replaced ALL emoji with inline SVG; Hire-me → `wa.me/2347079057773`; fixed `wa.me/+...` format; fixed `#` placeholder socials; added 3D tilt + parallax.
- **2026-09-11/12:** Owner added 8 project cards (Victok, Electricity, Food, E-commerce, Petroleum, Mapelo, Music + Banking/Pharmacy/E1/Biography edits). Agent then: WhatsApp+SMS dual form buttons; all cards → `onknow.com`; per-card SVG icons; UNIQUE tag sets; Python 80 + Tailwind 80 (avg stays 80); `admin.html` created; 4 empty cards removed from public → admin drafts; responsive audit patch; favicon; 11 distinct thumb gradients; fixed desktop nav hidden by `visibility` bug.
- **2026-09-12:** Crosscheck + decoupled card links (per-card `id`/`data-project`/comment); FIXED broken self-closed anchor on card 1; synced admin default link for Banking; created this `memory.md`.

---

## 6. PROJECT CARD LINK TABLE (keep in sync!)

Each card's URL lives ONLY in its own `<a id="project-…" href="…">` line (plus the matching `l:` in `admin.html` DEF). Changing one never touches the others. Owner is swapping them one after another.

| # | Title | `id` / `data-project` | Thumb | Tags (unique) | Current href | Status |
|---|---|---|---|---|---|---|
| 1 | Banking website | `project-banking-website` / `banking-website` | `thumb-bio` | HTML5, CSS3 | `https://victors-music.vercel.app` | ✅ CHANGED by owner |
| 2 | Pharmacy Hub | `project-pharmacy-hub` / `pharmacy-hub` | `thumb-company` | HTML, CSS, JavaScript | `https://onknow.com` | ⏳ pending |
| 3 | Room E1 website | `project-room-e1` / `room-e1` | `thumb-e1` | HTML5, Tailwind CSS, JavaScript | `https://onknow.com` | ⏳ pending |
| 4 | Biography | `project-biography` / `biography` | `thumb-geo` | HTML5, CSS, Python | `https://onknow.com` | ⏳ pending |
| 5 | Victok | `project-victok` / `victok` | `thumb-video` | HTML, Tailwind CSS, JavaScript | `https://onknow.com` | ⏳ pending |
| 6 | Electricity bill payment interface | `project-electricity-bill` / `electricity-bill` | `thumb-bolt` | HTML5, CSS3, JavaScript | `https://onknow.com` | ⏳ pending |
| 7 | Food ordering system | `project-food-ordering` / `food-ordering` | `thumb-food` | HTML, CSS3, Python | `https://onknow.com` | ⏳ pending |
| 8 | e commerce store with shopping cart | `project-ecommerce-store` / `ecommerce-store` | `thumb-cart` | HTML5, JavaScript, Python | `https://onknow.com` | ⏳ pending |
| 9 | Petroleum website | `project-petroleum-website` / `petroleum-website` | `thumb-fuel` | HTML, Tailwind CSS, Python | `https://onknow.com` | ⏳ pending |
| 10 | Mapelo | `project-mapelo` / `mapelo` | `thumb-news` | HTML5, Tailwind CSS, Python | `https://onknow.com` | ⏳ pending |
| 11 | Music store | `project-music-store` / `music-store` | `thumb-music` | JavaScript, CSS3, Python | `https://onknow.com` | ⏳ pending |

**How to change ONE card's link (3 steps, all required):**
1. `portfolio.html` — find `<!-- PROJECT n/11: … -->`, edit ONLY the `href` on the next line (`<a id="project-…"`).
2. `admin.html` — update the matching `l:"…"` in `DEF.projects` so admin stays in sync.
3. This file — flip the row's Status + Current href.

---

## 7. Crosscheck report (2026-09-12)

Checked: doctype/head/meta/favicon, lock, header/nav, hero, about, skills, projects, contact, footer, scripts, CSS, admin.
- ✅ `<div>` 102/102, `<section>` 5/5, `<a>` 34/34 balanced; 11/11 card ids + hrefs present.
- ✅ All 11 `thumb-*` classes used in HTML exist in CSS; all tag sets mutually unique; zero emoji (SVG only).
- ✅ Nav: desktop `visibility:visible`; mobile off-canvas hidden until `.open`. Favicon + `theme-color` present. No bare `href="#"`.
- 🐛 FOUND + FIXED: card 1 anchor was self-closed (`…data-tilt-max="8"></a>`) leaving card content outside the link + orphan `</a>` — restructured to proper open/content/close. (Likely caused by owner's manual link edit.)
- ⚠️ NOTE: card 1's URL (`victors-music.vercel.app`) sits on "Banking website" — looks possibly pasted onto the wrong card. Owner to confirm; agent did not move it.
- ⚠️ Section subtitle no longer names onknow.com (links now vary per card).

---

## 8. Rules for future agents

1. Never change §1 personal info. Never add emoji (inline SVG only, no CDN).
2. One card = one independent link (§6 procedure). Never `replaceAll` across cards for hrefs.
3. After edits, re-verify: tag balance (`<a>`/`<div>`/`<section>`), 11 card ids, thumb classes defined, no `href="#"`, form buttons wired (`btn-whatsapp`/`btn-sms`).
4. Keep `admin.html` DEF + preview in sync with `portfolio.html`; bump "Last updated" + Change log + §6 table here.
5. Test checklist before finishing: lock swipe (touch + mouse + keyboard), hamburger ≤600px, nav visible on desktop, skill bars animate, tilt ok, form → WhatsApp + SMS, footer year, 360px no horizontal scroll.

---

## 9. Pending / next steps

- [ ] Owner swapping card links one by one → update §6 rows as each lands (cards 2–11 still on `https://onknow.com`).
- [ ] Confirm card 1 URL vs title mismatch (Vercel music URL on Banking card?).
- [ ] Optional: real GitHub/LinkedIn profile URLs (currently `github.com/`, `linkedin.com/` placeholders); real contact email (currently only phone/WhatsApp); `og:image` meta.
- [ ] Keep `admin.html` off public hosting.
