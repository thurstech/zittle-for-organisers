# Pages that sell

How to write and dress a Zittle website and its events so they get found and booked. Draft from what the business tells you, show it, and save only after they agree. Every claim on a page must be true for this business: never invent reviews, numbers, awards or inclusions. The longer versions of this advice are on the Zittle blog (`https://zittle.in/blog/`), named in brackets; link the business to them.

## What search engines and link previews read

- **Home page**: its title is the website **title**, its description in search results is the website **description** (roughly the first 150 characters show), and a shared link shows the first **landing image**.
- **Event page**: its title is _event title – venue – city_, its description is the event's **overview** (again, the first 150 or so characters show; a city's page starts it with _event in city:_), and a shared link shows the event's first **photo**.
- **An event's web address comes from its title** when `create-event` or `duplicate-event` makes it, and the connector can't change it. Get the title right before creating.
- **Place pages**: each place's description and image from `save-place`.
- **Reviews** feed the star rating search engines can show next to the business.
- Every storefront has a sitemap at `https://<website address>/sitemap.xml`.

## Event titles

Say what guests do and who it's for, in a few words. Clever names can come later (`write-workshop-description`).

- **Vague:** _Earth & Fire Experience_. **Clear:** _Wheel Throwing Workshop for Beginners_.
- Put the level, age group or format in the title when the business runs more than one version: _Kids Pottery Camp (Ages 8–12)_, _Couples Pottery Date Night_.
- Use the words guests search for (pottery class, wheel throwing, glaze painting), not only the studio's own names for things. The venue and city are added to the page title already; don't repeat them.

## Overview (up to 2,000 characters)

The first two lines matter most: they are the search snippet and what most visitors read. Lead with what guests do and what they take home, then follow this shape (`write-workshop-description`):

> **[What you'll do], [for whom]**
>
> [Two lines: what guests do and what they take home.]
>
> **Who it's for:** [experience level, age, group size]
>
> **What's included:** [materials, food, take-home items]
>
> **Good to know:** [duration, what to wear, where to arrive, cancellation in one line]

Write like the owner talks: short sentences, plain words, _you'll_ rather than _participants will_. Ask the business for anything you don't know (duration, what's included, what to bring) rather than guessing.

## Highlight and FAQs

- **Highlight** (up to 500 characters, shown on the event's card): one or two lines with the best part, such as _Make your own mug on the wheel. Clay, glazing and firing included._
- **FAQs**: the practical questions that otherwise stop a booking: experience needed, what to wear, how long it lasts, parking or metro, when pieces are ready, age limits, what if they're late. Three to six real ones beat ten generic ones.

## The website

- **Title**: the business's name. **Description** (up to 500 characters): what the business offers, where, and for whom, in the first sentence, such as _Hands-on pottery workshops in Madhapur, Hyderabad: wheel throwing, glaze painting and kids' classes._
- **Categories** and **sections**: name them as guests would (_Pottery classes_, _Kids' workshops_), since they are headings on the home page. One category per kind of event.
- **About**: who runs it, since when, what makes a session there good, with photos of the space and the people. This is where trust comes from.
- **Website FAQs**: questions about the business as a whole (gift vouchers, private group bookings, parking, accessibility).
- **Template**: V1 (the default) or V2, which adds a stats band and a WhatsApp chat button to the homepage. The business can switch either way at any time, and its content carries over; on V2, set `stats` too.
- **Stats** (Template V2 only; V1 never shows them): real figures only, such as years teaching, guests taught or pieces fired. Give each default as the number alone (120, 4.8): the website adds the + after the counts and the ★ after the rating. Live counts (`showDynamicStats`) count bookings on Zittle, so leave them off for a new business until the numbers are worth showing.
- **Social links**: Instagram, WhatsApp and the Google Business Profile at least. A profile on Google Maps is free and sends bookings (`get-workshop-on-google-maps`).

## Photos and look

- **Real photos of real sessions**: hands at work, finished pieces, the room, guests enjoying it. Stock photos make a page feel like an ad. The first photo of an event is its cover and its link preview: use the most striking one.
- **Event photos**: up to 4. **Landing images**: up to 5, wide (landscape) photos that read at a glance, since the title sits on top of them. **Logo**: square works best, as it is also the browser and home-screen icon.
- You can't see the website. After a visual change, ask the business to open the storefront on their phone and tell you what looks off.

## Colours

The website has four, set with `update-website` `colors`. Where each shows:

| Colour        | Where guests see it                                                                                                    |
| ------------- | ---------------------------------------------------------------------------------------------------------------------- |
| `primary`     | The header and every button (Book Now), and also the text colour of links, prices and selected dates on the white page |
| `onPrimary`   | Text and icons on the primary colour (white when unset)                                                                |
| `secondary`   | Template V2's hero band, stats card and reviews card, and some secondary buttons                                       |
| `onSecondary` | Text on the secondary colour (white when unset)                                                                        |

How to choose:

1. **Primary from the brand**: the main colour of the logo, the studio's signage or its Instagram. Because it is also a text colour on white, it must be a mid-to-dark shade. Pastels and bright yellows, limes and light pinks wash out as text: use a deeper shade of the same hue (terracotta rather than peach, forest green rather than mint).
2. **onPrimary**: white on a mid or dark primary; near-black (`#171717`) on a light one.
3. **Secondary**: a dark, calm colour that lets white text stand out, such as a deep shade of the primary's hue, charcoal (`#1F2937`) or navy. Avoid a second loud colour competing with the buttons.
4. **onSecondary**: white on a dark secondary.
5. **Check the result**: `get-website` and `update-website` return `colorWarnings` for any pair under the 4.5:1 contrast that reads easily (the international accessibility standard). Don't leave one standing: offer a darker or lighter shade of the same hue, and explain it in plain words ("the gold is too pale to read as text on white, so the prices would be hard to see").
6. **Don't** use pure neon colours, or make primary and secondary the same colour, or near enough that buttons disappear into the hero band.

If the business has no brand colours yet, offer two or three palettes that suit what they do (warm earth tones for pottery, deep greens for wellness, a bold jewel tone for dance), each passing the checks above, and let them pick.

## Bookings come from a full calendar

- **An event with nothing to book gets no bookings.** Keep sessions at least 8 weeks ahead. For a regular class, add a repeating schedule for the season at once (`run-a-weekly-workshop`). `check-launch-readiness` shows each event's sessions in the next 4 weeks and the 4 after.
- **Packages**: offer the ways people come (single, couple, group of four) rather than one flat price (`how-to-price-a-workshop`).
- **Coupons**: a first-booking or early-bird coupon with a real deadline helps a new event fill (`early-bird-pricing-workshops`). Offer it; create it only after a yes.
- **Deposits and a clear cancellation policy** cut no-shows (`reduce-workshop-no-shows`, `workshop-deposits-partial-payments`).
- **Reviews**: ask guests the same day, while it's fresh (`get-more-workshop-reviews`).

## After launch: where guests come from

The connector can't post or message for the business. Give them the storefront and event links and point them to:

- **Instagram** bio, posts and stories, with the link everywhere (`sell-event-tickets-on-instagram`).
- **WhatsApp** groups, broadcast lists and Status (`promote-workshop-on-whatsapp`; message templates in `workshop-announcement-message-templates`).
- **Google**: the Google Business Profile with the website link, and Google Search Console with the sitemap above submitted, so new events are found sooner.
- **Campaign links** (dashboard) to see which posts bring bookings.
