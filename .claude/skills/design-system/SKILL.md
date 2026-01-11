# Design System

Tailwind CSS with custom brand colors. Minimal, clean, intentional.

---

## Setup

Add this to your HTML `<head>`:

```html
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600&display=swap" rel="stylesheet">
<script src="https://cdn.tailwindcss.com"></script>
<script>
  tailwind.config = {
    theme: {
      extend: {
        fontFamily: {
          sans: ['Inter', 'system-ui', 'sans-serif'],
        },
        colors: {
          'accent': '#1c1917',
          'accent-hover': '#292524',
          'muted': '#78716c',
          'error': '#dc2626',
          'error-bg': '#fef2f2',
          'success': '#16a34a',
          'success-bg': '#f0fdf4',
        }
      }
    }
  }
</script>
```

---

## Brand

**Default Style:** Minimal, warm, clean

**Typography:** Inter — a humanist sans-serif with subtle warmth

**Colors:**
- Accent: Stone black (`#1c1917`) — warm, sophisticated
- Muted: Stone gray (`#78716c`) — for helper text
- Backgrounds: Pure white
- Borders: Subtle (`stone-200`)

**Principles:**
- Generous whitespace
- Subtle borders, no shadows
- Typography does the heavy lifting
- One accent color, used sparingly
- Gentle transitions (`duration-200`)

**To customize:** Update the hex values in the config above. Keep it simple — one accent color is enough.

---

## Typography

| Element | Classes |
|---------|---------|
| H1 | `text-3xl font-semibold tracking-tight` |
| H2 | `text-2xl font-semibold tracking-tight` |
| H3 | `text-xl font-semibold` |
| Body | `text-base` |
| Small/Helper | `text-sm text-muted` |

---

## Components

### Button

```html
<!-- Primary -->
<button class="bg-accent hover:bg-accent-hover text-white font-medium px-4 py-2 rounded-lg transition-all duration-200">
  Button
</button>

<!-- Secondary -->
<button class="border border-stone-300 hover:border-stone-400 text-stone-700 font-medium px-4 py-2 rounded-lg transition-all duration-200">
  Button
</button>

<!-- Disabled -->
<button class="bg-accent text-white font-medium px-4 py-2 rounded-lg opacity-50 cursor-not-allowed" disabled>
  Button
</button>

<!-- Loading -->
<button class="bg-accent text-white font-medium px-4 py-2 rounded-lg opacity-75 cursor-wait" disabled>
  Loading...
</button>
```

### Card

```html
<div class="bg-white border border-stone-200 rounded-xl">
  <div class="p-5 border-b border-stone-100">
    <h3 class="font-semibold">Title</h3>
  </div>
  <div class="p-5">
    Content goes here.
  </div>
</div>
```

### Input

```html
<!-- Normal -->
<div class="flex flex-col gap-1.5">
  <label class="text-sm font-medium">Label</label>
  <input
    type="text"
    placeholder="Placeholder"
    class="border border-stone-300 rounded-lg px-3 py-2 focus:outline-none focus:ring-2 focus:ring-accent/20 focus:border-accent transition-all duration-200"
  />
  <span class="text-sm text-muted">Helper text</span>
</div>

<!-- Error -->
<div class="flex flex-col gap-1.5">
  <label class="text-sm font-medium">Email</label>
  <input
    type="email"
    value="bad-email"
    class="border border-error rounded-lg px-3 py-2 focus:outline-none focus:ring-2 focus:ring-error/20"
  />
  <span class="text-sm text-error">Please enter a valid email</span>
</div>
```

### Alert

```html
<!-- Error -->
<div class="p-4 bg-error-bg border border-error/20 rounded-lg">
  <p class="font-medium text-error">Something went wrong</p>
  <p class="text-sm text-muted mt-1">Please try again.</p>
</div>

<!-- Success -->
<div class="p-4 bg-success-bg border border-success/20 rounded-lg">
  <p class="font-medium text-success">Saved successfully</p>
</div>
```

### Empty State

```html
<div class="flex flex-col items-center justify-center py-16 text-center">
  <h3 class="text-lg font-semibold mb-1">No items yet</h3>
  <p class="text-muted mb-6">Create your first item to get started.</p>
  <button class="bg-accent hover:bg-accent-hover text-white font-medium px-4 py-2 rounded-lg transition-all duration-200">
    Create Item
  </button>
</div>
```

---

## Layout

```html
<!-- Container -->
<div class="max-w-3xl mx-auto px-6">
  Content
</div>

<!-- Stack -->
<div class="flex flex-col gap-6">
  <div>Item</div>
  <div>Item</div>
</div>

<!-- Row -->
<div class="flex items-center gap-4">
  <div>Item</div>
  <div>Item</div>
</div>
```

---

## Responsive

Mobile-first. Add prefixes for larger screens:

```html
<!-- Stack on mobile, row on desktop -->
<div class="flex flex-col md:flex-row gap-4">
  <div>Item</div>
  <div>Item</div>
</div>
```

| Prefix | Min Width |
|--------|-----------|
| `sm:` | 640px |
| `md:` | 768px |
| `lg:` | 1024px |

---

## Rules

1. **Use custom colors** — `accent`, `muted`, `error`, `success`
2. **Whitespace matters** — when in doubt, add more
3. **Subtle borders** — `stone-200` or `stone-300`, never heavy
4. **Every list needs an empty state**
5. **Every form input needs error handling**
6. **Every async action needs loading state**
7. **Mobile-first** — base is mobile, `md:` for desktop
