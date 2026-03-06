# Markly 

A minimal, real-time bookmark manager built with Next.js, Supabase, and Tailwind CSS.

**Live URL:** https://bookmark-1bco7oald-vamsys-projects-ca56c14f.vercel.app

---

## Features (v1)

- Google OAuth login (no email/password)
- Add and delete bookmarks (URL + title)
- Bookmarks are private per user — no user can see another user's bookmarks
- Real-time updates across browsers and devices without page refresh
- Favicon detection for saved URLs
- Relative timestamps ("Just now", "2h ago", etc.)

---

## Tech Stack

- **Framework:** Next.js 15 (App Router)
- **Auth + Database + Realtime:** Supabase
- **Styling:** Tailwind CSS
- **Deployment:** Vercel

---

## Setup

### 1. Clone and install dependencies

```bash
npm install
```

### 2. Create a Supabase project

Go to [supabase.com](https://supabase.com) and create a new project.

### 3. Run the database setup SQL

In your Supabase SQL Editor, run the contents of `supabase-setup.sql`. This creates the `bookmarks` table, enables RLS policies, adds the table to the Realtime publication, and sets `REPLICA IDENTITY FULL` for DELETE events.

### 4. Configure Google OAuth

1. Go to [Google Cloud Console](https://console.cloud.google.com) → APIs & Services → Credentials
2. Create an OAuth 2.0 Client ID
3. Add authorized redirect URI: `https://<your-project>.supabase.co/auth/v1/callback`
4. Copy the Client ID and Secret into Supabase → Authentication → Providers → Google

### 5. Set environment variables

Create a `.env.local` file:

```env
NEXT_PUBLIC_SUPABASE_URL=your_supabase_url
NEXT_PUBLIC_SUPABASE_ANON_KEY=your_supabase_anon_key
```

### 6. Run locally

```bash
npm run dev
```

---

