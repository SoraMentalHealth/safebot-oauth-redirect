# SafeBot OAuth Redirect Handler

This is a simple OAuth redirect handler for the SafeBot mobile app.

## Files

- `callback.html` - The main OAuth callback handler that redirects to the app
- `index.html` - Landing page for the GitHub Pages site

## Deployment Instructions

### Option 1: GitHub Pages (Recommended)

1. **Create a new GitHub repository** named `safebot-oauth-redirect`
2. **Upload these files** to the repository:
   - `callback.html`
   - `index.html`
3. **Enable GitHub Pages**:
   - Go to repository Settings > Pages
   - Set Source to "Deploy from a branch"
   - Select "main" branch and "/ (root)" folder
   - Click Save
4. **Your redirect URL will be**:
   ```
   https://soramentalhealth.github.io/safebot-oauth-redirect/callback.html
   ```

### Option 2: Vercel/Netlify

1. **Create a new project** on Vercel or Netlify
2. **Upload these files** to the project
3. **Deploy the project**
4. **Your redirect URL will be**:
   ```
   https://your-project.vercel.app/callback.html
   ```

## Google Cloud Console Setup

1. Go to [Google Cloud Console](https://console.cloud.google.com/)
2. Navigate to APIs & Services > Credentials
3. Find your OAuth 2.0 Client ID
4. Add your deployed redirect URL as the **only** redirect URI:
   ```
   https://soramentalhealth.github.io/safebot-oauth-redirect/callback.html
   ```
5. Remove all other redirect URIs

## App Configuration

Update your app's OAuth configuration to use your deployed redirect URL:

```javascript
const redirectUri = 'https://soramentalhealth.github.io/safebot-oauth-redirect/callback.html';
```

## How It Works

1. User clicks "Continue with Google" in your app
2. Browser opens for Google sign-in
3. User completes sign-in
4. Google redirects to your HTTPS callback page
5. The callback page immediately redirects to your app using the custom scheme
6. User is back in your app with successful authentication

## Security

- Only your app can handle the `safebot://` custom scheme
- The redirect page is hosted on your own domain
- No third-party services involved in the OAuth flow 