# Cloudflare Deploy

How to set up and deploy to Cloudflare Pages.

---

## New Project Setup

### 1. Create the project

```bash
npx wrangler pages project create PROJECT_NAME
```

### 2. Create wrangler.toml

```toml
name = "PROJECT_NAME"
compatibility_date = "2024-01-01"

[vars]
# Non-secret environment variables

# Uncomment if using D1
# [[d1_databases]]
# binding = "DB"
# database_name = "PROJECT_NAME-db"
# database_id = "your-database-id"
```

### 3. (Optional) Set up D1 Database

```bash
# Create database
npx wrangler d1 create PROJECT_NAME-db

# Add the database_id to wrangler.toml

# Create tables
npx wrangler d1 execute PROJECT_NAME-db --file=./schema.sql
```

### 4. Set secrets

```bash
npx wrangler pages secret put API_KEY --project-name PROJECT_NAME
```

---

## Deploy

```bash
npx wrangler pages deploy ./ --project-name PROJECT_NAME
```

- Returns a preview URL for each deployment
- Production URL: `PROJECT_NAME.pages.dev`

---

## Local Development

```bash
npx wrangler pages dev ./
```

For D1 locally:
```bash
npx wrangler pages dev ./ --d1=DB
```

---

## Post-Deploy Checklist

- [ ] Preview URL works
- [ ] No console errors
- [ ] API endpoints respond
- [ ] Environment variables are set

---

## Custom Domain (Later)

1. Go to Cloudflare Dashboard → Pages → PROJECT_NAME
2. Custom domains → Add
3. Follow DNS setup instructions
