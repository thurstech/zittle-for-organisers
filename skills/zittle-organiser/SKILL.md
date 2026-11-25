---
name: zittle-organiser
description: Run a Zittle business (events and workshops on zittle.in) through the Zittle for Organisers connector — set up a new business and its website, launch events, add sessions, change prices and seats, and check bookings, sales and enquiries. Use whenever the user manages their Zittle business, or asks about their events, sessions, bookings, payouts, website or policies on Zittle.
---

# Running a Zittle business

The user is an organiser: a studio, teacher or host who sells workshops and events on their own Zittle booking website. The Zittle for Organisers connector acts as their business. Everything it changes is live on their website, so work like a careful assistant with the keys to their shop.

Zittle works only for businesses in India for now. If the user's business is elsewhere, say so before they sign up, and point them to the waitlist at https://zittle.in/waitlist, where they're emailed when Zittle opens in their country.

For what Zittle's terms mean (places, packages, ticket types, seats, fees, payouts, policies), read [references/concepts.md](references/concepts.md) before explaining them or making a change that depends on them.

For anything guests read or see (titles, descriptions, overviews, highlights, FAQs, photos, colours) and for getting more bookings, read [references/selling.md](references/selling.md) first. A working website isn't the goal; one that gets found and booked is.

## Always

1. **Start with `get-business-overview`.** It gives today's date and the business's timezone; every date and time in the tools is in that timezone. Say dates the way the business does ("Sat 6 Mar, 11:00").
2. **Never invent anything.** Ids, image keys, prices, seat counts and booking details come from a tool. If a tool fails, say what failed; don't fill the gap with a guess.
3. **Say what will change, then wait for a yes** before any tool that changes something. Name the event, venue, dates and the before and after ("Single seat ₹900 → ₹1,000 at Clay Studio Madhapur, all dates").
4. **Read, then write.** Edits take the `version` from the read tool (`get-event`, `list-places`, `get-website`, `get-policy`, `manage-event-photos`). If an edit is refused as stale, read again, rebuild the change from what is there now, and confirm again if it differs.
5. **Sessions, prices, seats and pausing go through the preview.** Call `preview-bulk-change`, show the business what it will do, and call `apply-bulk-change` with the same arguments and its `previewToken` only after they agree. Never apply twice.
6. **Files come from the business's device.** When something needs an image or a PDF that isn't on Zittle yet, open `upload-files` with the right purpose and wait: the business's next message gives the keys. If no upload area appears for them, say so, and offer what works without it (for an event's photos, `create-event` with `photosFrom`).

## Ask twice before these

These can't be undone. Repeat the exact value back and get an explicit yes:

- **The website address** (`update-business-details` `websiteAddress`): `name.zittle.in` is set once and never changes.
- **A ticket type** (`create-ticket-type`): it can never be edited or deleted. Check the name and how many people one ticket admits.
- **How a venue counts seats** (`add-event-venue` `seatsCounted`): per package, or one total per session shared by all packages. It can't be changed for that venue later.
- **Repeating sessions**: once added, a repeating schedule's dates, times and frequency can't be edited, only its prices and seats. Check the first date, last date, days and times.
- **An event's title when it is created** (`create-event`, `duplicate-event`): it sets the event's web address, which can't change later.
- **Deleting a package** (`delete-event-package`) or **removing a category** from the website.

## Set up a new business

When the business is new (no events, no website address), walk through this in order, one step at a time:

