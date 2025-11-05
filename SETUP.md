# Quick Setup Guide

## Step 1: Install Dependencies
```bash
npm install
```

## Step 2: Get Google OAuth Credentials

1. Visit [Google Cloud Console](https://console.cloud.google.com/)
2. Create a project or select an existing one
3. Go to **APIs & Services** > **Credentials**
4. Click **Create Credentials** > **OAuth client ID**
5. Configure OAuth consent screen if needed
6. Select **Web application**
7. Add redirect URI: `http://localhost:3000/api/auth/callback/google`
8. Copy **Client ID** and **Client Secret**

## Step 3: Create Environment File

Create a file named `.env.local` in the root directory with:

```env
GOOGLE_CLIENT_ID=your_google_client_id_here
GOOGLE_CLIENT_SECRET=your_google_client_secret_here
NEXTAUTH_SECRET=generate_a_random_secret_here
NEXTAUTH_URL=http://localhost:3000
```

To generate a random secret, run:
```bash
openssl rand -base64 32
```

## Step 4: Run the Application

```bash
npm run dev
```

Visit [http://localhost:3000](http://localhost:3000) to see the login page.


