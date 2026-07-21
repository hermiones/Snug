**# Product Requirements Document

## **Snug** — The ADHD-first productivity app that wraps around your brain, not against it.

**Version:** 1.0 (MVP)
**Date:** July 2026
**Status:** Draft for Prototype

---

## 1. The Problem (Grounded in Research)

ADHD is not a deficit of attention — it is a disorder of **self-regulation and executive function** (Barkley, 1997). Research identifies four core breakdowns that no mainstream productivity app addresses:

| Breakdown | What the research says | What users experience |
|---|---|---|
| **Task initiation** | ADHD brains have hyposensitive dopamine neurons — tasks need to be novel, urgent, or interesting to generate activation energy (Positive Reset, 2026) | "I know what I need to do. I just can't start." |
| **Time blindness** | Dopamine dysregulation disrupts the brain's internal clock; people with ADHD cannot feel time passing (Mette et al., 2023; ADDA, 2023) | Losing 3 hours without noticing |
| **Working memory deficit** | ADHD impairs serial/temporal reordering (effect size d=1.34) and continuous updating (Barkley, 2015) | Forgetting a task the moment they close the app |
| **Energy fluctuation** | Executive bandwidth varies day to day — there is no "average day" for an ADHD brain | Doing 15 tasks Monday, 0 on Tuesday |

Standard productivity apps are built on **neurotypical assumptions**: stable willpower, consistent motivation, reliable working memory. They punish inconsistency through streaks, overdue badges, and missed-day resets — the exact experience ADHD users have the most. The result: the app gets deleted on the first bad day.

**Snug is different.** It acts as an external prosthetic for executive function — externalising the planning, the time awareness, and the activation energy that ADHD brains struggle to generate internally (Barkley, 2012; VOX Mental Health, 2026).

---

## 2. Product Vision

> **Snug wraps around your energy, not your schedule.**

An app that asks "how are you today?" before asking "what will you do today?" — then shrinks or expands its demands accordingly. On low days it becomes a comfort tool. On high days it becomes a power tool. It never shames, never streaks, never resets.

**Tagline:** *Do what you can, today.*

---

## 3. Target Users

**Primary:** Adults (18–45) diagnosed with or self-identifying as having ADHD.

**Secondary:** People with burnout, anxiety, or executive dysfunction who aren't ADHD-diagnosed but relate to the experience.

### Core Persona
**Rohan, 27, freelance designer with ADHD.**
Some days he hyperfocuses for 6 hours straight and ships incredible work. Other days he can't open his laptop. Every to-do app he's tried made him feel like a failure on his bad days. He stopped using them all. He needs an app that understands that Tuesday-him and Friday-him are different people — and that both deserve to feel okay.

---

## 4. The Science Behind Each Feature

### 4.1 Energy Check-in → *Addresses: energy fluctuation*
Research shows ADHD executive bandwidth is not constant (Barkley, 2015). Asking users to self-assess their state before planning activates metacognitive awareness — a CBT technique shown to improve self-regulation in adults with ADHD (Safren et al., 2017). Self-monitoring is a core pillar of CBT-based ADHD treatment.

### 4.2 Adaptive Task Load → *Addresses: working memory + task initiation*
Barkley (2012) explicitly recommends **externalising executive functions** — making regulatory demands live in the environment rather than the mind. Showing fewer tasks on low days reduces cognitive load. Research on task breakdown shows that "next smallest step" techniques remove activation energy barriers and create natural momentum (Positive Reset, 2026). On low days, Snug shows 1–3 pre-broken micro-tasks — steps so small they feel slightly silly, which is exactly the right size.

### 4.3 "Just Start" Timer → *Addresses: task initiation + dopamine*
The hardest part for ADHD brains is starting, not continuing. A 2-minute "Just Start" mode targets the initiation barrier directly. Once started, natural task engagement (hyperfocus potential) takes over. This mirrors the clinical recommendation: "Make the first 5 minutes ridiculously easy to start" (FLOWN, 2026). The timer uses progressive commitment — after 2 minutes it asks "keep going?" — so the user never feels trapped.

### 4.4 Streak-Free Habit Tracking → *Addresses: emotional dysregulation + shame cycles*
Streak mechanics actively harm ADHD users because inconsistency is neurological, not motivational. Removing streaks and replacing them with a total wins counter removes the shame trigger. This aligns with CBT-ADHD adaptations that deprioritise outcome metrics in favour of effort and participation (Safren et al., 2017).