1. **Business details** (`update-business-details`): business name, display name if different, address and city. Then the website address: suggest one from the name, confirm it (see above), set it.
2. **Website** (`get-website`, then `update-website`): a title and a short description (up to 500 characters), at least one category with an image (events are tagged with categories; upload with purpose `category_images`) and a heading for them (`categoriesTitle`), at least one landing page section (`sections`; a title is enough), a logo (`logo`), a primary colour and the other brand colours (choose them with the selling guide's _Colours_ section, and fix any `colorWarnings`), and at least one landing image (`landing_images`). **Template**: a website is on Template V1 unless the business picked V2 (`get-website` `business.template`). V2 adds a stats band and a WhatsApp chat button to the homepage. The business can switch either way itself, here (`update-business-details` `template`) or in the dashboard, and its content carries over. Offer the stats band (`stats`: three figures such as workshops hosted, guest rating and happy guests, each with a title and a figure) only when the business is on V2 or wants to switch: switching to V2 means setting `stats` with `update-website`, and `missingForTemplate` lists them until then (the homepage just leaves the band out meanwhile). Offer to write the wording from what the business tells you about itself, following the selling guide, and ask for their Instagram, WhatsApp and Google Business Profile links. Offer an About section and website FAQs too. The storefront shows an error page until all of these are set, so this step isn't finished, and the website isn't ready to share, until `get-website` returns an empty `missingForStorefront`.
3. **Policies** (`get-policy` for `terms`, `privacy`, `cancellation`): pages not saved yet come back as Zittle's starter text. Show the business the gist, adjust anything that doesn't fit, and save each with `update-policy`.
4. **Cancellation rules** (`update-cancellation-rules`): whether guests can cancel their own bookings, how many hours before, and the charge. Explain the options from the concepts reference.
5. **Places** (`save-place`): each studio or venue, with its address, city and a Google Maps link. The city must be on Zittle's list. If `save-place` says it isn't, check whether it's listed under another name; if not, confirm the spelling (and state) with the business and send `request-city`. Zittle emails them when it's added. Carry on with the other steps and the event itself, and add this place once the city is there.
6. **Ticket types** (`create-ticket-type`): the kinds of ticket sold everywhere, such as Single seat or Couple (see above).
7. **The first event**: follow _Launch an event_ below.
8. **In the dashboard** (the connector can't): verify the business phone number on WhatsApp, add bank details so payouts can be made, and choose a plan before the current one ends. Link the pages listed under _Only in the dashboard_.
9. **Launch check** (`check-launch-readiness`): fix everything under `blocking` first; setup isn't done while it lists anything. Then go through its facts with the selling guide and offer, one at a time, to fix what's thin: short overviews, events without FAQs or with fewer than 3 photos, a calendar less than 8 weeks ahead, missing social links, policy pages still on starter text. Finish with the storefront link and the guide's _After launch_ list of where guests come from.

## Launch an event

1. **Like an existing one?** `duplicate-event` copies its text, photos, venues, packages and prices under a new title. Otherwise `create-event`: title, an overview (what happens, up to 2,000 characters), a one-line highlight (up to 500), 1–4 categories the website already has, an age range, FAQs, and photos (upload with purpose `event_photos`, up to 4, cover first). Draft the title, overview, highlight and FAQs with the selling guide and show them before creating: the title sets the event's web address for good.
2. **Where and what it sells** (`add-event-venue`): a place from `list-places`, the venue's contact number, how seats are counted (see above), and the packages: name, price, optional discount and deposit, and tickets per session (or seats per ticket). Link each package to a ticket type (`packageCatalogId`), or price changes across events can't find it later.
3. **When** (`preview-bulk-change` with `add_sessions`, then `apply-bulk-change`): one-off dates, or a repeating schedule. For a venue counting seats per session, give `ticketsPerSession`. Suggest at least 8 weeks of dates: guests can't book what isn't on the calendar.
4. **Check and share**: `check-launch-readiness` confirms nothing blocks bookings; `list-sessions` shows the dates with seats left; `get-event` gives the storefront link to share.

## Change the schedule or prices

- Everything across events, venues or dates goes through `preview-bulk-change`: add sessions, change prices by a set amount or a percentage, change seats, pause or resume (some dates, or whole venues).
- Target by city, plus event names, venue names or category tags. Use names exactly as `search-events` shows them.
- One venue's own package (rename it, change its deposit or tickets): `save-event-package`, with the version from `get-event`.
- A session that won't happen is **cancelled**, which refunds every guest. That is only in the dashboard. Pausing stops new bookings and keeps everyone's.

## A weekly check-in

When the business asks how things are going, gather and summarise in a few lines:

- `get-sales-summary`: sales, settled and pending, and the payout balance (explain any `held` amount: see the concepts reference).
- `list-sessions` for the coming week: sessions with few seats left, and sessions with none booked.
- `list-bookings` for the coming week, and `list-enquiries` and `list-reviews` for anything new.
- `check-launch-readiness`: anything blocking, and events with few or no sessions in the next 4 weeks or the 4 after.

End with one or two concrete suggestions (add dates where sessions sold out or the calendar runs short, pause or promote one that's empty, a coupon or a better overview for an event that isn't selling; see the selling guide), and make none of them without a yes.

## Customers

- Find a booking with `list-bookings` (by event, dates or the customer's phone number), then `get-booking` for its details. The platform fee shows what the customer paid and, if the business pays a share, what the business paid.
- `get-enquiry` gives a customer's phone and email so the business can reply. The connector can't message customers.
- Refunds and cancellations are dashboard-only.

## Only in the dashboard

The connector can't do these. Say so plainly and link the page (all under `https://zittle.in/docs/`):

| Task                                                                 | Page                                                                                                  |
| -------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------- |
| Cancel or refund a booking, refund more                              | `running-events/manage-bookings/`                                                                     |
| Cancel a session (refunds every guest)                               | `running-events/pause-or-cancel/`                                                                     |
| Record a booking paid at the venue                                   | `running-events/offline-tickets/`                                                                     |
| Bank details, payouts, who pays the platform fee                     | `getting-started/bank-details/`, `running-events/payments-and-payouts/`                               |
| The Zittle plan, renewal, paying for held months                     | `running-events/payments-and-payouts/`                                                                |
| The business phone number (WhatsApp-verified), login email, password | `getting-started/business-details/`                                                                   |
| A custom domain such as www.studio.com                               | `getting-started/website-details/`                                                                    |
| Instagram and WhatsApp chatbots, Google Calendar                     | `running-events/chatbots/`, `getting-started/integrations/`                                           |
| Waitlist, campaign links, customer list, replying to reviews         | `running-events/waitlist/`, `running-events/campaign-links/`, `running-events/reviews-and-customers/` |
