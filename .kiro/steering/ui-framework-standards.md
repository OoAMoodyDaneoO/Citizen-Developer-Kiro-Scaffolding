---
name: UI Framework & Component Standards
description: Approved frontend stack (React, Tailwind, shadcn/ui), component patterns, accessibility requirements, responsive design rules, and forbidden patterns.
inclusion: always
---

# UI Framework & Component Standards

## Approved Technology Stack

When building front-end applications, use the following approved stack:

- **Framework**: React 18+ with TypeScript (preferred) or Next.js 14+
- **Styling**: Tailwind CSS 3+ or CSS Modules — no inline styles for production components
- **Component Library**: shadcn/ui (preferred), Radix UI primitives, or AWS Amplify UI
- **Icons**: Lucide React or Heroicons
- **Forms**: React Hook Form with Zod validation
- **State Management**: React Context for simple state, Zustand for complex state
- **HTTP Client**: Native fetch API or AWS Amplify API module

## Component Patterns

- All components must be functional components with TypeScript interfaces for props
- Use semantic HTML elements (`<nav>`, `<main>`, `<article>`, `<button>`) — not `<div>` for everything
- Every interactive element must have visible focus indicators
- Every `<img>` must have a meaningful `alt` attribute
- Forms must have associated `<label>` elements for every input
- Error states must be communicated visually AND via `aria-live` regions
- Loading states must use appropriate `aria-busy` attributes
- Color must not be the only means of conveying information

## Accessibility Requirements

- All pages must have a single `<h1>` and logical heading hierarchy
- Interactive elements must be keyboard navigable (Tab, Enter, Escape, Arrow keys)
- Minimum color contrast ratio of 4.5:1 for normal text, 3:1 for large text
- Touch targets must be at least 44x44 pixels on mobile
- Skip navigation links for pages with repeated navigation
- All modals must trap focus and return focus on close

## Responsive Design

- Mobile-first approach — design for 320px minimum width
- Use Tailwind breakpoints: `sm` (640px), `md` (768px), `lg` (1024px), `xl` (1280px)
- Test layouts at common breakpoints — no horizontal scrolling
- Images must be responsive with appropriate `srcset` or Next.js `Image` component

## Forbidden Patterns

- No `any` type in TypeScript — use proper typing
- No `// @ts-ignore` or `// eslint-disable` without documented justification
- No direct DOM manipulation — use React refs when necessary
- No `localStorage` for sensitive data — use secure cookies or server-side sessions
- No third-party analytics or tracking scripts without explicit approval
