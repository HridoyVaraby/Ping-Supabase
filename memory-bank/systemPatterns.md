# System Patterns: Supabase Keep-Alive Ping

## System Architecture
This project follows a simple client-side architecture with no server-side components:

```
+----------------+      +-------------------+
|                |      |                   |
|  Browser       |----->|  Supabase API     |
|  (HTML/JS)     |<-----|  (RPC Endpoint)   |
|                |      |                   |
+----------------+      +-------------------+
```

## Key Technical Decisions

1. **Client-Side Only Approach**
   - Decision: Implement the entire solution in client-side code
   - Rationale: Simplifies deployment, reduces complexity, and eliminates the need for server maintenance

2. **Vanilla JavaScript**
   - Decision: Use plain JavaScript without frameworks or libraries
   - Rationale: Minimizes dependencies, reduces load time, and simplifies maintenance

3. **RPC Endpoint Selection**
   - Decision: Use the `now()` RPC function for pinging
   - Rationale: Minimal overhead, simple to implement, and sufficient to keep the database active

4. **Automatic Retry Mechanism**
   - Decision: Implement different retry intervals for success (10 min) vs. failure (1 min)
   - Rationale: Balances keeping the database active with not overwhelming it during issues

## Design Patterns in Use

### Observer Pattern
- The page observes and displays the status of Supabase connection attempts
- Status updates are reflected both in the UI and console logs

### Interval-Based Polling
- Regular polling of the Supabase endpoint at fixed intervals
- Different intervals based on success/failure states

### Error Handling Pattern
- Try/catch blocks for robust error management
- Visual feedback for different states (loading, success, error)

## Component Relationships

### Main Components
1. **UI Layer**
   - HTML structure and CSS styling
   - Status display component

2. **Logic Layer**
   - Ping function implementation
   - Error handling logic
   - Scheduling mechanism

3. **Integration Layer**
   - Supabase API connection
   - Fetch request configuration

### Data Flow
```
+-------------+     +---------------+     +----------------+
|             |     |               |     |                |
| Page Load   |---->| Ping Function |---->| Supabase API   |
|             |     |               |     |                |
+-------------+     +---------------+     +----------------+
                           |                     |
                           v                     v
                    +----------------+    +----------------+
                    |                |    |                |
                    | Update UI     |<---| Process        |
                    | Status        |    | Response       |
                    |                |    |                |
                    +----------------+    +----------------+
                           |
                           v
                    +----------------+
                    |                |
                    | Schedule Next  |
                    | Ping           |
                    |                |
                    +----------------+
```

## Critical Implementation Paths

### Initial Page Load
1. DOM content loaded event triggers
2. pingSupabase() function executes
3. Fetch request sent to Supabase
4. Response processed
5. UI updated
6. Next ping scheduled

### Error Handling Path
1. Error occurs during fetch
2. Catch block executes
3. Error logged to console
4. UI updated with error status
5. Shorter retry interval scheduled

### Automatic Ping Path
1. setTimeout callback triggers
2. pingSupabase() function executes again
3. Process repeats