# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Development Commands

- **Start development server**: `npm run dev` (uses Turbopack for faster builds)
- **Build for production**: `npm run build` (also uses Turbopack)
- **Start production server**: `npm run start`
- **Lint code**: `npm run lint` (ESLint with Next.js config)

## Project Architecture

This is a Next.js 15 application using the App Router pattern with the following key characteristics:

### Framework Stack
- **Next.js 15** with App Router (src/app directory structure)
- **React 19** with TypeScript
- **Tailwind CSS 4** for styling
- **shadcn/ui** components with "new-york" style variant
- **Motion** for animations and gestures
- **Turbopack** for fast development and builds

### Project Structure
```
src/
├── app/                    # App Router pages and layouts
│   ├── layout.tsx         # Root layout with Geist font setup
│   ├── page.tsx           # Home page
│   └── globals.css        # Global Tailwind styles
├── components/
│   └── ui/                # shadcn/ui components
│       └── button.tsx     # Button component with CVA variants
└── lib/
    └── utils.ts           # Utility functions (cn class merger)
```

### Key Patterns

#### Component Architecture
- Uses **shadcn/ui** component library configured in `components.json`
- Components use **class-variance-authority (CVA)** for variant-based styling
- **CSS variables are disabled** in shadcn config (`cssVariables: false`)
- Utility function `cn()` merges classes using `clsx` and `tailwind-merge`

#### Styling
- Tailwind CSS 4 with custom design system
- Base color scheme uses "zinc" palette
- Components use extensive variant systems with hover/focus states
- Dark mode support built into component variants

#### TypeScript Configuration
- Path aliases configured: `@/*` maps to `./src/*`
- Strict TypeScript settings enabled
- Next.js plugin integrated for optimal type checking

#### Development Setup
- Uses **Geist** font family (sans and mono variants)
- ESLint configured with Next.js recommended rules
- PostCSS with Tailwind CSS integration

### Component Development
When creating new components:
1. Follow the shadcn/ui pattern with CVA for variants
2. Use the `cn()` utility for conditional classes
3. Import from aliased paths (`@/components`, `@/lib`)
4. Implement proper TypeScript interfaces
5. Follow the existing variant naming conventions (default, secondary, destructive, etc.)

### Icon Library
Uses **Lucide React** for icons (configured in shadcn setup).

### Animation Library
Uses **Motion** (formerly Framer Motion) for animations and gestures. When adding animations:
- Import from `motion` package
- Use motion components for animated elements
- Leverage motion's gesture handlers and layout animations