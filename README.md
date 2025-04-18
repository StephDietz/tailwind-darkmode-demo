# 🌙 Tailwind Dark Mode Toggle Example

This project demonstrates how to implement a dark mode toggle using Tailwind CSS with custom utility classes and a simple JavaScript toggle function.

## 🧩 Enable Dark Variant in CSS

By default, Tailwind’s `dark:` variant is based on the `prefers-color-scheme` media query (i.e. your system setting). To manually toggle dark mode using a dark class (like `<html class="dark"`>), you need to override the dark variant with a custom selector.

Add this line at the top of your main CSS file (e.g. `main.css` or `style.css`):

```css
@custom-variant dark (&:where(.dark, .dark \*));
```

Now instead of `dark:*` utilities being applied based on `prefers-color-scheme`, they will be applied whenever the `dark` class is present earlier in the HTML tree.

Without this, `dark:` will only work if the system settings is set to dark mode. They will not be able to manually toggle it on.

## 🌗 Dark Mode Toggle

We need a _tiny_ bit of JavaScript to make this work. Add this JavaScript function somewhere in your app (e.g., `main.js`):

```js
function toggleTheme() {
  const html = document.documentElement
  const isDark = html.classList.contains('dark')

  if (isDark) {
    html.classList.remove('dark')
    localStorage.theme = 'light'
  } else {
    html.classList.add('dark')
    localStorage.theme = 'dark'
  }
}
```

Call this function using a button:

```html
<button onclick="toggleTheme()">Toggle Dark Mode</button>
```

💡 The `dark:` variants in Tailwind will automatically respond to the presence of the dark class on `<html>`.

## 🎨 Custom Tailwind Utility Classes

You can define reusable component-level styles in your CSS file using `@apply` inside the `@layer` components block:

```css
@layer components {
  .dashboard-card {
    @apply bg-white dark:bg-zinc-900 text-zinc-800 dark:text-white rounded-xl p-4 shadow;
  }
}
```

Use them in your Vue components like this:

```html
<div class="dashboard-card">
  <h2 class="text-lg font-bold">Today's Sales</h2>
  <p>$1,200</p>
</div>
```

## Testing

To run this locally, `npm install` and `npm run dev`.

This demo is also deployed on Vercel and can be found here:
# tailwind-darkmode-demo
