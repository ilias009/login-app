# Login App with Supabase

This is a Next.js application with a login form that registers emails in Supabase.

## Setup Instructions

### 1. Supabase Setup

1. Go to [Supabase](https://supabase.com) and create a new project
2. In your Supabase dashboard, go to Settings > API
3. Copy your Project URL and anon public key
4. Create a `.env.local` file in the root directory with:

```
NEXT_PUBLIC_SUPABASE_URL=https://cyzstkgqgvcyfvtihsqu.supabase.co
NEXT_PUBLIC_SUPABASE_ANON_KEY=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6ImN5enN0a2dxZ3ZjeWZ2dGloc3F1Iiwicm9sZSI6ImFub24iLCJpYXQiOjE3NjA5NzM1NDUsImV4cCI6MjA3NjU0OTU0NX0.sdNAKB4MC29weaZ7Im3RUNxtYw1NDb6xdj8NL9gRD3g
```

### 2. Database Setup

The app will automatically create users in Supabase's auth.users table when they submit their email.

### 3. Run the Application

```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) to view the application.

### 4. Deploy to Vercel

1. Push your code to GitHub
2. Connect your GitHub repository to Vercel
3. Add your environment variables in Vercel dashboard
4. Deploy!

## Features

- Email-only login form
- Automatic user registration in Supabase
- Display of UUID, timestamp, and email after registration
- Built with Next.js, React, Tailwind CSS, and shadcn/ui