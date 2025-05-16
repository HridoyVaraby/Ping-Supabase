# Tech Context: Supabase Keep-Alive Ping

## Technologies Used

### Frontend
- **HTML5**: Basic structure of the webpage
- **CSS3**: Styling for responsive design and visual feedback
- **JavaScript (ES6+)**: Core functionality for pinging Supabase
- **Fetch API**: Making HTTP requests to Supabase endpoints

### Backend Integration
- **Supabase**: Database service being pinged
- **Supabase REST API**: Specifically using the RPC endpoint with the `now()` function

### Hosting Options
- **GitHub Pages**: Free static site hosting through GitHub
- **Netlify**: Static site hosting with additional features
- **Vercel**: Modern hosting platform for static sites

## Development Setup
This is a simple static website with no build process required. Development can be done with:
- Any text editor (VS Code, Sublime Text, etc.)
- A modern web browser for testing

## Technical Constraints
- Must use only client-side code (no server-side processing)
- Must be compatible with static site hosting
- Must use only the public API key for Supabase (no authentication)

## Dependencies
- No external libraries or frameworks required
- Uses only native browser APIs

## Tool Usage Patterns

### Supabase Integration
```javascript
// Pattern for pinging Supabase
fetch(`${SUPABASE_URL}/rest/v1/rpc/now`, {
    method: 'POST',
    headers: {
        'Content-Type': 'application/json',
        'apikey': SUPABASE_PUBLIC_KEY,
        'Authorization': `Bearer ${SUPABASE_PUBLIC_KEY}`
    },
    body: JSON.stringify({})
});
```

### Error Handling Pattern
```javascript
try {
    // API call
    // Success handling
} catch (error) {
    // Error handling
    // Retry mechanism
}
```

### Automatic Retry Pattern
```javascript
// On success
setTimeout(pingFunction, 10 * 60 * 1000); // 10 minutes

// On failure
setTimeout(pingFunction, 60 * 1000); // 1 minute
```