### 4.5 Gemini AI — Smart Nudge + Task Suggester → *Addresses: working memory + time blindness*
The brain is designed for having ideas, not storing them — for ADHD brains this is doubly true (Brain.fm, 2026). Gemini (free tier) will act as an external working memory layer: suggesting what to work on based on the user's energy state and history, gently noting if 2 hours have passed with no check-in, and generating micro-step breakdowns from vague tasks like "finish report." This is digital scaffolding — the app carries the cognitive load the user's brain can't hold reliably.

### 4.6 Tiny Wins Library → *Addresses: dopamine + low-energy days*
On low-energy days, the goal is not productivity — it is **not breaking the habit of showing up**. Completing even one tiny win (drink a glass of water, reply to one message, stand outside for 2 minutes) triggers a small dopamine response and builds the identity that "I'm someone who uses this app." Over time this compounds. The tiny wins library is research-adjacent to behavioural activation therapy for depression, which has crossover evidence in ADHD (Safren et al., 2017).

---

## 5. Features (MVP)

### F1 — Daily Energy Check-in `[P0]`
- First screen every day: pick 🔥 High / 🌤 Medium / 🪫 Low
- One extra optional field: "What's draining you today?" (free text, optional, feeds Gemini)
- Can be updated any time during the day
- Skipping defaults to Medium — no penalty

**Acceptance criteria**
- ≤ 2 taps to complete check-in
- State visible as a soft colour tint throughout the app (not a badge or score)
- History stored locally; state resets at midnight

---

### F2 — Adaptive Task List `[P0]`
- **High energy:** full list visible; soft cap suggestion at 8 tasks ("You're in the zone — pick your top 3 in case energy shifts later")
- **Medium energy:** top 5 tasks shown; rest collapsed under "save for later"
- **Low energy:** only 1–3 Tiny Wins visible; big tasks hidden (not deleted)
- Tasks roll over silently — no "overdue" language, no red indicators
- Tasks can be flagged as: Big task / Tiny win / Brain dump (ideas, not commitments)

**Acceptance criteria**
- Changing energy state immediately reflows the task list
- No overdue indicators, red badges, or missed-task messaging anywhere in the app
- Brain dump tasks never appear in the active list unless user promotes them

---

### F3 — "Just Start" Focus Timer `[P0]`
- Presets: **2 min (Just Start)**, 10, 15, 25 min
- 2-min mode: after 2 minutes, gentle prompt — "You started 🎉 Keep going?" → one tap extends by 10 min
- Optional background ambient sound (lo-fi / white noise / rain) via free audio APIs
- Runs in background / screen-locked
- Abandoning a session logs partial time as progress — shown as "You did 7 minutes today"

**Acceptance criteria**
- Timer works offline
- No harsh alarm — session end is a gentle chime or vibration
- Partial sessions are always celebrated, never flagged as incomplete

---

### F4 — Streak-Free Habit Tracker `[P0]`
- Habits show total completions counter only ("Meditated 47 times")
- Optional weekly dot view — dots for completed days, blanks for missed ones; no chains, no zeroes, no colour change for missed days
- Habits are grouped by energy level — some habits only show on High days (e.g. "30 min workout"), some only on Low (e.g. "1 glass of water")

**Acceptance criteria**
- No streak counter, broken chain, or missed-day visual anywhere
- Counter only ever goes up
- Users can assign habits to energy levels

---

### F5 — Gemini AI Assistant `[P1]`
Uses **Gemini 1.5 Flash (free tier)** via Google AI API.

**Use cases in MVP:**
- **"What should I do now?"** button → Gemini reads current energy state + incomplete tasks and suggests 1 task with a micro-step breakdown ("Start with just opening the doc")
- **Task exploder:** user types "finish presentation" → Gemini returns 4–5 micro-steps → user adds the ones that feel doable today
- **Gentle time nudge:** if no focus session started by 11am on a High day, soft in-app message: "You said you had energy today — want to pick one thing to start?"
- **End-of-day reflection:** "You did 3 things today. On a Low day, that's real." (tone always warm, never patronising)

**Gemini API implementation notes:**
- Free tier: 15 requests/min, 1 million tokens/day — sufficient for MVP
- System prompt enforces: no guilt language, no streaks, ADHD-aware tone, short responses only
- All Gemini calls are opt-in — users can use Snug fully without the AI features
- No user data sent to Gemini except: current energy state + task titles (no personal identifiers)

---

### F6 — Patterns View `[P1]`
- 30-day calendar view: colour-coded dots by energy level
- Simple stat: "Your most common high-energy day: Tuesday"
- Task completion by energy state: "On Low days you complete 2 tasks on average — that's enough"
- No productivity scores, no comparison to other users, no "you could do better" framing

---

## 6. Out of Scope (MVP)

