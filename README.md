# Meesho Wholesale — DICE prototype

An independent, mobile-first concept prototype inspired by the attached Meesho buyer-app screenshots. It is not an official Meesho product. Orders, accounts, notifications, refunds, fulfilment, supplier checks, and payment outcomes are demo data only; nothing is sent to Meesho or a payment provider.

## Run locally

```bash
npm install
npm run dev
```

Open [http://localhost:5173](http://localhost:5173). Demo credentials for either role: **Prototype / 1234**. To check a production build, run `npm run build`; to serve that build, run `npm run preview`.

All demo state is saved in this browser's `localStorage`. Use **About this concept demo → Reset demo data** (or the seller's **Demo account, reset & logout**) to restore the seed. Buyer and seller share the same local data.

## Three-to-five-minute judge walkthrough

1. Sign in as **Buyer**. On the Meesho-style home, tap **Meesho Wholesale** to see the three paths. Open **Buy Wholesale**, choose the cotton tote, and set 200 units in the quantity sheet. The unit price crosses to ₹72; continue through review and select **Simulate payment**.
2. Back at home, open **Demand Pools**. The first pool shows 320 interested, 140 paid, and a 200 paid-unit minimum. Register free interest, then pay for units separately. The seeded **Seller price offer · 187/200** scenario shows original-price units and the revised-price cohort as separate counters. Review the offer, pay at its revised terms, then switch to Seller to see the same cohorts. The simulator can close the window and show both cohorts refunded if either paid minimum is missed.
3. From the seller role, use the pool manager's **N−1 underfilled · 187/200** card to record **Accept 187 at original price**. For the buyer-consent alternative, load **Extension offered**, switch to Buyer, and explicitly choose **Extend for one week**. The closing date advances only after that choice.
4. As Buyer, open **BulkRequest**, post a uniquely named request, and switch to Seller → **Requests**. Open the request, prepare a structured quote, and send it. Switch back to Buyer, open the request, compare the quote, award the supplier, and complete the prepaid simulation. The awarded order appears in seller **Orders**.
5. In Buyer **My Orders**, report an issue for only a subset of units. Seller **Resolve issues** shows the claim and can agree to replace or refund the affected units. Pool failures and refund examples are available from the pool scenario menu.

## What works in the local prototype

- Mobile layouts at 390 × 844 and 430 × 932, with full-viewport screens on phones and a centered phone frame on desktop.
- Reusable React UI parts for top bars, search, bottom navigation, buttons, cards, price tiers, progress, forms, notices, sheets, sticky actions, timelines, and claim states.
- Buyer and seller login/role switching, home/catalogue search and category filtering, direct order quantity/stock/serviceability validation, itemised prepaid checkout, seller offers, and shared order tracking.
- Free pool interest, full-prepaid commitments, independent revised-price cohorts, explicit extension consent, early lock and capacity states, waitlist, cancellation, and simulated failed-pool refunds.
- Structured BulkRequest posting and validation, seller pass/quote, quote comparison and award, prepaid order simulation, and shared notifications.
- Partial-quantity issue reports, seller responses, seller-created listings and pools, optional buyer services, and live formula-based pilot metrics.
- Concept/demo explanation, seller 0% sales commission display, and reset controls.

Free essentials include wholesale browsing and delivered-cost comparison, Demand Pool interest, prepaid ordering, BulkRequests, basic quote comparison, order tracking, free basic seller identity verification, and seller tools with 0% sales commission. Optional buyer services are enhanced supplier diligence, quote-scoped Specification & Sample Review under a pilot 2x-unit-price rule with same-supplier/spec order credit, and managed sourcing priced after scope. Prices and uptake are illustrative assumptions, not validated willingness to pay. Optional seller-paid Sponsored ads are a potential Wholesale pilot hypothesis; no placements or ad revenue are simulated. Existing Meesho advertising is separate from that hypothesis. Organic quote comparisons are never sponsored.

The browser performs all state changes locally. There is no real authentication, contact verification, SMS, payment processor, banking access, inventory feed, logistics, return pickup, supplier diligence, or refund settlement. The evidence-photo control is a placeholder. Identity checks, reliability figures, suppliers, orders, messages, payments, service outcomes, and sample refunds/replacements are simulated demo data. A simulated completed transaction is not Meesho revenue; separately simulated optional buyer-service payments are tracked apart from order value. Sample-review payments are credited against eligible orders and are not counted again as service revenue.

## UI system

Primary frame target: 390 × 844; checked at 430 × 932. The styles in `src/styles.css` define the reusable color, type, spacing, radius, divider, and shadow tokens. The interface uses white surfaces, restrained lilac/pink fills, magenta actions, charcoal text, muted gray secondary copy, and green paid/savings states. Product photos are bundled under `public/assets/`; CSS/React components are editable source code and retain local illustration fallbacks.

The main route groups are Welcome/Login; Buyer Home/Wholesale Hub/Catalogue/Product/Offers; Review/Payment/Confirmation; Demand Pools/My Buckets/Pool Decision; BulkRequest/Form/Quotes/Award; Notifications/My Orders/Issue; and Seller Overview/Listings/Pools/Requests/Orders/Issue Resolution. The scenario controller exposes open, underfilled, revised-price, successful, early-lock, capacity, extension, and failed/refund pool cases.

## Figma handoff status

No Figma file was created in this session. The connected tool inventory contained no Figma MCP tools, so this environment could not create a design file, write native Figma components/styles/Auto Layout, or capture the live interface as editable layers. Screenshots, PNGs, and SVG uploads would not meet the requested editable design deliverable.

Once the remote Figma MCP plugin is connected in Codex, this running app can be captured into **Meesho Wholesale — DICE Prototype** as editable frames, followed by native UI-kit components and prototype links. Figma's current Codex setup is: Codex app → **Plugins** → **+** beside Figma → **Install Figma** → authenticate and allow Figma access; then restart Codex if the tools do not load. The remote server is required for `generate_figma_design` code-to-canvas capture. See [Figma’s Codex setup steps](https://help.figma.com/hc/en-us/articles/39888629089175-Codex-and-Figma-Set-up-the-MCP-server) and [code-to-canvas workflow](https://developers.figma.com/docs/figma-mcp-server/code-to-canvas/).

The planned Figma page structure is **References**, **UI Kit**, **Buyer — Wholesale**, **Buyer — Demand Pools**, **Buyer — BulkRequest**, **Seller**, and **Demo Journeys**. The capture map includes role/login; home, hub, catalogue, product, offers and quantity sheet; review/payment/confirmation/tracking; pool interest/paid choice, buckets/transfer consent, 187/200 seller decisions, extension/reprice, lock/capacity/failure/refunds; RFQ validation/quotes/award; seller listing, fulfilment and issue resolution. These are handoff plans only; they are not Figma pages or clickable links yet.
