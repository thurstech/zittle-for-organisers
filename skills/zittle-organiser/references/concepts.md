# Zittle concepts

How Zittle works, for explaining it to an organiser and choosing the right tool. Drawn from the Zittle docs at `https://zittle.in/docs/`; link the business to the page named in brackets for the full picture.

## Events, places, venues and packages

- **Event**: what guests book, such as _Wheel Throwing Workshop_. It has a title, an overview, a one-line highlight, 1–4 photos (the first is the cover), 1–4 category tags, an age range and optional FAQs. (`getting-started/create-event/`)
- **Place** (the dashboard's _Venues_ page): a physical location the business keeps once: name, address, city, a Google Maps link, and an optional description and image for its page on the website. Editing a place changes it for every event there. (`running-events/more-venues/`)
- **Venue of an event**: an event running at one place, with its own contact number and packages. One event can run at many places, even in different cities; guests pick a city on the website. (`getting-started/add-venue/`)
- **Package**: a ticket guests can buy at a venue, such as _Single seat_ ₹1,800 or _Couple_ ₹3,400. Each has a price, an optional discount (0–100%), an optional deposit, and a number of tickets. Every venue has at least one. (`getting-started/add-packages/`)
- **Ticket type** (the dashboard's _saved packages_): a package saved once, with its name and how many people one ticket admits, and picked on every venue that sells it. Prices are set per venue. Bulk price changes find packages by their ticket type, so a package not linked to one is left out of them. A ticket type can't be edited or deleted. (`running-events/saved-packages/`)
- **How seats are counted** (fixed per venue when it is added):
  - **Per package**: each package has its own number of tickets per session.
  - **Per session** (_Shared across packages_): one seat total per session, set when sessions are added; each ticket uses as many seats as its ticket type admits (a _Couple_ uses 2).

## Sessions

- A **session** (the dashboard's _slot_) is a date and time guests book. One-off sessions, or a **repeating schedule** (daily, weekly or monthly, for up to 12 months). Once a repeating schedule is added, its dates and times can't be edited, only its prices and seats. (`getting-started/add-dates/`)
- Bulk changes add sessions, change prices or seats, or pause and resume, across many events, venues and dates at once; one change creates or edits at most 2,000 sessions. (`running-events/bulk-changes/`)
- **Pause** stops new bookings (some dates, or a venue as a whole); guests who booked keep their places, and it can be resumed. **Cancel** calls a session off and refunds every guest: dashboard only. (`running-events/pause-or-cancel/`)

## Money

- **Platform fee**, on every online booking, on what the guest pays online (after discounts and coupons): 5% for Indian phone numbers (3% convenience + 2% transaction), 7% for others. By default guests pay it on top of the ticket price and the business keeps the full price. The business can choose to pay part or all of it instead (dashboard). Offline tickets have no fee. (`running-events/payments-and-payouts/`)
- **Deposit** (_partial payment_): part of the price paid online to book, as a fixed amount (less than the price after discount) or a percentage (under 100%); the rest is paid at the venue. The fee applies only to the deposit.
- **Payouts**: weekly. Every Monday, Zittle pays out the online payments received up to the previous Sunday to the business's bank account. Money paid at the venue never goes through payouts.
- **Held money**: online payments made while the business has no Zittle plan are held, not paid out, until it pays for that time (a Monthly plan per month, or Quarterly). If a month is left unpaid, Zittle takes a Monthly plan from the held money at the month's end and pays out the rest. Paying is dashboard only.
- **Coupons**: a code for a fixed amount or a percentage off (with an optional maximum), with an expiry, and optional limits: one event, a minimum order, a number of uses. (`running-events/coupons/`)

## Guest cancellations

Whether guests can cancel their own bookings is set in the cancellation rules: up to how many hours before the start, and the charge. (`getting-started/policies/`)

- **No charge** (`platform_fee_kept`): the guest gets back the ticket price they paid online; the platform fee they paid isn't refunded.
- **Full refund** (`full_refund`): everything, fee included; the business covers the fee from its payouts.
- **Keep your part of the fee** (`whole_platform_fee_kept`): if the business pays part of the fee, the guest doesn't get that part back either. Same as no charge when guests pay the whole fee.
- **A percentage by notice** (`percent`): up to 3 tiers of hours before the start and a share of the ticket price, such as 0% at 72+ hours, 25% from 24 hours, 50% with less notice. The fee isn't refunded either.

Only bookings paid online can be cancelled by guests. When the business cancels a booking or a session, it chooses the refund instead (dashboard).

## Website

- The website is at `name.zittle.in`, set once with the business details and never changed. A custom domain (`www.studio.com`) is set up by the Zittle team. (`getting-started/business-details/`)
- **Title** (the main heading), **description** (up to 500 characters), **landing images** (up to 5), **logo** (also the browser and home-screen icon, so square looks best), **colours** (primary and secondary, and the text colour on each: keep it readable), and the homepage button's text. (`getting-started/website-details/`)
- **Categories**, each with an image: the groups events are tagged with. **Sections** group categories under headings on the homepage: categories not placed in another section show in the first one, and a category is in at most one section.
- **About** sections (a title, a description, up to 4 images), **FAQs**, and **social links** (Instagram, Facebook, YouTube, LinkedIn, WhatsApp, Google Business).
- **Policies**: terms and conditions, privacy, and cancellation pages, each starting as Zittle's starter text for the business to review. The cancellation page follows the cancellation rules for as long as it holds the starter text; once the business writes its own, it must keep it in step with the rules itself. (`getting-started/policies/`)
- **GST**: an optional GST certificate PDF, approved by the Zittle team.
