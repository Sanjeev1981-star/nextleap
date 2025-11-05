# NextLeap - Google Authentication

A modern login page with Google OAuth integration built with Next.js 14, NextAuth.js, and Tailwind CSS.

## Features

- 🔐 Google OAuth 2.0 authentication
- 🎨 Beautiful, modern UI with Tailwind CSS
- 🔒 Secure session management with NextAuth.js
- 📱 Responsive design
- ⚡ Built with Next.js 14 App Router

## Getting Started

### Prerequisites

- Node.js 18+ installed
- A Google Cloud Console project with OAuth 2.0 credentials

### Setup Google OAuth Credentials

1. Go to [Google Cloud Console](https://console.cloud.google.com/)
2. Create a new project or select an existing one
3. Navigate to **APIs & Services** > **Credentials**
4. Click **Create Credentials** > **OAuth client ID**
5. Configure the OAuth consent screen if prompted
6. Select **Web application** as the application type
7. Add authorized redirect URIs:
   - `http://localhost:3000/api/auth/callback/google` (for development)
   - `https://yourdomain.com/api/auth/callback/google` (for production)
8. Copy the **Client ID** and **Client Secret**

### Installation

1. Clone the repository and install dependencies:
```bash
npm install
```

2. Create a `.env.local` file in the root directory:
```bash
cp .env.local.example .env.local
```

3. Update `.env.local` with your credentials:
```env
GOOGLE_CLIENT_ID=your_google_client_id_here
GOOGLE_CLIENT_SECRET=your_google_client_secret_here
NEXTAUTH_SECRET=your_nextauth_secret_here
NEXTAUTH_URL=http://localhost:3000
```

4. Generate a NextAuth secret (optional but recommended):
```bash
openssl rand -base64 32
```

### Running the Application

```bash
npm run dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser.

## Project Structure

```
nextleap/
├── app/
│   ├── api/
│   │   └── auth/
│   │       └── [...nextauth]/
│   │           └── route.ts      # NextAuth configuration
│   ├── dashboard/
│   │   └── page.tsx              # Protected dashboard page
│   ├── layout.tsx                # Root layout with providers
│   ├── page.tsx                  # Login page
│   ├── providers.tsx             # Session provider wrapper
│   └── globals.css               # Global styles
├── package.json
└── README.md
```

## How It Works

1. **Login Page** (`app/page.tsx`): Displays a beautiful login interface with a "Sign in with Google" button
2. **NextAuth API Route** (`app/api/auth/[...nextauth]/route.ts`): Handles the OAuth flow with Google
3. **Dashboard** (`app/dashboard/page.tsx`): Protected route that displays user information after successful authentication
4. **Session Provider** (`app/providers.tsx`): Wraps the app to provide session context

## Customization

- **Styling**: Modify `app/globals.css` and Tailwind classes in components
- **Redirect URLs**: Update callback URLs in Google Cloud Console and `NEXTAUTH_URL` in `.env.local`
- **Protected Routes**: Add more protected pages in the `app/` directory and use `useSession()` hook

## Security Notes

- Never commit `.env.local` to version control
- Use strong, randomly generated `NEXTAUTH_SECRET`
- Keep your Google OAuth credentials secure
- Use HTTPS in production

## License

MIT



