# Next.js Auth Starter Kit

A production-ready authentication boilerplate built with Next.js, NextAuth.js v5, Prisma, and Shadcn UI. Get started with secure user authentication in minutes.

## ✨ Features

- **Credentials-Based Authentication**: Secure email and password login.
- **Social Logins**: Integrated with Google and GitHub for easy sign-in.
- **Email Verification**: Ensure users have a valid email address.
- **Password Reset**: Secure flow for users to reset their password.
- **Two-Factor Authentication (2FA)**: Add an extra layer of security with TOTP.
- **User Profile Management**: Users can view and update their personal information.
- **Avatar Uploads**: Local file uploads for profile pictures, powered by Vercel Blob.
- **Account Settings**: Manage security, notifications, and privacy settings.
- **Secure Server Actions**: All authentication and user management logic is handled securely on the server.
- **Validation**: End-to-end type-safe validation with Zod.

## 🚀 Tech Stack

- **Framework**: [Next.js](https://nextjs.org/) 15
- **Authentication**: [NextAuth.js (Auth.js v5)](https://authjs.dev/)
- **ORM**: [Prisma](https://www.prisma.io/)
- **UI**: [Tailwind CSS](https://tailwindcss.com/) & [Shadcn UI](https://ui.shadcn.com/)
- **Validation**: [Zod](https://zod.dev/)
- **File Storage**: [Vercel Blob](https://vercel.com/storage/blob)
- **Package Manager**: [pnpm](https://pnpm.io/)

## 🏁 Getting Started

Follow these steps to get the project up and running on your local machine.

### Prerequisites

- [Node.js](https://nodejs.org/en) (v18 or later)
- [pnpm](https://pnpm.io/installation)

### 1. Clone the Repository

```bash
git clone https://github.com/Dendro-X0/next-authjs-starter.git
cd next-authjs-starter
```

### 2. Install Dependencies

```bash
pnpm install
```

### 3. Set Up Environment Variables

Copy the example environment file and fill in the required variables.

```bash
cp .env.example .env
```

You will need to provide credentials for your database, authentication providers (Google, GitHub), email service (e.g., Resend), and Vercel Blob.

### 4. Set Up the Database

Push the Prisma schema to your database and generate the Prisma Client.

```bash
pnpm prisma migrate dev
pnpm prisma generate
```

For production/CI, use:

```bash
pnpm prisma migrate deploy
```

### 5. Run the Development Server

```bash
pnpm dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser to see the application.

## 📂 Project Structure

```
.
├── src
│   ├── app         # App Router pages and layouts
│   ├── actions     # Server-side actions for auth and user management
│   ├── components  # Reusable UI components
│   ├── lib         # Library functions (db, mail, etc.)
│   └── schemas     # Zod validation schemas
├── prisma          # Prisma schema and migrations
└── ...
```

## 🔧 Troubleshooting

### Common Issues

#### 1. **pnpm Virtual Store Issues**
If you encounter virtual store location conflicts:
```bash
pnpm config set virtual-store-dir "node_modules/.pnpm"
rm -rf node_modules pnpm-lock.yaml
pnpm install
```

#### 2. **Missing Shadcn UI Dependencies**
The UI components require additional Radix UI dependencies. Install them as needed:
```bash
pnpm add @radix-ui/react-accordion @radix-ui/react-aspect-ratio @radix-ui/react-collapsible @radix-ui/react-context-menu @radix-ui/react-hover-card @radix-ui/react-menubar @radix-ui/react-navigation-menu @radix-ui/react-popover @radix-ui/react-progress @radix-ui/react-radio-group @radix-ui/react-scroll-area @radix-ui/react-select @radix-ui/react-slider @radix-ui/react-tabs @radix-ui/react-toggle @radix-ui/react-toggle-group @radix-ui/react-tooltip
```

#### 3. **TypeScript Path Resolution**
If you encounter path alias issues when running `tsc` directly, use Next.js build instead:
```bash
pnpm build
```

#### 4. **Prisma Client Generation**
If you get Prisma client errors:
```bash
pnpm prisma generate
```

### Environment Variables

Make sure all required environment variables are set in your `.env` file:

```env
# Database
DATABASE_URL="your-database-url"

# Authentication
AUTH_SECRET="your-auth-secret"
NEXT_PUBLIC_APP_URL="http://localhost:3000"

# OAuth Providers
GOOGLE_CLIENT_ID="your-google-client-id"
GOOGLE_CLIENT_SECRET="your-google-client-secret"
GITHUB_CLIENT_ID="your-github-client-id"
GITHUB_CLIENT_SECRET="your-github-client-secret"

# Email Service
RESEND_API_KEY="your-resend-api-key"
EMAIL_FROM="noreply@example.com" # optional in development; defaults to onboarding@resend.dev if omitted

# Two-Factor Authentication
TWO_FACTOR_ISSUER="AuthKit" # optional in development
```

Notes
- EMAIL_FROM and TWO_FACTOR_ISSUER are optional for local development to simplify setup. In production, set both explicitly.
- When EMAIL_FROM is not provided, the app uses the placeholder `onboarding@resend.dev`. Configure a verified sender in Resend and set EMAIL_FROM for production.
- To use SMTP locally (e.g., MailHog), set `MAIL_PROVIDER=SMTP` and configure `SMTP_HOST`, `SMTP_PORT`, `SMTP_SECURE`, `SMTP_USER`, and `SMTP_PASS`.
- Ensure all values use your deployment URL (e.g., APP_URL/NEXT_PUBLIC_APP_URL) with HTTPS in production.

## 🚀 Deployment

### Vercel (Recommended)

1. Push your code to GitHub
2. Connect your repository to Vercel
3. Add environment variables in Vercel dashboard
4. Deploy!

### Other Platforms

The application can be deployed to any platform that supports Next.js:
- Netlify
- Railway
- DigitalOcean App Platform
- AWS Amplify

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- [NextAuth.js](https://authjs.dev/) for the authentication framework
- [Shadcn UI](https://ui.shadcn.com/) for the beautiful components
- [Prisma](https://www.prisma.io/) for the database toolkit
