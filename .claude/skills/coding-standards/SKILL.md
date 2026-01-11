# Coding Standards

Technical patterns for backend code, APIs, and security.

---

## Tech Stack

- **Frontend**: Vanilla HTML/CSS/JS + Tailwind CDN
- **Backend**: Cloudflare Pages Functions (`/functions` directory)
- **Database**: Cloudflare D1 (when needed)

---

## Project Structure

```
/
├── index.html              # Main page (includes Tailwind setup from design-system)
├── functions/              # Cloudflare Pages Functions
│   └── api/                # API endpoints
├── wrangler.toml           # Cloudflare config
└── README.md
```

---

## API Route Pattern

```javascript
// functions/api/example.js
export async function onRequestGet(context) {
  const { env } = context;

  try {
    const data = { message: 'Hello' };

    return Response.json(data, {
      headers: { 'Cache-Control': 'public, max-age=3600' }
    });
  } catch (error) {
    console.error('Request failed:', error);
    return Response.json(
      { error: 'Request failed' },
      { status: 500 }
    );
  }
}

export async function onRequestPost(context) {
  const { env, request } = context;

  try {
    const body = await request.json();
    // validate, process, return
    return Response.json({ success: true });
  } catch (error) {
    console.error('Request failed:', error);
    return Response.json(
      { error: 'Request failed' },
      { status: 500 }
    );
  }
}
```

---

## Error Response Format

All API errors use this format:

```json
{
  "error": "Human-readable message",
  "code": "OPTIONAL_ERROR_CODE"
}
```

| HTTP Status | When to Use |
|-------------|-------------|
| 400 | Bad request (validation failed) |
| 401 | Not authenticated |
| 403 | Not authorized |
| 404 | Resource not found |
| 500 | Server error |

**Frontend displays** the `error` field to users. Keep messages helpful:
- Bad: `"Invalid input"`
- Good: `"Email address is required"`

---

## Security

### API Keys

Store in Cloudflare environment variables. Never in client code.

```javascript
// In Cloudflare Function
const API_KEY = env.API_KEY;
```

Set secrets:
```bash
npx wrangler pages secret put API_KEY --project-name PROJECT_NAME
```

### Input Validation

Always validate on the server, even if validated on client:

```javascript
export async function onRequestPost(context) {
  const body = await context.request.json();

  if (!body.email || !body.email.includes('@')) {
    return Response.json(
      { error: 'Valid email is required' },
      { status: 400 }
    );
  }

  // proceed with valid data
}
```

---

## D1 Database Pattern

```javascript
// functions/api/items.js
export async function onRequestGet(context) {
  const { env } = context;

  try {
    const { results } = await env.DB.prepare(
      'SELECT * FROM items ORDER BY created_at DESC'
    ).all();

    return Response.json(results);
  } catch (error) {
    console.error('Database error:', error);
    return Response.json(
      { error: 'Failed to fetch items' },
      { status: 500 }
    );
  }
}
```

---

## Frontend Fetch Pattern

```javascript
async function fetchData(endpoint) {
  try {
    const response = await fetch(`/api/${endpoint}`);
    const data = await response.json();

    if (!response.ok) {
      throw new Error(data.error || 'Request failed');
    }

    return data;
  } catch (error) {
    // Show error to user using alert component from design-system
    showError(error.message);
    throw error;
  }
}
```

---

## Rules

1. **All API keys in env vars** — never in code
2. **Validate server-side** — client validation is UX, not security
3. **Log errors** — `console.error` before returning error response
4. **Use standard error format** — `{ error: string }`
