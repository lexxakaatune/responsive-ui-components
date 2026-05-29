```
# Responsive UI Components

A collection of plain HTML, CSS, and vanilla JavaScript components I built because I was tired of importing entire UI libraries just to use a navbar and a button. No frameworks. No build steps. No npm install. Just copy the folder you need and tweak the CSS variables until it looks like your brand.

I use these in my own projects and figured other people might find them useful too. Everything is MIT licensed — take it, break it, improve it, whatever.

---

## What's inside

| Component | Folder | What it does |
|-----------|--------|-------------|
| **Navbar** | `navbar/` | Responsive nav with a hamburger menu that animates into a clean X. Uses a tiny bit of JS for the toggle. |
| **Login Form** | `login-form/` | Centered card-style form with email, password, remember me, and forgot password link. Ready for validation. |
| **Hero Section** | `hero-section/` | Two-column layout with text + image that stacks on mobile. Uses `clamp()` for fluid typography. |
| **Footer** | `footer/` | Multi-column footer with brand info, link groups, and an auto-updating year. |
| **Buttons** | `buttons/` | 9 color variants (primary, secondary, success, danger, warning, info, dark, light, ghost), 3 sizes, pill style, and icon-only circles. Each has its own shadow and hover color. |
| **Card** | `card/` | Article cards with image, tag, title, meta date, description, and CTA. Built with semantic `<article>`, `<figure>`, `<header>`, `<footer>`, and `<time>`. |
| **Modal** | `modal/` | Accessible modal using the native `<dialog>` element. Handles backdrop click, Escape key, focus trap, body scroll lock, and focus restoration. No dependencies. |
| **Alert** | `alert/` | Dismissible alert banners in success, error, warning, and info colors. Smooth slide-out animation when you close them. |
| **Accordion** | `accordion/` | FAQ-style collapsible sections using native `<details>` and `<summary>`. The `name` attribute makes them exclusive (only one open at a time). Zero JavaScript. |
| **Form Inputs** | `form-inputs/` | Styled text inputs, email, password, textarea, select dropdown, custom checkboxes, custom radio buttons, and animated toggle switches. All with proper focus rings and labels. |
| **Tabs** | `tabs/` | Content-switching tabs with full keyboard support (arrow keys, Home, End). Uses `role="tablist"`, `role="tab"`, and `role="tabpanel"` for screen readers. |
| **Breadcrumb** | `breadcrumb/` | Simple breadcrumb trail using `<nav>`, `<ol>`, and `<li>`. Includes `aria-current="page"` on the active item. Two visual styles: boxed and minimal. |
| **Pagination** | `pagination/` | Real-world pagination with dynamic page generation, ellipsis logic, boundary pages, and disabled Prev/Next states. Pass it your current page and total pages and it renders itself. |

---

## How to use

1. Download or clone the repo.
2. Open any component's `index.html` in your browser to see it in action.
3. Copy the HTML and CSS into your project.
4. Edit the CSS variables at the top of each `style.css` file to match your colors.

That's it. No webpack. No vite. No tailwind config.

### Customizing colors

Every component uses CSS custom properties. Want to change the navbar from dark blue to black? Just change the variable:

```css
/* navbar/style.css */
:root {
  --nav-bg: #0a0a0a;        /* was #1a1a2e */
  --nav-accent: #f59e0b;    /* was #e94560 */
  --nav-height: 72px;       /* was 64px */
}
```

Same deal with buttons:

```css
/* buttons/style.css */
:root {
  --btn-primary-bg: #7c3aed;    /* purple instead of blue */
  --btn-danger-bg: #be123c;       /* deeper red */
  --btn-success-bg: #059669;      /* deeper green */
}
```
```
```
---

## Component notes

### Buttons

The button classes work like Lego. You need the base `.btn` class, then add a variant and a size:

```html
<button class="btn btn-primary btn-md">Click me</button>
<button class="btn btn-success btn-lg btn-pill">Pill button</button>
<button class="btn btn-danger btn-sm" disabled>Disabled</button>
```

Variants: `btn-primary`, `btn-secondary`, `btn-success`, `btn-danger`, `btn-warning`, `btn-info`, `btn-dark`, `btn-light`, `btn-ghost`

Sizes: `btn-sm`, `btn-md`, `btn-lg`

Extras: `btn-pill` (fully rounded), `btn-icon` (circular icon-only), `btn-block` (full width)

### Modal

The modal uses the native HTML `<dialog>` element. Open it with JavaScript:

```js
const dialog = document.getElementById('confirm-dialog');
dialog.showModal();   // opens with backdrop
dialog.close();       // closes and returns focus to the trigger button
```

It already handles:
- Clicking the backdrop closes it
- Pressing Escape closes it
- Tab cycles only inside the modal (focus trap)
- Body scroll is locked while open
- Focus goes back to the button that opened it when closed

### Card

Cards are semantic `<article>` elements. Swap the image, update the `<time>` datetime, and change the text. The container uses CSS Grid with `auto-fit` so cards reflow naturally on any screen size. A single `.card` works anywhere — you don't need the grid wrapper if you only want one.

### Accordion

Built with native `<details>` and `<summary>` elements. The `name="faq"` attribute on each `<details>` creates an exclusive accordion — opening one section automatically closes the others. This is supported in all modern browsers and requires zero JavaScript.

### Pagination

The pagination component includes a small vanilla JS class that generates the page numbers dynamically. It handles the math for showing boundary pages, sibling pages, and ellipsis. Use it like this:

```js
Pagination.init(document.querySelector('.pagination'), {
  current: 1,
  total: 50,
  siblingCount: 1,   // pages shown on each side of current
  boundaryCount: 1,  // always show first and last page
  onChange: (page) => {
    // fetch your data here
    console.log('Loading page', page);
  },
});
```

If you don't need the JS, the CSS works fine with static HTML too.

### Breadcrumb

Breadcrumbs are intentionally static HTML. In real projects, they're generated by your router or backend based on the current URL path. The component provides the accessible markup structure — an `<ol>` with `<li>` items, proper `aria-label`, and `aria-current="page"` on the active item. Generate the array server-side and loop over it.
```
```
---

## Browser support

Tested in the latest versions of Chrome, Firefox, Safari, and Edge. Uses standard CSS like Flexbox, CSS Grid, `clamp()`, custom properties, and the native `<dialog>` element. If you need to support Internet Explorer 11, this is not the repo for you (and honestly, neither is 2026).

---

## Contributing

Found a bug? Want to add a component? Open an issue or pull request. A few ground rules:

- Keep it framework-free. No React, no Vue, no Svelte. Plain HTML/CSS/JS only.
- Use semantic HTML where possible. `<article>`, `<nav>`, `<dialog>`, `<details>`, `<fieldset>`, etc.
- Add CSS variables for theming. Nobody wants to hunt through 300 lines of CSS to change a button color.
- Keep the JS small. If it needs more than 50 lines, it probably belongs in a different repo.

---

## License

MIT. Do whatever you want with it. Use it in commercial projects, personal projects, client work, whatever. No attribution required (though it's nice if you do). Just don't blame me if something breaks.

---

## Why I made this

I got tired of installing 50kb of JavaScript just to render a navbar. Most UI libraries are great, but sometimes you just need a clean, responsive component you can drop into a static site or a Laravel project without learning a new framework. These are the components I copy-paste between projects, cleaned up and documented so I don't have to rebuild them every time.

Hope they save you some time too.
```
