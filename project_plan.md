# BattleCards 🦁⚔️🐅

## 1. Project Summary 🎮🏟️

**BattleCards** is a mobile-first social voting game that captures the viral appeal of absurd hypothetical matchups like "100 men vs 1 gorilla." Users vote on randomly generated battles between different quantities of animals, creatures, and characters—such as **"10 goats vs 1 donkey"** or **"3 velociraptors vs 12 hockey dads."**

The platform generates endless entertainment through **algorithmically balanced matchups** that feel both ridiculous and genuinely debatable. Users can play anonymously or create accounts to track their voting history and see their name attached to controversial picks.

After each vote, users immediately see **real-time community results**, creating that satisfying "I knew it!" or "Wait, really?!" moment that drives social sharing and repeat engagement.

### **Why This Matters**

BattleCards taps into humanity's love for hypothetical debates and "who would win" discussions that naturally happen in friend groups, social media, and internet forums. By systematizing these debates with visual cards, real-time voting, and community results, we create an **instantly shareable, endlessly entertaining** experience that thrives on both the absurdity and genuine strategic thinking these matchups inspire.

---

## 2. Goals & Objectives 🎯🏆⚡

1. **Capture Viral "Who Would Win" Energy**
   - Generate **endless combinations** of absurd but compelling matchups.
   - Use **high-quality animal artwork** and clean card design to make sharing irresistible.
   - Create debates that feel both **silly and genuinely thought-provoking**.

2. **Drive Social Engagement & Sharing**
   - Design **highly shareable results screens** showing community vote splits.
   - Enable users to **challenge friends** with specific matchups.
   - Create **"controversial takes"** leaderboards for users with unpopular opinions.

3. **Build Addictive Gameplay Loop**
   - **Instant gratification**: Vote → See results → Get next matchup.
   - **"Just one more"** psychology through endless unique combinations.
   - **Social validation** through seeing your username next to votes.

4. **Maintain Simplicity & Accessibility**
   - **Zero learning curve**: Anyone can immediately understand and play.
   - **Fast loading**: Optimized for mobile with minimal data usage.
   - **Anonymous play** option for maximum accessibility.

---

## 3. Scope 📜⚔️🚀

### 3.1 In-Scope

- **Random matchup generation** from curated database of animals/creatures/quantities.
- **Real-time voting** with immediate community results display.
- **User accounts** with vote history and username attribution (optional).
- **Anonymous play** for users who don't want to sign up.
- **Shareable results screens** optimized for social media.
- **Live matchup history** showing all recent battles and outcomes.
- **Basic moderation tools** for inappropriate content/usernames.
- **Mobile-first responsive design** with card-based UI.
- **Simple analytics** tracking popular matchups and voting patterns.

### 3.2 Out-of-Scope

- Complex user profiles or social following systems.
- User-generated content (custom animals/matchups).
- Real-time chat or commenting on matchups.
- Advanced matchmaking algorithms or ELO ratings.
- Monetization features (ads, premium accounts) in initial version.
- Video/GIF content integration.
- Tournament brackets or structured competitions.
- Detailed battle simulations or explanations.

---

## 4. Target Audience 🎯🎮📱

1. **Social Media Users (16-35)** who share memes, polls, and debate hypotheticals in group chats.
2. **Casual Mobile Gamers** looking for quick, entertaining experiences during downtime.
3. **Friend Groups & Communities** who enjoy debating silly "what if" scenarios together.
4. **Content Creators** seeking shareable, engaging content for their audiences.

---

## 5. Project Requirements 🏗️⚡

### 5.1 Functional Requirements

1. **User Authentication**
   - **Anonymous play** as the default experience.
   - **Optional account creation** with email/username only.
   - **Magic link authentication** (no passwords required).
   - Users can **upgrade from anonymous to registered** mid-session.

2. **Matchup Generation**
   - **Algorithmic pairing system** that creates balanced but absurd matchups.
   - **Quantity randomization** (1-50 range with weighted probabilities).
   - **Animal/creature database** with categories (mammals, reptiles, mythical, humans, etc.).
   - **Avoid recent duplicates** for each user session.
   - **Difficulty balancing** to ensure most matchups feel genuinely debatable.

