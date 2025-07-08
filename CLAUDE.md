# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Development Commands

- `pnpm dev` - Start development server with HMR at http://localhost:5173
- `pnpm build` - Create production build
- `pnpm start` - Start production server from build
- `pnpm typecheck` - Run TypeScript type checking (generates types and runs tsc)
- `pnpm prettier --write .` - Format all files with Prettier
- `pnpm prettier --check .` - Check if files are formatted

## Architecture Overview

This is a React Router v7 application with server-side rendering enabled by default. The project uses:

- **React Router v7** - File-based routing with SSR
- **TypeScript** - Strict type checking enabled
- **Vite** - Build tool and dev server
- **Tailwind CSS** - Styling framework
- **pnpm** - Package manager
- **Prettier** - Code formatting with import organization and Tailwind class sorting

### Key Files and Structure

- `app/root.tsx` - Root layout component with error boundary
- `app/routes.ts` - Route configuration using React Router's file-based routing
- `app/routes/` - Route components
- `react-router.config.ts` - React Router configuration (SSR enabled)
- `vite.config.ts` - Vite configuration with React Router, Tailwind, and TypeScript paths
- `tsconfig.json` - TypeScript configuration with path aliases (`~/*` maps to `./app/*`)
- `.prettierrc` - Prettier configuration with import organization and Tailwind plugin

### Route System

Routes are configured in `app/routes.ts` using React Router's programmatic route configuration. Each route component should:
- Export a `meta` function for page metadata
- Use the `Route` types from `+types/[route-name]` for type safety
- Follow the established pattern in `app/routes/home.tsx`

### Styling

The project uses Tailwind CSS v4 with Vite integration. Global styles are in `app/app.css`. Components use Tailwind utility classes.

### Build and Deployment

The application builds to a `build/` directory with:
- `build/client/` - Static assets
- `build/server/` - Server-side code

Docker deployment is configured with multi-stage builds optimized for production.