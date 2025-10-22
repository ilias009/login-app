# Deployment Guide

## Deploy to Vercel

### Step 1: Push to GitHub
1. Initialize git repository: `git init`
2. Add all files: `git add .`
3. Commit: `git commit -m "Initial commit"`
4. Create repository on GitHub
5. Push to GitHub: `git push origin main`

### Step 2: Deploy on Vercel
1. Go to [Vercel](https://vercel.com)
2. Click "New Project"
3. Import your GitHub repository
4. Add environment variables:
   - `NEXT_PUBLIC_SUPABASE_URL`: `https://cyzstkgqgvcyfvtihsqu.supabase.co`
   - `NEXT_PUBLIC_SUPABASE_ANON_KEY`: `eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6ImN5enN0a2dxZ3ZjeWZ2dGloc3F1Iiwicm9sZSI6ImFub24iLCJpYXQiOjE3NjA5NzM1NDUsImV4cCI6MjA3NjU0OTU0NX0.sdNAKB4MC29weaZ7Im3RUNxtYw1NDb6xdj8NL9gRD3g`
5. Click "Deploy"

### Step 3: Test the Application
1. Visit your Vercel URL
2. Enter an email address
3. Check that the user appears in your Supabase dashboard
4. Verify the UUID, timestamp, and email are displayed correctly

## Supabase Setup
1. In your project, enable Email auth in Authentication > Providers
2. Create table `emails` and policies (SQL below) in SQL editor

### SQL to create table and RLS policies
```sql
-- 1) Table
create table if not exists public.emails (
  id uuid primary key default gen_random_uuid(),
  email text not null,
  created_at timestamptz not null default now()
);

-- 2) Enable RLS
alter table public.emails enable row level security;

-- 3) Policies (Postgres doesn't support IF NOT EXISTS for policies)
do $$
begin
  begin
    create policy "Allow anon insert" on public.emails
      for insert to anon
      with check (true);
  exception when duplicate_object then null;
  end;

  begin
    create policy "Allow anon select" on public.emails
      for select to anon
      using (true);
  exception when duplicate_object then null;
  end;
end $$;
```