3. **Voting Mechanism**
   - **Single-tap voting** on either card option.
   - **Vote confirmation** with brief animation/feedback.
   - **Immediate redirect** to results page after voting.
   - **No vote changing** once submitted to maintain data integrity.

4. **Results Display**
   - **Real-time vote percentages** with visual progress bars.
   - **Total vote count** for the specific matchup.
   - **User attribution** showing "You voted for [option]" and username if logged in.
   - **"Majority/Minority"** indicator showing if user picked popular choice.
   - **Social sharing buttons** with pre-generated text and images.

5. **Card Design & Assets**
   - **High-quality animal illustrations** (sourced or commissioned artwork).
   - **Consistent card template** with animal image, quantity, and creature name.
   - **Visual hierarchy** making quantities and creatures immediately recognizable.
   - **Responsive design** working perfectly on all mobile screen sizes.

6. **Live History Feed**
   - **Chronological list** of recent matchups with community results.
   - **Filter options** by creature type, quantity range, or vote closeness.
   - **"Vote on this too"** buttons for matchups user hasn't seen.
   - **Pagination** for performance with large datasets.

7. **Session Tracking**
   - **Anonymous sessions** tracked via browser storage.
   - **Vote history** visible within current session.
   - **Session stats** showing total votes, controversial picks, etc.
   - **"Continue where you left off"** functionality.

8. **Performance & Reliability**
   - **Sub-second load times** for new matchups.
   - **Offline capability** for viewing recent matchups.
   - **Error handling** for network issues during voting.
   - **Rate limiting** to prevent spam voting.

---

## 6. System Architecture

### 6.1 Overall Flow

1. **Landing & Onboarding**
   - Users land on **marketing page** explaining the concept.
   - **"Start Playing"** button launches directly into first matchup.
   - **Optional signup** promoted after 3-5 votes for vote attribution.

2. **Matchup Generation**
   - **Background service** pre-generates popular matchup combinations.  
   - **Real-time generation** for edge cases and new user sessions.
   - **Balancing algorithm** ensures most matchups have 30-70% vote splits.
   - **Duplicate prevention** within user sessions using client-side tracking.

3. **Voting Process**
   - User taps card → **Optimistic UI update** → **API call** → Results redirect.
   - **Vote validation** server-side with duplicate prevention.
   - **Real-time vote aggregation** using database triggers or cache updates.

4. **Results & Social Sharing**
   - **Dynamic image generation** for social sharing with vote results.
   - **Permalink system** for specific matchups to enable sharing.
   - **"Next Battle"** button generates new matchup immediately.

5. **Data Persistence**
   - **Vote storage** with user attribution (anonymous ID or username).
   - **Matchup caching** for popular combinations.
   - **Session tracking** for anonymous users.
   - **Analytics collection** for matchup popularity and voting patterns.

---

### 6.2 Tech Stack

| **Component**          | **Technology**                    | **Why?**                                              |
| ---------------------- | --------------------------------- | ----------------------------------------------------- |
| **Frontend**           | **React 19 + TanStack Router**   | Fast, mobile-optimized with excellent UX patterns.   |
| **Backend**            | **Node.js + Express/Fastify**    | Simple API layer with real-time capabilities.        |
| **Database**           | **PostgreSQL + Redis Cache**     | Reliable vote storage + fast matchup generation.     |
| **Authentication**     | **Supabase Auth (Magic Links)**  | Passwordless, optional signup flow.                  |
---

### 6.3 Data Model

| **Table**           | **Fields**                                                                                                    | **Purpose & Notes**                                                                                                      |
| ------------------- | ------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------ |
| **Users**           | `id (PK), username, email, created_at, total_votes, controversial_votes, last_active, is_anonymous`           | Tracks registered users and anonymous sessions. `controversial_votes` counts minority picks.                            |
| **Creatures**       | `id (PK), name, category, image_url, power_rating, size_category, created_at`                                 | Master list of all animals/creatures. `power_rating` helps balance matchups.                                            |
| **Matchups**        | `id (PK), creature_a_id (FK), creature_a_quantity, creature_b_id (FK), creature_b_quantity, created_at`       | Stores unique matchup combinations. Used for caching and permalinks.                                                    |
| **Votes**           | `id (PK), matchup_id (FK), user_id (FK), chosen_side, voted_at, session_id`                                   | Individual vote records. `chosen_side` is 'A' or 'B'. `session_id` tracks anonymous users.                              |
| **MatchupStats**    | `matchup_id (PK/FK), total_votes, side_a_votes, side_b_votes, last_vote_at`                                   | Precomputed vote totals for fast results display. Updated via triggers.                                                 |
| **Sessions**        | `id (PK), session_token, created_at, last_active, total_votes, user_id (FK, nullable)`                        | Tracks anonymous sessions and their voting history.                                                                     |
| **PopularMatchups** | `id (PK), matchup_id (FK), vote_count, controversy_score, trending_score, updated_at`                         | Tracks viral/popular matchups for homepage features. `controversy_score` measures closeness of vote split.              |

