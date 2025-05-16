# Supabase Keep-Alive Ping

A simple webpage-based solution that pings a Supabase database when visited to prevent free-tier databases from pausing due to inactivity.

## Features

- Minimal HTML page with clean UI
- JavaScript function that triggers a Supabase API request on page load
- Automatic pinging every 10 minutes while the page is open
- Visual status indicator and console logging
- No authentication required (uses public API key)

## Setup Instructions

1. Clone or download this repository
2. Open `index.html` in a text editor
3. Replace the placeholder values with your actual Supabase details:
   ```javascript
   const SUPABASE_URL = 'https://your-project-id.supabase.co';
   const SUPABASE_PUBLIC_KEY = 'your-supabase-public-key';
   ```
4. Save the file

## How It Works

When the webpage loads, it sends a request to the Supabase RPC endpoint using the `now()` function. This minimal request is enough to keep your database active. The page displays the status of the ping and logs the result in the browser console.

The script will automatically ping your database:
- On initial page load
- Every 10 minutes while the page remains open
- If a ping fails, it will retry after 1 minute

## Hosting Options

You can host this simple HTML page on any static site provider:

### GitHub Pages
1. Push this repository to GitHub
2. Go to repository Settings > Pages
3. Select your branch and save

### Netlify
1. Sign up for a Netlify account
2. Create a new site from Git or drag and drop the folder
3. Deploy

### Vercel
1. Sign up for a Vercel account
2. Create a new project and import your repository
3. Deploy

## Usage Tips

- Bookmark the deployed page and visit it occasionally
- Consider setting it as your browser's homepage
- For more reliable pinging, consider setting up a scheduled task or cron job to visit the URL

## Security Note

This project uses your Supabase public API key, which is safe to expose in client-side code. The key only has permissions that you've explicitly enabled for unauthenticated users in your Supabase dashboard.