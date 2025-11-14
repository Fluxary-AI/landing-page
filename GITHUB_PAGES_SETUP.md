# GitHub Pages Setup Guide for fluxary.ai

## Step 1: Push to GitHub

1. Initialize git repository (if not already done):
   ```bash
   git init
   git add .
   git commit -m "Initial commit - Coming soon page"
   ```

2. Create a new repository on GitHub (e.g., `landing-page`)

3. Push to GitHub:
   ```bash
   git remote add origin https://github.com/YOUR_USERNAME/landing-page.git
   git branch -M main
   git push -u origin main
   ```

## Step 2: Enable GitHub Pages

1. Go to your repository on GitHub
2. Click on **Settings** tab
3. Scroll down to **Pages** section (in the left sidebar)
4. Under **Source**, select:
   - Branch: `main`
   - Folder: `/ (root)`
5. Click **Save**
6. Your site will be available at: `https://YOUR_USERNAME.github.io/landing-page/`

## Step 3: Configure Custom Domain (fluxary.ai)

### In GitHub:
1. In the same **Pages** settings section
2. Under **Custom domain**, enter: `fluxary.ai`
3. Check **Enforce HTTPS** (after DNS propagates)
4. Click **Save**

### In GoDaddy:
1. Log into your GoDaddy account
2. Go to **My Products** → **Domains** → **fluxary.ai** → **DNS**
3. Add/Edit DNS records:

   **Option A: Using A records (Recommended)**
   - Type: **A**
   - Name: `@` (or leave blank)
   - Value: `185.199.108.153`
   - TTL: 600 seconds
   
   - Type: **A**
   - Name: `@` (or leave blank)
   - Value: `185.199.109.153`
   - TTL: 600 seconds
   
   - Type: **A**
   - Name: `@` (or leave blank)
   - Value: `185.199.110.153`
   - TTL: 600 seconds
   
   - Type: **A**
   - Name: `@` (or leave blank)
   - Value: `185.199.111.153`
   - TTL: 600 seconds

   **Option B: Using CNAME (Alternative)**
   - Type: **CNAME**
   - Name: `@` (or `www`)
   - Value: `YOUR_USERNAME.github.io`
   - TTL: 600 seconds

4. Save the DNS records

### Create CNAME file (for custom domain):
Create a file named `CNAME` in the root of your repository with just:
```
fluxary.ai
```

Then commit and push:
```bash
echo "fluxary.ai" > CNAME
git add CNAME
git commit -m "Add CNAME for custom domain"
git push
```

## Step 4: Wait for DNS Propagation

- DNS changes can take 24-48 hours to propagate globally
- You can check propagation status at: https://www.whatsmydns.net/#A/fluxary.ai
- Once DNS propagates, GitHub will automatically enable HTTPS for your custom domain

## Step 5: Verify

1. Visit `http://fluxary.ai` (should redirect to HTTPS after propagation)
2. Check that the favicon appears in the browser tab
3. Verify the logo displays correctly

## Troubleshooting

- **Domain not working?** Wait 24-48 hours for DNS propagation
- **HTTPS not enabled?** Wait for DNS to fully propagate, then GitHub will enable it automatically
- **404 error?** Make sure your `index.html` is in the root directory and GitHub Pages is enabled
- **Favicon not showing?** Clear browser cache or try incognito mode

## Notes

- GitHub Pages is free for public repositories
- Custom domains are free
- HTTPS is automatically enabled once DNS is configured
- Your site will update automatically when you push changes to the `main` branch