#### 6.3.1 Key Relationships

- **Users** can have many **Votes** (one-to-many)
- **Creatures** appear in many **Matchups** (many-to-many through creature_a_id/creature_b_id)
- **Matchups** have many **Votes** (one-to-many)
- **Sessions** can be promoted to **Users** when anonymous users sign up

#### 6.3.2 Indexes & Performance

| **Table**      | **Index**                           | **Purpose**                               |
| -------------- | ----------------------------------- | ----------------------------------------- |
| `Votes`        | `idx_votes_matchup_user`            | Prevent duplicate votes per matchup       |
| `Votes`        | `idx_votes_session_matchup`         | Track anonymous user voting history       |
| `MatchupStats` | `idx_matchupstats_popularity`       | Fast retrieval of popular matchups        |
| `Matchups`     | `idx_matchups_creatures`            | Quick lookups for existing combinations   |

---

## 7. Implementation Plan (Phased Approach)

### 7.1 Phase 1: Core MVP (4-6 weeks)

**Week 1-2: Foundation**
1. **Project Setup & Database**
   - Set up React frontend with TanStack Router
   - PostgreSQL database with core tables (Users, Creatures, Matchups, Votes)
   - Basic API endpoints for voting and results
   - Seed database with 50+ creatures and power ratings

2. **Core Game Loop**
   - Matchup generation algorithm with basic balancing
   - Single-page voting interface with card design
   - Vote submission and validation
   - Results page with percentage display

**Week 3-4: Polish & Features**
3. **User Experience**
   - Anonymous session tracking
   - Optional user registration with magic links
   - Vote history for sessions/users
   - Mobile-responsive card design with animations

4. **Performance & Reliability**
   - Vote deduplication and validation
   - Error handling and loading states
   - Basic rate limiting
   - Matchup caching for popular combinations

**Week 5-6: Launch Preparation**
5. **Social Features & Polish**
   - Live history feed showing recent matchups
   - Social sharing buttons and dynamic images
   - Basic analytics tracking
   - Admin tools for creature management

**Key Deliverables:**
- Fully functional voting game with 50+ creatures
- Anonymous and registered user flows
- Real-time results display
- Mobile-optimized interface
- Basic social sharing


---

## 8. Risk Management ⚠️🛡️

### 8.1 Technical Risks

| **Risk**                    | **Impact** | **Probability** | **Mitigation Strategy**                                           |
| --------------------------- | ---------- | --------------- | ----------------------------------------------------------------- |
| **Database performance**    | High       | Medium          | Implement caching, database indexing, and query optimization     |
| **Vote manipulation**       | Medium     | High            | Rate limiting, session tracking, and duplicate vote prevention   |
| **Image loading speed**     | Medium     | Medium          | CDN implementation, image optimization, and lazy loading         |
| **Scalability bottlenecks** | High       | Low             | Horizontal scaling, load balancing, and performance monitoring   |

---

## 10. Conclusion 🏆⚔️

**BattleCards** transforms the universal appeal of "who would win" debates into an addictive, shareable social game. By combining **algorithmic matchup generation**, **instant social validation**, and **viral sharing mechanics**, we create a platform that naturally spreads through social networks while providing endless entertainment.

The key to success lies in **execution quality**—ensuring matchups feel genuinely debatable, results are instantly satisfying to share, and the core gameplay loop remains frictionless across all devices. With proper attention to **viral mechanics** and **community building**, BattleCards has the potential to become the next breakout social gaming sensation.