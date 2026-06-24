<div align="center">

<img src="public/logo.svg" alt="Prepora Logo" width="80" />

# Prepora

### AI Interview Marketplace — Practice. Improve. Get Hired.

[![Next.js](https://img.shields.io/badge/Next.js_15-black?style=flat-square&logo=next.js)](https://nextjs.org/)
[![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)](https://www.typescriptlang.org/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-06B6D4?style=flat-square&logo=tailwindcss&logoColor=white)](https://tailwindcss.com/)
[![Prisma](https://img.shields.io/badge/Prisma-2D3748?style=flat-square&logo=prisma)](https://www.prisma.io/)
[![Supabase](https://img.shields.io/badge/Supabase-3FCF8E?style=flat-square&logo=supabase&logoColor=white)](https://supabase.com/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=flat-square)](LICENSE)

[Live Demo](https://ai-interview-marketplace-prepora.vercel.app) · [Report Bug](https://github.com/SathvikChoutapally/AI-INTERVIEW-MARKETPLACE-PREPORA/issues) · [Request Feature](https://github.com/SathvikChoutapally/AI-INTERVIEW-MARKETPLACE-PREPORA/issues)

</div>

---

## What is Prepora?

**Prepora** is a full-stack AI-powered interview marketplace where candidates can book live video interview sessions with AI interviewers, practice in real-time, and receive instant Gemini-powered feedback — all in one seamless platform.

Built as a production-grade Next.js 15 App Router application with real-time video via Stream, authentication via Clerk, and a PostgreSQL-backed marketplace for scheduling and booking sessions.

---

## Features

- **AI-Powered Interviews** — Google Gemini generates domain-specific questions in real time and evaluates your responses
- **Live Video Rooms** — Full video call infrastructure via Stream Video SDK with recording support
- **Marketplace Booking** — Browse, schedule, and pay for mock interview sessions with a clean booking flow
- **Instant Feedback** — Post-interview AI analysis: strengths, weaknesses, and improvement roadmap
- **Secure Auth** — Clerk authentication with role-based access (candidate / interviewer)
- **Rate Limiting & Bot Protection** — Arcjet middleware for abuse prevention
- **Webhook Reliability** — Clerk + Stream webhook handlers with gzip-safe body parsing
- **Responsive UI** — Shadcn UI components on a Tailwind base, mobile-first

---

## Tech Stack

| Layer | Technology |
|---|---|
| Framework | Next.js 15 (App Router) |
| Language | TypeScript |
| Styling | Tailwind CSS + Shadcn UI |
| Auth | Clerk |
| Database | PostgreSQL via Supabase |
| ORM | Prisma |
| Video | Stream Video SDK |
| AI | Google Gemini API |
| Security | Arcjet |
| Deployment | Vercel |

---

## Project Structure

```
prepora/
├── app/
│   ├── (auth)/             # Clerk sign-in / sign-up routes
│   ├── (root)/
│   │   ├── dashboard/      # Candidate & interviewer dashboards
│   │   ├── interviews/     # Interview listing + booking pages
│   │   └── call/[id]/      # Live video call room
│   └── api/
│       ├── webhooks/       # Clerk + Stream webhook handlers
│       └── interviews/     # REST endpoints for session management
├── components/
│   ├── ui/                 # Shadcn base components
│   ├── InterviewCard.tsx
│   ├── CallRoom.tsx
│   └── FeedbackPanel.tsx
├── lib/
│   ├── prisma.ts           # Prisma client singleton
│   ├── stream.ts           # Stream client setup
│   └── gemini.ts           # Gemini API helpers
├── prisma/
│   └── schema.prisma       # DB schema
└── middleware.ts            # Clerk + Arcjet middleware
```

---

## Getting Started

### Prerequisites

- Node.js 18+
- PostgreSQL database (Supabase recommended)
- Accounts on: Clerk, Stream, Supabase, Google AI Studio

### 1. Clone & Install

```bash
git clone https://github.com/SathvikChoutapally/AI-INTERVIEW-MARKETPLACE-PREPORA.git
cd AI-INTERVIEW-MARKETPLACE-PREPORA
npm install
```

### 2. Environment Variables

Create a `.env.local` file in the root:

```env
# Database
DATABASE_URL=postgresql://...

# Clerk Auth
NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=pk_...
CLERK_SECRET_KEY=sk_...
CLERK_WEBHOOK_SECRET=whsec_...

# Stream Video
NEXT_PUBLIC_STREAM_API_KEY=...
STREAM_SECRET_KEY=...

# Google Gemini
GEMINI_API_KEY=...

# Arcjet
ARCJET_KEY=ajkey_...
```

### 3. Database Setup

```bash
npx prisma generate
npx prisma db push
```

### 4. Run Locally

```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000)

---

## Key Implementation Notes

**Next.js 15 Async Params** — All dynamic route params are awaited as per the Next.js 15 spec:
```ts
const { id } = await params;  // not params.id directly
```

**Webhook Body Parsing** — Raw body is preserved for Clerk signature verification. Gzip decompression handled explicitly before verification.

**Stream Call Lifecycle** — Orphaned calls are cleaned up on DB transaction failure to prevent dangling video sessions.

**Arcjet Middleware** — Rate limiting and bot detection run before Clerk auth in the middleware chain.

---

## Roadmap

- [ ] Stripe payment integration for paid sessions
- [ ] Interview recording playback
- [ ] Multi-round interview scheduling
- [ ] Resume parsing and role-specific question generation
- [ ] Interviewer rating and review system
- [ ] Email notifications via Resend

---

## Contributing

Pull requests are welcome. For major changes, please open an issue first.

```bash
# Fork the repo, then:
git checkout -b feature/your-feature
git commit -m "feat: add your feature"
git push origin feature/your-feature
# Open a PR
```

---

## Author

**Sathvik Choutapally**
B.Tech ECE · VNIT Nagpur

[![GitHub](https://img.shields.io/badge/GitHub-SathvikChoutapally-181717?style=flat-square&logo=github)](https://github.com/SathvikChoutapally)

---

<div align="center">
  <sub>Built with Next.js, Stream, Clerk, Prisma, and Google Gemini · © 2025 Sathvik Choutapally</sub>
</div>
