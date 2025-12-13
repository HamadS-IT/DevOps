# How to `Deploy` a `Vite + React App` on `GitHub Pages`?

This guide explains how to deploy a Vite + React application to **GitHub Pages**.

---

## Prerequisites

- A GitHub account
- Git installed
- Node.js (v16+ recommended)
- A Vite + React project

---

## Step 1: Create a Vite + React App (If Not Already Created)

```bash
npm create vite@latest my-vite-app -- --template react
cd my-vite-app
npm install
npm run dev
````

---

## Step 2: Update `vite.config.js`

GitHub Pages serves your app from a subpath, so you must set the `base` option.

```js
import { defineConfig } from 'vite'
import react from '@vitejs/plugin-react'

export default defineConfig({
  plugins: [react()],
  base: '/<repository-name>/',
})
```

Replace `<repository-name>` with your GitHub repository name.

---

## Step 3: Build the Project

```bash
npm run build
```

This creates a `dist/` folder with production-ready files.

---

## Step 4: Create a GitHub Repository

1. Go to [https://github.com](https://github.com)
2. Click **New Repository**
3. Name it the same as your project (recommended)
4. Set it to **Public**
5. Create the repository

---

## Step 5: Install `gh-pages`

```bash
npm install --save-dev gh-pages
```

---

## Step 6: Update `package.json`

Add the following fields:

```json
{
  "homepage": "https://<username>.github.io/<repository-name>",
  "scripts": {
    "dev": "vite",
    "build": "vite build",
    "preview": "vite preview",
    "deploy": "gh-pages -d dist"
  }
}
```

Replace `<username>` and `<repository-name>` accordingly.

---

## Step 7: Deploy to GitHub Pages

```bash
npm run deploy
```

This pushes the `dist` folder to a `gh-pages` branch.

---

## Step 8: Enable GitHub Pages

1. Go to your repository → **Settings**
2. Open **Pages**
3. Under **Source**:

   * Select **Deploy from a branch**
   * Choose:

     * Branch: `gh-pages`
     * Folder: `/root`
4. Save changes

---

## Step 9: Access Your Website

Your app will be live at:

```text
https://<username>.github.io/<repository-name>/
```

Deployment may take a minute.

---

## Common Issues & Fixes

### Blank Page After Deployment

* Ensure `base` in `vite.config.js` is correct
* Confirm repository name matches exactly

### Routing Issues (React Router)

GitHub Pages doesn’t support client-side routing by default.

**Solution:** Use `HashRouter`

```jsx
import { HashRouter } from 'react-router-dom'

<HashRouter>
  <App />
</HashRouter>
```

---

## Project Structure Example

```text
my-vite-app/
├── dist/
├── src/
├── index.html
├── vite.config.js
└── package.json
```

---

## Conclusion

Using Vite + GitHub Pages provides a fast, free, and simple deployment solution for React apps.

Happy coding 🚀
