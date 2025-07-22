# Helix Mail

> The open-source email client for power users.

Helix Mail is an ambitious, open-source project to build the best email client in the world. Our goal is to create a beautiful, modern, and minimalistic application that is blazingly fast, works seamlessly offline, and is packed with powerful features to help you conquer your inbox.

We are starting with full support for Gmail and will expand from there. This project is for those who believe email can be better.

## The Vision

Modern email clients often fall short. They can be slow, clunky, and lack the features needed for true productivity. Helix Mail is being built to solve this. Our core principles are:

- **Speed as a Feature:** Every interaction should be instantaneous. No waiting for network requests.
- **Offline First:** The application must be 100% usable offline. All actions (reading, searching, archiving) are performed locally and synced intelligently.
- **Minimalistic Design:** A clean, beautiful, and intuitive interface that puts your email front and center.
- **Powerful Features:** From AI-powered summaries to advanced productivity tools, we will build features that save you time.
- **Open Source:** We believe in the power of community and transparent development.

## Architecture

To achieve our goals, we are building on a robust, scalable, full-stack architecture designed for performance and reliability.

![Architecture Diagram](https://i.imgur.com/gY1BqYp.png)

1.  **Frontend (Next.js):** A powerful "thick client" that runs in the browser. It contains a local copy of your mailbox in an embedded database (IndexedDB) for instant access and a full-text search index for offline search. All user actions happen here first, providing an optimistic UI that feels incredibly responsive.

2.  **Backend API (NestJS):** A dedicated backend service that acts as a powerful synchronization and orchestration engine. It handles secure communication with Google's APIs, manages user authentication, and processes background jobs.

3.  **Database (PostgreSQL):** Our central source of truth for user accounts, encrypted credentials, and a durable backup of all synced email data.

4.  **Sync Engine (Google Pub/Sub & WebSockets):** The heart of our real-time system. The backend uses the **Gmail Push Notifications API** to receive instant alerts about changes in the user's mailbox. These changes are processed and then pushed directly to the connected clients via WebSockets, ensuring the UI is always up-to-date.

## Feature Roadmap

We are building Helix Mail methodically, ensuring each feature is production-ready before moving to the next.

### Phase 0: Project Setup & Foundation

- [] **Feature 1: Monorepo & Backend Scaffolding**

### Phase 1: Authentication & Core Data Sync

- [ ] **Feature 2: Google OAuth & User Authentication**
- [ ] **Feature 3: Logout**
- [ ] **Feature 4: Initial Mailbox Sync (Backend)**

### Phase 2: The Core Reading Experience

- [ ] **Feature 5: Standard Email Threading (Conversation View)**
  - Group individual emails into conversations in the inbox list. The UI will be designed to display and manage these threads, just like in any modern email client.
- [ ] **Feature 6: Real-Time Sync**
  - Implement the full real-time pipeline (Pub/Sub -> Backend -> WebSocket -> Frontend) to push updates for threads.
- [ ] **Feature 7: Full Thread View**
  - Create the view to read an entire conversation, with proper grouping of messages.
- [ ] **Feature 8: Client-Side Caching of Threads**
  - Cache entire conversations in IndexedDB for instant loads and offline access.

### Phase 3: Core Email Actions

- [ ] **Feature 9: The Modifier Queue & Thread Actions**
  - Build the client-side "modifier queue" for optimistic UI updates and reliable background syncing of actions. Implement thread-level actions like **Archive** and **Delete**.
- [ ] **Feature 10: Mark as Read/Unread**
- [ ] **Feature 11: Compose, Reply & Forward**
  - Build a rich composer for sending new emails, replying to messages within a thread, and forwarding conversations.

### Phase 4: The Productivity Layer

- [ ] **Feature 12: Split Inbox**
  - Automatically triage emails into distinct, manageable feeds (e.g., "Newsletters", "Team", "VIPs").
- [ ] **Feature 13: Snooze**
  - Temporarily remove threads from the inbox to have them reappear later.
- [ ] **Feature 14: Reminders / Follow-Up**
  - Get reminded to follow up on sent emails if you don't receive a reply.
- [ ] **Feature 15: Send Later**
  - Schedule emails to be sent at a future date and time.
- [ ] **Feature 16: Command Palette**
  - Implement a `Cmd+K` palette for keyboard-first navigation and access to all features.

### Phase 5: The Collaboration Layer

- [ ] **Feature 17: Team Features**
  - Implement team-aware read statuses and live reply indicators to avoid collisions.
- [ ] **Feature 18: Shared Conversation Links**
  - Create shareable links to email threads for discussion in other tools.

### Phase 6: The Intelligence Layer (AI)

- [ ] **Feature 19: AI Auto-Summarize**
  - Display AI-generated summaries at the top of long conversations.
- [ ] **Feature 20: AI-Assisted Writing**
  - Help users draft emails, change tone, and fix grammar.
- [ ] **Feature 21: Natural Language Search ("Ask AI")**
  - Allow users to ask natural questions to find information across their entire mailbox.

## Tech Stack

- **Frontend:** Next.js, React, TypeScript, React Query, Tailwind CSS, shadcn/ui, `dexie.js` (for IndexedDB)
- **Backend:** NestJS, TypeScript, PostgreSQL, Prisma, Redis (for background jobs)
- **Authentication:** Passport.js (Google OAuth 2.0 Strategy)
- **Infrastructure:** Docker, Google Cloud Platform (for Gmail API & Pub/Sub), Vercel (for frontend hosting)
