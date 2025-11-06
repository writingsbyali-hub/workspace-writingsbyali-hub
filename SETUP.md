# Workspace Template Setup Guide

This guide explains how to set up your personal Workspace after forking this template.

## Automatic Setup (Recommended)

If you signed up through the Workspace platform:
1. ✅ Repository automatically forked to your account
2. ✅ Branches (`main` and `draft`) already created
3. ✅ GitHub webhook configured for cache sync

**You're ready to go!** Just navigate to your workspace and start creating content.

## Manual Setup (Advanced Users)

If you want to set up manually or self-host:

### 1. Fork or Clone

```bash
# Option A: Fork via GitHub UI
# Click "Use this template" or "Fork" button

# Option B: Clone directly
git clone https://github.com/workspace-by-ali/workspace-template.git my-workspace
cd my-workspace
```

### 2. Create Branches

```bash
# Ensure you have both main and draft branches
git checkout -b draft
git push origin draft
git checkout main
```

### 3. Install Dependencies

```bash
npm install
# or
pnpm install
# or
yarn install
```

### 4. Configure Environment Variables

Create `.env` file:

```env
# Supabase (required for auth)
PUBLIC_SUPABASE_URL=your-supabase-url
PUBLIC_SUPABASE_ANON_KEY=your-anon-key

# GitHub (for Keystatic)
PUBLIC_GITHUB_REPO_OWNER=your-username
PUBLIC_GITHUB_REPO_NAME=workspace-by-your-username

# Optional: GitHub OAuth App (for publishing from UI)
GITHUB_CLIENT_ID=your-client-id
GITHUB_CLIENT_SECRET=your-client-secret
```

### 5. Run Development Server

```bash
npm run dev
```

Visit:
- **Site**: http://localhost:4321
- **Keystatic CMS**: http://localhost:4321/keystatic

### 6. Deploy

#### Vercel (Recommended)

```bash
# Install Vercel CLI
npm i -g vercel

# Deploy
vercel

# Set environment variables
vercel env add PUBLIC_SUPABASE_URL
vercel env add PUBLIC_SUPABASE_ANON_KEY
# ... add all env vars

# Deploy to production
vercel --prod
```

#### Netlify

```bash
# Install Netlify CLI
npm i -g netlify-cli

# Deploy
netlify deploy

# Set environment variables in Netlify UI
# Then deploy to production
netlify deploy --prod
```

#### GitHub Pages

```bash
# Build static site
npm run build

# Deploy to gh-pages branch
npm run deploy
```

### 7. Configure GitHub Webhook (Optional)

For automatic cache sync when you push to GitHub:

1. Go to your repo → Settings → Webhooks → Add webhook
2. **Payload URL**: `https://your-workspace-url.vercel.app/api/webhooks/github`
3. **Content type**: `application/json`
4. **Secret**: (generate a random string, store in env as `GITHUB_WEBHOOK_SECRET`)
5. **Events**: Select "Just the push event"
6. Click "Add webhook"

## Customization

### Change Site Title

Edit `astro.config.mjs`:

```js
export default defineConfig({
  site: 'https://your-username.github.io',
  base: '/workspace',
  // ... other config
});
```

### Add Custom Logo

1. Add logo file to `public/images/logo.png`
2. Update Keystatic config or layout components to use it

### Modify Branding

Edit brand colors in your Astro layouts while maintaining accessibility:
- Ensure contrast ratios meet WCAG AA standards
- Test with color-blind simulators
- Keep consistent with Workspace design principles

## Keystatic Configuration

### Local Editing

Keystatic works locally out of the box. Just run `npm run dev` and visit `/keystatic`.

### Cloud Editing (GitHub Backend)

For editing content directly from your deployed site:

1. Create GitHub OAuth App:
   - Go to GitHub Settings → Developer settings → OAuth Apps
   - **Homepage URL**: `https://your-workspace-url.vercel.app`
   - **Callback URL**: `https://your-workspace-url.vercel.app/api/keystatic/github/oauth/callback`
   - Copy Client ID and Client Secret

2. Add to environment variables:
   ```env
   GITHUB_CLIENT_ID=your-client-id
   GITHUB_CLIENT_SECRET=your-client-secret
   ```

3. Redeploy your site

Now you can edit content from anywhere using the `/keystatic` admin panel!

## Content Management

### Creating Projects

Two methods:

**1. Via Keystatic (Recommended)**
- Navigate to `/keystatic`
- Click "Projects" → "Create New"
- Fill in details and save
- Changes commit to `draft` branch

**2. Manual (Advanced)**
```bash
# Create project structure
mkdir -p content/projects/my-project/streams/my-stream/{updates,docs,data}

# Create README files with frontmatter
# Edit files
# Commit and push to draft
git add .
git commit -m "Add new project"
git push origin draft
```

### Publishing Changes

**Via UI:**
1. Review changes in draft branch
2. Click "Publish" button in your workspace
3. Confirms merge draft → main

**Manual:**
```bash
git checkout main
git merge draft
git push origin main
```

## Safety Gating

To gate hazardous content:

1. Create `.access.yml` in project directory:
   ```yaml
   gated: true
   required_acknowledgment: "your_safety_code_v1.0"
   risk_level: "high"
   ```

2. Create safety documentation in `public/docs/safety/your-protocol.md`

3. Users must acknowledge before viewing content

## Troubleshooting

### Keystatic Not Loading

- Check GitHub token is valid
- Ensure `GITHUB_CLIENT_ID` and `GITHUB_CLIENT_SECRET` are set
- Verify OAuth callback URL matches deployment

### Changes Not Publishing

- Check both `main` and `draft` branches exist
- Verify GitHub token has `repo` scope
- Check webhook is configured correctly

### Build Errors

```bash
# Clear cache and rebuild
rm -rf node_modules .astro dist
npm install
npm run build
```

## Support

- [Full Documentation](../../docs/README.md)
- [GitHub Issues](https://github.com/workspace-by-ali/workspace-by-ali/issues)
- [Community Discussions](https://github.com/workspace-by-ali/workspace-by-ali/discussions)

---

**Need Help?** Open an issue or ask in community discussions!
