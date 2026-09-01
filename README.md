<<<<<<< HEAD
This is a [Next.js](https://nextjs.org) project bootstrapped with [`create-next-app`](https://nextjs.org/docs/app/api-reference/cli/create-next-app).

## Getting Started

First, run the development server:

```bash
npm run dev
# or
yarn dev
# or
pnpm dev
# or
bun dev
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

You can start editing the page by modifying `app/page.tsx`. The page auto-updates as you edit the file.

This project uses [`next/font`](https://nextjs.org/docs/app/building-your-application/optimizing/fonts) to automatically optimize and load [Geist](https://vercel.com/font), a new font family for Vercel.

## Learn More

To learn more about Next.js, take a look at the following resources:

- [Next.js Documentation](https://nextjs.org/docs) - learn about Next.js features and API.
- [Learn Next.js](https://nextjs.org/learn) - an interactive Next.js tutorial.

You can check out [the Next.js GitHub repository](https://github.com/vercel/next.js) - your feedback and contributions are welcome!

## Deploy on Vercel

The easiest way to deploy your Next.js app is to use the [Vercel Platform](https://vercel.com/new?utm_medium=default-template&filter=next.js&utm_source=create-next-app&utm_campaign=create-next-app-readme) from the creators of Next.js.

Check out our [Next.js deployment documentation](https://nextjs.org/docs/app/building-your-application/deploying) for more details.
=======
# heathen-store
A vintage vinyl-record-crate aesthetic fashion e-commerce site built with Next.js, React, and Supabase. Features interactive turntables, drag-to-scroll crates, infinite record conveyors, and liner-note product details.
# HEATHEN (WIP) — Vintage Fashion & Vinyl E-Commerce

## The Concept
A conceptual e-commerce platform blending vintage fashion with the tactile experience of a physical record store. The UI treats garments as vinyl records, featuring crate-digging mechanics, interactive turntables, liner-note product descriptions, and track numbers instead of SKUs.

## The Aesthetic
*   **Vibe:** Raw denim, worn leather, faded cotton, analogue warmth.
*   **Interactions:** Drag-to-scroll physical crates, dropping the tonearm to spin records, auto-scrolling infinite conveyors, and record sleeves that slide open to reveal garments.
*   **Typography:** Playfair Display, Bebas Neue, Special Elite, IBM Plex Mono.

## Tech Stack Evolution
**Phase 1: Prototype (Completed)**
*   Single-file monolithic `index.html`.
*   Vanilla JavaScript DOM manipulation.
*   Bespoke CSS animations (`@keyframes` for vinyl spinning, synthetic tonearm physics).
*   `localStorage` for Cart and Wishlist persistence.

**Phase 2: Production Build (In Progress)**
*   **Frontend:** Next.js (App Router, React 18+).
*   **State Management:** Zustand (for complex Cart/Wishlist/Audio states).
*   **Backend/Database:** Supabase (Postgres) for product inventory, user profiles, and order management.
*   **Authentication:** Supabase Auth.
*   **Payments:** Stripe Checkout.

## Roadmap
1.  **Componentization:** Break the vanilla HTML/CSS into reusable React components while strictly preserving the custom CSS variables and animation logic.
2.  **Database Migration:** Move the hardcoded JS product array into a Postgres schema.
3.  **Global State:** Replace `localStorage` with a robust Zustand store tied to the user's database session.
4.  **Checkout Integration:** Wire the frontend cart to a Next.js Server Action generating a Stripe Checkout session.
>>>>>>> 4e936b234ecd06198dc9d77f8ae0a7f0c1c3879f