- Account/cloud sync (local-first, offline-first for v1)
- Push notifications / reminders engine (v2 — requires careful ADHD-aware design)
- Calendar integrations
- Social / accountability partner features (body doubling is v2 — strong evidence base but needs live backend)
- Medication tracking (regulatory sensitivity)
- Paid features / subscription (figure out pricing after finding product-market fit)

---

## 7. UX Laws (Non-Negotiable)

These are not guidelines. Any feature that violates these gets cut.

1. **Zero guilt.** No red, no "overdue," no streaks, no missed-day resets. Ever.
2. **Start before you're ready.** Every flow prioritises getting the user to do *something* over planning to do *everything*.
3. **The app adapts to the user. Never the reverse.** If the app is making demands, we've failed.
4. **Low friction, low stimulation.** Every core action ≤ 2 taps. Calm palette, generous spacing. No pop-ups.
5. **Celebrate the small.** A 2-minute session is a win. One task completed on a Low day is a win. The app says so, every time.
6. **Partial is enough.** No task is ever "failed." It is either done or waiting.

---

## 8. Technical Architecture (MVP)

| Layer | Choice | Reason |
|---|---|---|
| Frontend | React (web prototype) → React Native | Fast to prototype; native for production |
| Storage | Local only (AsyncStorage / SQLite) | Offline-first, no auth needed for MVP |
| AI | Gemini 1.5 Flash (free tier via Google AI Studio API key) | Free, fast, good instruction-following |
| Audio | Free ambient sound libraries (Pixabay / Freesound API) | No licensing cost |
| Hosting (web prototype) | Vercel free tier | Instant deploy |

**Privacy principle:** Nothing leaves the device except optional Gemini API calls (task titles + energy state only, no identifiers). Even that is opt-in.

---

## 9. Success Metrics

| Metric | Target (90 days post-launch) | Why it matters |
|---|---|---|
| Low-day check-in rate | ≥ 40% of users open app on self-reported low days | North Star — proves the app isn't abandoned on bad days |
| "Just Start" extension rate | ≥ 50% extend past 2 minutes | Validates the initiation mechanic |
| D7 retention | ≥ 30% | Baseline viability |
| Task completion on Low days | ≥ 1 tiny win completed | Proves the low-day experience works |
| Gemini "What should I do?" usage | ≥ 20% of DAU | Validates AI feature investment |
| Qualitative: "no guilt" mentions in reviews | Track in first 50 reviews | Brand signal |

---

## 10. Research References

- Barkley, R. A. (1997). Behavioral inhibition, sustained attention, and executive functions. *Psychological Bulletin*, 121(1), 65–94.
- Barkley, R. A. (2012). *Executive Functions.* Guilford Press.
- Barkley, R. A. (2015). *Attention-Deficit Hyperactivity Disorder: A Handbook for Diagnosis and Treatment* (4th ed.). Guilford Press.
- Mette, C. et al. (2023). Time perception in adult ADHD: Findings from a decade — A review. *International Journal of Environmental Research and Public Health*, 20(4), 3098.
- Safren, S. A. et al. (2017). *Mastering Your Adult ADHD: A Cognitive-Behavioral Treatment Program* (2nd ed.). Oxford University Press.
- FLOWN / Neurodiversity in Business (2026). Virtual body doubling for ADHD: New research findings from 117 adults.
- Positive Reset (2026). Task initiation in ADHD: Why starting feels impossible.
- VOX Mental Health (2026). What is behavioural scaffolding for adults with ADHD?
- ScienceDirect (2025). Efficacy of digital mental health interventions for ADHD: A meta-analytic review.

---

## 11. Milestones

| Phase | Timeline | Deliverable |
|---|---|---|
| **0 — PRD + Design** | Week 1 | This document + UI prototype (React) |
| **1 — Core prototype** | Week 2–3 | F1 + F2 + F3 working in browser |
| **2 — AI layer** | Week 4 | Gemini integration (F5) |
| **3 — Beta** | Week 5–7 | Full MVP, 20–30 ADHD users testing |
| **4 — Iterate** | Week 8–10 | Fix friction points from beta feedback |
| **5 — Launch** | Week 11–12 | App Store / Play Store submission |

---

## 12. Open Questions

- Should energy check-in include a 4th state — "wired but scattered" (hyperfocus without direction)?  
- Notifications: can we design a genuinely ADHD-friendly reminder that doesn't become noise? (probably opt-in, time-of-day chosen by user)
- Monetisation: strong signal from ADHD community that one-time purchase (~$4.99) beats subscription. Validate before deciding.
- Name trademark search: confirm "Snug" is clear in target markets before App Store submission.**
