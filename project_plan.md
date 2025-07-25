# Battle Cards: Daily Creature Clash 🦍🆚🐐

## 1. Project Summary ⚔️📱
**Battle Cards (BC)** is a mobile‑first social platform that serves users a fresh, hypothetical combat match‑up every day—e.g., **“10 goats vs 1 donkey”** or **“3 velociraptors vs 12 hockey dads.”**

With a single tap, players vote for the presumed victor, watch real‑time community odds shift, and add the result to their personal **Clash Diary**. An ELO‑style rating system updates each creature’s global power ranking, while streaks, badges, and private **Debate Rings** (mini‑leagues) keep users coming back.

*Why it matters*: Instead of endless doom‑scrolling, BC delivers bite‑sized, meme‑powered debate prompts that spark laughter, discussion, and surprisingly deep strategic arguments—all wrapped in an ethical, cruelty‑free fantasy context.

---

## 2. Goals & Objectives 🎯📊🦁
- **Spark Daily Engagement** – deliver a frictionless, meme‑driven experience that users complete in seconds but talk about all day.  
- **Cultivate Community Debate** – aggregate global voting splits, friend‑league stats, and comment threads to fuel discussion.  
- **Evolve the “Meta”** – use an ELO‑like rating so creatures rise or fall in perceived strength, rewarding returning users with fresh dynamics.  
- **Stay Lightweight & Accessible** – passwordless magic‑link auth, tiny install footprint (PWA), and push/email reminders.

---

## 3. Scope 📜🦍🚀
### 3.1 In‑Scope
- Daily randomized match‑up assignment (two quantity‑creature cards).  
- One‑tap voting, global result display, personal Clash Diary.  
- Real‑time rating updates for each creature/quantity combo.  
- Basic stats: wins/losses, accuracy %, daily streaks.  
- Social: Debate Rings, comment threads, shareable result cards.  
- Gamification: streaks, badges, achievements.  
- PWA + push/email notifications.

### 3.2 Out‑of‑Scope
- Real violence or graphic simulation.  
- Complex in‑app messaging (DMs).  
- 3‑D battle visualizations (initially).  
- Cryptocurrency / NFT monetization (unless later validated).  
- Advanced ML balancing (future phase).

---

## 4. Target Audience 🎯🦓
- **Casual Meme Lovers** – quick, funny polls.  
- **Debate Enthusiasts** – classic “Who would win?” arguments.  
- **Friend Groups / Offices** – daily ice‑breakers.  
- **Influencers** – viral, shareable content prompts.

---

## 5. Project Requirements 🏗️📌

### 5.1 Functional Requirements

| Feature | Description |
|---------|-------------|
| **User Registration** | Email or social OAuth; passwordless magic links. |
| **Daily Match‑Up Assignment** | At 00:00 UTC‑5 a job assigns each user (or their Debate Ring) a unique battle pair with no repeats until the pool cycles. |
| **Vote / Confidence** | One‑tap winner pick (optional 51‑100 % confidence slider). |
| **Result Display** | Show global vote split, haptic feedback, ELO delta. |
| **Clash Diary** | Chronological list of match‑ups with user pick, outcome, accuracy. |
| **Comment Threads** | Emoji reactions + text, moderated. |
| **Debate Rings** | Private leagues with shared match‑ups and leaderboards. |
| **Achievements** | Streaks, perfect‑week badge, “Underdog Whisperer,” etc. |
| **Notifications** | Daily push/email with deep‑link to vote. |
| **Admin Panel** | CRUD for creature cards and moderation tools. |

---

## 6. System Architecture 🏛️⚙️

### 6.1 Overall Flow
1. **Auth** → magic‑link verifies email.  
2. **Daily Job** → selects unseen card pair; Debate Rings share the same pick.  
3. **Vote Action** → stores vote, broadcasts updated tallies.  
4. **ELO Update Worker** → batch rating shifts hourly.  
5. **Push/Email** → templated clash card with deep‑link.

### 6.2 Tech Stack

| Component | Tech | Rationale |
|-----------|------|-----------|
| Frontend | React Native + Expo / React 19 PWA | Shared codebase, smooth animations. |
| Backend | Node.js + Fastify | Lightweight, real‑time ready. |
| Database | PostgreSQL + Prisma ORM | Relational voting data. |
| Cache | Redis | Instant vote tallies. |
| Auth | Clerk / Supabase Auth | Passwordless magic links. |
| Background Jobs | BullMQ | Reliable queues. |
| Email/Push | Resend + Expo Push | Unified messaging. |
| Hosting | Render.com | Turn‑key deploys. |
| Image CDN | Cloudinary | Optimized card art delivery. |

### 6.3 Data Model (Key Tables)

| Table | Key Fields | Purpose |
|-------|------------|---------|
| **Users** | id, email, streak_count, verified_at | Core user info. |
| **Creatures** | id, name, tier, base_strength, lore | Master list (e.g., Goat). |
| **Quantities** | id, amount | Preset numbers (1, 3, 5 …). |
| **Cards** | id, creature_id, quantity_id | Unique combatant (e.g., 10 Goats). |
| **Matchups** | id, card_a_id, card_b_id, created_at | Daily pairings. |
| **UserMatchups** | user_id, matchup_id, chosen_card_id, confidence, voted_at | Individual votes. |
| **EloRatings** | card_id, rating, wins, losses, last_updated | Dynamic strength. |
| **DebateRings** | id, name, owner_id, created_at | Private leagues. |
| **RingMembers** | ring_id, user_id, joined_at, is_admin | Memberships. |
| **Achievements** | id, code, name, description | Badge definitions. |
| **UserAchievements** | user_id, achievement_id, earned_at | Unlocked badges. |
| **Emails** | user_id, type, sent_at, status | Delivery logs. |

---

## 7. Implementation Plan (Phased)

### Phase 1 – MVP
- Magic‑link auth, daily matchup job, vote & result display.  
- Clash Diary, basic stats, email notification, admin CRUD.

### Phase 2 – Engagement & Polish
- Streaks, badges, shareable result cards, confidence slider.

### Phase 3 – Community & Debate Rings
- Private leagues, ring leaderboards, comment threads, public “Top Cards.”

### Phase 4 – Gamification & PWA
- Full PWA, push notifications, seasonal tournaments, AR scale viewer.

### Phase 5 – Scalability & Monetization
- Cosmetic store, brand/IP crossover decks, performance tuning.

---

## 8. Risk Management ⚠️
- **Meme Fatigue** – continual content drops & events.  
- **Toxic Comments** – AI + human moderation, filters.  
- **Animal‑Cruelty Concerns** – clear “fantasy only” messaging.  
- **Vote Rigging/Bots** – rate‑limit, reCAPTCHA, anomaly detection.

---

## 9. Conclusion 🏆
Battle Cards transforms the viral “Who would win?” debate into a structured, daily ritual. One‑tap voting, evolving creature rankings, and social mini‑leagues deliver a low‑friction, high‑conversation spark—no gore, just endless hypothetical showdowns. **Ready to unleash the goats?**
