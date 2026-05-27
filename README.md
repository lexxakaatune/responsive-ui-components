# Responsive UI Components

A small, open-source collection of responsive UI components built with plain HTML, CSS, and a touch of vanilla JavaScript. No frameworks, no build steps—just copy, paste, and customize.

## What's inside

| Component | Files |
|-----------|-------|
| **Navbar** | `navbar/index.html` + `style.css` |
| **Login Form** | `login-form/index.html` + `style.css` |
| **Hero Section** | `hero-section/index.html` + `style.css` |
| **Footer** | `footer/index.html` + `style.css` |

Each component lives in its own folder with its own stylesheet, so you can grab exactly what you need without untangling a giant codebase.

## How to use

1. Clone or download this repo.
2. Open any `index.html` in your browser to preview the component.
3. Copy the HTML and CSS into your project.
4. Tweak the CSS variables at the top of each `style.css` to match your brand.

### Example: customizing the navbar

```css
:root {
  --nav-bg: #0f172a;        /* change background */
  --nav-accent: #38bdf8;    /* change accent color */
  --nav-height: 72px;       /* change height */
}
```

## Browser support

Tested in modern versions of Chrome, Firefox, Safari, and Edge. Uses standard CSS like Flexbox, `clamp()`, and custom properties.

## Contributing

Found a bug or want to add a component? Feel free to open an issue or pull request. Keep it simple and framework-free so everyone can use it.

## License

MIT — do whatever you want with it, just don't sue me 😂.
