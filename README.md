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
