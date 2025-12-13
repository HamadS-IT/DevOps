# How to `Deploy` a `Static Website` on `GitHub Pages`?

GitHub Pages allows you to host static websites (HTML, CSS, JavaScript) directly from a GitHub repository for free.

---

## Prerequisites

- A GitHub account
- Git installed on your machine
- A static website (HTML/CSS/JS files)

---

## Step 1: Create a GitHub Repository

1. Go to https://github.com
2. Click **New Repository**
3. Name your repository (e.g., `my-static-website`)
4. Set it to **Public**
5. Click **Create repository**

---

## Step 2: Prepare Your Project

Your project should include at least:

```text
index.html
style.css
script.js (optional)
````

> ⚠️ `index.html` is required as the entry point.

---

## Step 3: Push Your Code to GitHub

```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/<username>/<repository-name>.git
git push -u origin main
```

Replace `<username>` and `<repository-name>` with your own.

---

## Step 4: Enable GitHub Pages

1. Go to your repository on GitHub
2. Click **Settings**
3. Navigate to **Pages**
4. Under **Source**:

   * Select **Deploy from a branch**
   * Choose:

     * Branch: `main`
     * Folder: `/root`
5. Click **Save**

---

## Step 5: Access Your Website

After a few seconds, your site will be available at:

```text
https://<username>.github.io/<repository-name>/
```

GitHub will show the live URL in the **Pages** section.

---

## Optional: Custom Domain

1. Buy a domain (e.g., from Namecheap or Google Domains)
2. In **Settings → Pages**, add your custom domain
3. Update DNS records as instructed by GitHub

---

## Common Issues

### Page Not Loading?

* Ensure `index.html` is in the root directory
* Check that the repository is **public**
* Wait a minute and refresh

### CSS/JS Not Applying?

* Use relative paths:

```html
<link rel="stylesheet" href="./style.css">
<script src="./script.js"></script>
```

---

## Example Repository Structure

```text
my-static-website/
├── index.html
├── style.css
└── script.js
```

---

## Conclusion

GitHub Pages is a fast and free way to deploy static websites. Perfect for portfolios, documentation, and demos.

Happy deploying 🚀
