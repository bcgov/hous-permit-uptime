# GitHub App Migration - Simple Setup

## Your App Details
- **App Name:** HOUS-Upptime-Status-Page
- **Repository:** bcgov/hous-permit-uptime

## Setup (5 minutes)

### Step 1: Verify App Installation ✅

1. Go to your GitHub Repo
2. Settings → Installed GitHub Apps
3. Confirm `HOUS-Upptime-Status-Page` is listed

### Step 2: Remove Old PAT Secret (If Exists)

1. Settings → Secrets and variables → Actions
2. Find `GH_PAT` secret (if it exists)
3. Click delete and confirm

**Done!** Your workflows now use the GitHub App automatically.

---

## How It Works

Your Upptime workflows already support GitHub App authentication:

```yaml
token: ${{ secrets.GH_PAT || github.token }}
```

**Before (PAT):**
- Used Personal Access Token (less secure, manual management)

**Now (GitHub App - Option A):**
- Uses `github.token` (automatic, GitHub manages it)
- GitHub App permissions apply automatically
- More secure

---

## Testing

1. Go to Actions tab
2. Click "Uptime CI" workflow
3. Click "Run workflow" 
4. Check logs - should see no authentication errors

That's it! Everything else runs automatically.

---

## Token Management

GitHub automatically handles token rotation:
- Each workflow run gets a fresh token
- No manual refresh needed
- No 1-hour expiration issues (GitHub manages it)
- App permissions applied automatically

---

## Rollback (If Needed)

If something breaks:
1. Create a new `GH_PAT` secret with your old Personal Access Token value
2. Workflows will use that instead
3. Everything goes back to normal
