# Project Brief: Supabase Keep-Alive Ping

## Project Overview
A simple webpage-based solution that pings a Supabase database when visited to prevent free-tier databases from pausing due to inactivity.

## Core Requirements
- HTML page with basic structure
- JavaScript function that triggers a Supabase API request on page load
- Fetch request to Supabase RPC (`now()`) endpoint
- Hosted on a static site provider (Netlify, Vercel, or GitHub Pages)
- No authentication required (uses public API key)
- Logs success/failure in the console

## Implementation Details
- Created a responsive HTML page with clean UI
- Implemented JavaScript function to ping Supabase's RPC endpoint
- Set up automatic pinging every 10 minutes while the page is open
- Added visual status indicator and console logging
- Created comprehensive README with setup and hosting instructions

## Configuration Requirements
Users need to configure two values in the index.html file:
1. `SUPABASE_URL`: The URL of their Supabase project
2. `SUPABASE_PUBLIC_KEY`: Their Supabase public API key

## Hosting Options
The solution can be hosted on any static site provider, including:
- GitHub Pages
- Netlify
- Vercel

## Future Enhancements
Potential improvements could include:
- Adding a configuration UI to set the URL and API key without editing code
- Implementing a service worker for background pinging
- Creating a browser extension version