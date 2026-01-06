# BNP Technologies & Solutions

## Overview

This is a corporate website for BNP Technologies & Solutions, a banking infrastructure and technology provider. The application is a full-stack TypeScript project with a React frontend and Express backend, featuring a contact form that stores inquiries in a PostgreSQL database.

## User Preferences

Preferred communication style: Simple, everyday language.

## System Architecture

### Frontend Architecture
- **Framework**: React 18 with TypeScript
- **Routing**: Wouter for lightweight client-side routing
- **Styling**: Tailwind CSS with custom design system (Inter + Outfit fonts, professional blue color palette)
- **UI Components**: shadcn/ui component library built on Radix UI primitives
- **State Management**: TanStack Query (React Query) for server state
- **Forms**: React Hook Form with Zod validation
- **Animations**: Framer Motion for page transitions and scroll animations
- **Build Tool**: Vite with path aliases (`@/` for client/src, `@shared/` for shared code)

### Backend Architecture
- **Framework**: Express.js with TypeScript
- **Database**: PostgreSQL with Drizzle ORM
- **Schema Location**: `shared/schema.ts` contains all database table definitions
- **API Routes**: Defined in `shared/routes.ts` with Zod schemas for type-safe validation
- **Storage Pattern**: Repository pattern via `server/storage.ts` abstracting database operations

### Project Structure
```
├── client/           # React frontend
│   └── src/
│       ├── components/   # UI components (shadcn + custom)
│       ├── hooks/        # Custom React hooks
│       ├── lib/          # Utilities (queryClient, utils)
│       └── pages/        # Page components
├── server/           # Express backend
│   ├── db.ts         # Database connection
│   ├── routes.ts     # API route handlers
│   ├── storage.ts    # Data access layer
│   └── vite.ts       # Vite dev server integration
├── shared/           # Shared code between client/server
│   ├── schema.ts     # Drizzle database schema
│   └── routes.ts     # API route definitions with Zod schemas
└── migrations/       # Drizzle database migrations
```

### Development vs Production
- **Development**: Uses Vite dev server with HMR via `server/vite.ts`
- **Production**: Builds client with Vite, bundles server with esbuild, serves static files via `server/static.ts`

### Database Schema
Currently has one table:
- `contact_inquiries`: Stores contact form submissions (id, name, email, message, createdAt)

Use `npm run db:push` to sync schema changes to the database.

## External Dependencies

### Database
- **PostgreSQL**: Primary database, connection via `DATABASE_URL` environment variable
- **Drizzle ORM**: Type-safe database queries and schema management
- **connect-pg-simple**: Session storage (available but not currently in use)

### Frontend Libraries
- **Radix UI**: Accessible component primitives (dialogs, dropdowns, forms, etc.)
- **TanStack Query**: Server state management and caching
- **Framer Motion**: Animation library
- **Lucide React**: Icon library

### Build & Development
- **Vite**: Frontend build tool with React plugin
- **esbuild**: Server bundling for production
- **Drizzle Kit**: Database migration tooling

### Replit-Specific
- `@replit/vite-plugin-runtime-error-modal`: Error overlay in development
- `@replit/vite-plugin-cartographer`: Development tooling
- `@replit/vite-plugin-dev-banner`: Development banner