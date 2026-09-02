# HEATHEN: System Architecture & Workflow Roadmap

## 1. Technology Stack
*   **Frontend:** Next.js (App Router), React, TypeScript.
*   **Styling:** Tailwind CSS + custom CSS for complex turntable/spin animations.
*   **State Management:** Zustand (for Cart, Wishlist, and Audio/Turntable state).
*   **Backend & Database:** Supabase (PostgreSQL, Authentication, Storage).
*   **Payments:** Stripe (Checkout Sessions, Webhooks).
*   **Deployment:** Vercel.

## 2. Sandbox / Proof of Concept (PoC) Bypass
If this project is being built strictly for portfolio display or local learning, apply the following bypasses:
*   **Skip Phase 4 (Auth):** Rely entirely on `localStorage` to manage cart/wishlist state.
*   **Skip Phase 5 (Payments):** Do not integrate Stripe. Wire the checkout button to simply clear the cart state and trigger a "Payment Successful" toast.
*   **Skip Phase 6 (Deployment):** Run the project locally via `npm run dev` rather than deploying to Vercel.
*   **Supabase Free Tier Note:** Free Supabase projects automatically pause after 7 days without a database request. This preserves your data but will cause your local app to fail to load products. When this happens, simply log into the Supabase dashboard and manually click "Restore project" before you start coding. 

## 3. Database Schema (Supabase)
### `products`
*   `id` (SERIAL, primary key)
*   `slug` (TEXT, unique - human-readable URL identifier)
*   `title` (TEXT, required)
*   `cat` (TEXT, required - product category)
*   `price` (INTEGER, required - amount in cents or base units)
*   `color` (TEXT - primary color tag)
*   `fabric` (TEXT)
*   `fit` (TEXT)
*   `colorway` (TEXT)
*   `track` (TEXT - SKU equivalent / album track number)
*   `year` (INTEGER)
*   `img` (TEXT - image path / URL)
*   `desc` (TEXT - product description)
*   `liner` (TEXT - liner notes text)
*   `stock` (TEXT - inventory indicator)
*   `sizes` (TEXT[] - array of available size options, e.g. `['S', 'M', 'L']`)
*   `is_active` (BOOLEAN, default: `true` - visibility toggle)
*   `created_at` (TIMESTAMPTZ, default: `NOW()`)
*   `updated_at` (TIMESTAMPTZ, default: `NOW()`)

### `users` (Managed via Supabase Auth - *Skip for PoC*)
*   `id` (UUID, primary key)
*   `email` (TEXT)
*   `created_at` (TIMESTAMPTZ)

### `orders` (*Skip for PoC*)
*   `id` (UUID, primary key)
*   `user_id` (UUID, foreign key referencing users.id)
*   `total_amount` (NUMERIC)
*   `stripe_session_id` (TEXT)
*   `status` (TEXT - e.g., 'pending', 'paid', 'shipped')
*   `created_at` (TIMESTAMPTZ)

## 4. Phased Implementation Plan

### Phase 1: Component Deconstruction (UI Foundation)
**Goal:** Translate the monolithic `index.html` into a static Next.js component tree using dummy data.
*   Configure Tailwind with the custom HEATHEN color palette and Google Fonts.
*   Build the persistent `Layout` component (Ticker, Sticky Nav, Cart Drawer UI).
*   Rebuild the interactive Turntable logic using React state and CSS modules/Tailwind for the `@keyframes` spin.
*   Construct the Crate component with horizontal drag-to-scroll functionality.
*   Create the Library hover-flip animations using Tailwind group-hover and 3D transforms.

### Phase 2: Global State & Interactivity
**Goal:** Make the frontend fully interactive without a backend.
*   Implement Zustand store for `cartStore` and `wishlistStore`.
*   Ensure state persists to `localStorage`.
*   Wire up the Add to Cart/Wishlist buttons to update the live badge counts in the Nav.
*   Build the dynamic Product Page UI (`/product/[slug]`) that accepts URL parameters and renders the spinning garment animation.

### Phase 3: Backend Integration (Supabase)
**Goal:** Replace hardcoded arrays with a live database.
*   Initialize the Supabase project and execute the SQL `CREATE TABLE products` migration.
*   Seed product records matching all columns.
*   Upload uncompressed product assets to Supabase Storage.
*   Write Next.js Server Components to fetch product data on the server.
*   Update the Crate, Shop All, and Product pages to consume live Supabase queries filtered by `is_active = true`.

### Phase 4: Authentication & User Accounts *(Optional)*
*   Implement Supabase Auth UI for Email/Password login.
*   Create a protected `/account` route.
*   Migrate guest `localStorage` wishlists to the user's database profile upon login.

### Phase 5: Checkout & Payments *(Optional)*
*   Set up Stripe Products and Prices matching the Supabase database.
*   Create a Next.js API Route (`/api/checkout`) to generate a Stripe Checkout Session.
*   Set up a Stripe Webhook endpoint to listen for `checkout.session.completed`.

### Phase 6: Final Polish & Deployment *(Optional)*
*   Connect the GitHub repository to Vercel.
*   Add all production environment variables to Vercel.