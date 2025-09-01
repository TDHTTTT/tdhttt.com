# Claude Assistant Knowledge Base for tdhttt.com

## Repository Structure
- **Main site**: Deployed from `main` branch to tdhttt.com
- **Blog site**: Deployed from `blog` branch to blog.tdhttt.com
- **Important**: These are two separate branches that should NOT be merged

## Netlify Deployment Setup

### Branch Configuration
- Production site (tdhttt.com): Deploys from `main` branch
- Blog site (blog.tdhttt.com): Deploys from `blog` branch as a Branch Deploy
- Branch subdomain is configured: `blog` → `blog.tdhttt.com`

### Build Configuration (netlify.toml)
```toml
[build]
  publish = "public"
  command = "hugo"

[build.environment]
  HUGO_VERSION = "0.101.0"
  HUGO_ENV = "production"
  HUGO_ENABLEGITINFO = "true"

[context.branch-deploy]
  command = "hugo"  # Uses baseURL from config.toml

[context.deploy-preview]
  command = "hugo -b $DEPLOY_PRIME_URL"
```

### Key Fix for Custom Domain
- Don't use `$DEPLOY_PRIME_URL` for branch deploys if you want to use custom domain
- Let Hugo use the `baseURL` from config.toml instead

## Hugo Configuration
- Hugo version: v0.101.0+extended
- Base URL for blog: `https://blog.tdhttt.com/`
- Theme: casper
- Config file: `config.toml`

## Content Management
- Blog posts location: `/content/post/`
- Image assets: `/static/images/`

## Deployment Workflow
1. Make changes on the `blog` branch
2. Commit changes: `git add . && git commit -m "message"`
3. Push to trigger deployment: `git push origin blog`
4. Netlify automatically builds and deploys to blog.tdhttt.com

## Common Issues & Solutions

### Hugo not found error
- **Problem**: "hugo: command not found" during Netlify build
- **Solution**: Add netlify.toml with HUGO_VERSION environment variable

### Wrong domain in links
- **Problem**: Links showing Netlify subdomain instead of custom domain
- **Solution**: Remove `-b $DEPLOY_PRIME_URL` from branch-deploy command in netlify.toml

## Testing Commands
- Build locally: `hugo`
- Serve locally: `hugo server`
- Check Hugo version: `hugo version`

## Git Branches
- `master`: Old default branch (legacy)
- `main`: Current production branch
- `blog`: Blog deployment branch
- Various feature branches for specific updates