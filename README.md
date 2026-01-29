# Payload Auth

The [Better Auth](https://www.better-auth.com) plugin for [Payload CMS](https://payloadcms.com).

This plugin deeply integrates Better Auth into Payload, allowing you to use Better Auth as your single source of truth for authentication across your database, admin panel, and frontend application.

## Features

- 🔐 **Single Auth Source**: Replaces or enhances standard Payload auth with Better Auth.
- 🗄️ **Automatic Schema**: Injects `users`, `sessions`, `accounts`, and `verifications` collections automatically.
- 💻 **Admin UI Integration**: Replaces the Payload login screen with your Better Auth flow.
- 🚀 **Full Control**: Configure every aspect of the users collection and admin access.
- 📦 **Monorepo Ready**: Designed to work with modern Next.js + Payload setups.

## Installation

```bash
pnpm add payload-auth
```

> **Note**: Requires Next.js 16.1+ and Payload 3.0+.

## Quick Start

In your `payload.config.ts`:

```typescript
import { buildConfig } from 'payload/config'
import { betterAuthPlugin } from 'payload-auth'

export default buildConfig({
  // ...
  plugins: [
    betterAuthPlugin({
      betterAuthOptions: {
        // Your Better Auth config
        secret: process.env.BETTER_AUTH_SECRET,
      },
      // Disable default Payload auth to let Better Auth handle everything
      disableDefaultPayloadAuth: true, 
      users: {
        slug: 'users',
        adminRoles: ['admin'],
        defaultRole: 'user',
      },
      admin: {
          loginMethods: ['github', 'emailPassword']
      }
    }),
  ],
})
```

## License

MIT
