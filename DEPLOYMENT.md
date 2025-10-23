# Deployment Guide

## Quick Deployment to GitHub Pages

### Step 1: Initialize Git Repository

```bash
cd adarsh-umesh-portfolio
git init
git add -A
git commit -m "Initial commit: Portfolio website for Adarsh Umesh"
```

### Step 2: Create GitHub Repository

1. Go to https://github.com/new
2. Repository name: `adarsh-umesh-portfolio` or `adarshumesh5.github.io` (for automatic GitHub Pages)
3. Make it **Public**
4. **Do NOT** initialize with README, .gitignore, or license (we already have these)
5. Click **Create repository**

### Step 3: Push to GitHub

Replace `YOUR_USERNAME` with your actual GitHub username (adarshumesh5):

```bash
git remote add origin https://github.com/adarshumesh5/adarsh-umesh-portfolio.git
git branch -M main
git push -u origin main
```

### Step 4: Enable GitHub Pages

1. Go to your repository on GitHub
2. Click **Settings** → **Pages** (in the left sidebar)
3. Under **Source**, select:
   - Branch: `main`
   - Folder: `/ (root)`
4. Click **Save**
5. Wait 1-2 minutes for deployment

### Step 5: Access Your Website

Your site will be available at:
- If repo name is `adarshumesh5.github.io`: https://adarshumesh5.github.io
- If repo name is `adarsh-umesh-portfolio`: https://adarshumesh5.github.io/adarsh-umesh-portfolio

---

## Alternative: Using the Automated Script

### Prerequisites

The automated deployment script requires:

1. **jq** (JSON processor)
   - Windows: `choco install jq` or download from https://stedolan.github.io/jq/
   - Mac: `brew install jq`
   - Linux: `apt-get install jq`

2. **GitHub CLI**
   - Download from: https://cli.github.com/
   - Windows: `winget install --id GitHub.cli`
   - Mac: `brew install gh`

3. **GitHub Personal Access Token (PAT)**
   - Go to https://github.com/settings/tokens/new
   - Select scopes: `repo`, `workflow`
   - Generate and copy the token

### Run the Script

```bash
export GH_TOKEN="ghp_YOUR_TOKEN_HERE"
./deploy_automated.sh
```

Or:

```bash
./deploy_automated.sh --token="ghp_YOUR_TOKEN_HERE"
```

---

## Updating Your Portfolio

After initial deployment, to update your site:

```bash
git add -A
git commit -m "Update portfolio content"
git push
```

GitHub Pages will automatically rebuild and deploy your changes.

---

## Troubleshooting

### Authentication Issues

If you have authentication issues, use a Personal Access Token:

```bash
git remote set-url origin https://YOUR_TOKEN@github.com/adarshumesh5/adarsh-umesh-portfolio.git
git push
```

### Force Push (if needed)

If you need to overwrite remote history:

```bash
git push -f origin main
```

**Warning**: Only use force push if you're sure you want to overwrite the remote repository.

---

## Custom Domain (Optional)

To use a custom domain like `adarshum.com`:

1. Create a `CNAME` file in the root directory with your domain:
   ```
   adarshum.com
   ```

2. Configure DNS records at your domain registrar:
   - Type: A, Host: @, Value: 185.199.108.153
   - Type: A, Host: @, Value: 185.199.109.153
   - Type: A, Host: @, Value: 185.199.110.153
   - Type: A, Host: @, Value: 185.199.111.153
   - Type: CNAME, Host: www, Value: adarshumesh5.github.io

3. Enable "Enforce HTTPS" in GitHub Pages settings

---

## Need Help?

- GitHub Pages Documentation: https://docs.github.com/en/pages
- Git Documentation: https://git-scm.com/doc
- GitHub CLI: https://cli.github.com/manual/
