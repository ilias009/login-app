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
   - `NEXT_PUBLIC_SUPABASE_URL`: Your Supabase project URL
   - `NEXT_PUBLIC_SUPABASE_ANON_KEY`: Your Supabase anon key
5. Click "Deploy"

### Step 3: Test the Application
1. Visit your Vercel URL
2. Enter an email address
3. Check that the user appears in your Supabase dashboard
4. Verify the UUID, timestamp, and email are displayed correctly

## Supabase Setup
1. Create a new project at [supabase.com](https://supabase.com)
2. Go to Authentication > Settings
3. Enable email authentication
4. Copy your project URL and anon key to Vercel environment variables
