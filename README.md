# GivMoo homepage: 5-section concept

A concept mockup of a simpler GivMoo homepage, built by Veteran Vectors for Evan Parnell and Martiel Beatty after the 2026-09-28 call. It is a static page for review. It does not take orders: every button and link goes to the matching page on the live givmoo.com.

**Preview:** open `index.html` in a browser. No build step, no framework.

## Why 5 sections

On the call Evan said the live homepage runs about 17 phone screens because sections kept getting added and none were removed. He wants roughly five, and a page that reads "here's what we do, here's the offer, buy this thing."

Measured on this mockup (headless WebKit, fallback font): **about 5.7 phone screens at 390 x 844**, 3.9 screens at 1440 x 900.

| # | Section | Job |
|---|---|---|
| 1 | Hero | What GivMoo is in one line, one offer (free shipping over $50), one main button (Shop best sellers), one side door (For nonprofits), the three trust numbers |
| 2 | Best sellers + shop by cause | 8 real products with price and the nonprofit each one supports; the 11 nonprofit stores as a chip row |
| 3 | How it works | 3 steps: pick a product, choose your cause, the profits go to them |
| 4 | For nonprofits | Two doors side by side: open a store, or place a bulk order. The bulk door carries the Harvest of Savings offer |
| 5 | Proof, FAQ, newsletter | Two real customer reviews, 4 FAQs, the $5-off signup, then the footer |

## What was cut from the live homepage

Second H1 ("GivMoo" and "Every Small Purchase Has BIG Impact." are both H1s on the live page), Featured Favorites category tabs, the "Your shortcut to best sellers" carousel, "Favorite Finds Only On GivMoo", the Buy Now Pay Later banner (Afterpay, Klarna, Zip), the shipping banner, Smart Finds tiles, the full "Shop All Over 328 items" catalog with filters and 37 pages, the Live Shipping / Great Gifts / Quality Guarantee strip, Shop by Collection tiles, and three of the FAQs (size waitlist, gift wrapping, order tracking). All of it still exists one click away on /shop/ and the category pages.

## Sources (live site, read 2026-09-28)

| What | Source |
|---|---|
| Colors, font | `--gm-*` tokens in the live combined stylesheet (primary `#e84a1a`, dark `#c13a0e`, accent `#f4831e`, light `#fff4ee`, font Nunito Sans) |
| Logo, hero photo, favicon | `givmoo.com/wp-content/mu-plugins/givmoo-redesign/assets/img/logo.png`, `.../hero-shopping-bags.png` (served as JPEG), `wp-content/uploads/2025/11/cropped-GivMoo-Cow-Only-192x192.png` |
| "100% of the retail profits go back to the organization behind it" | givmoo.com/about-us/ and the application page (hellogivmoo.com/apply) |
| "Fully managed", product creation to fulfillment, customer service, marketing | givmoo.com/about-us/ |
| "Within 2 business days" reply on applications | hellogivmoo.com/apply |
| Free shipping over $50 | live site top bar |
| 5K happy customers, 4.9★ average rating, 328+ products | live homepage stat row |
| 7,000+ subscribers, $5 off | live homepage newsletter block |
| Bulk orders "decorated or blank in most cases" | live homepage FAQ |
| "Custom merch for schools, teams, nonprofits and events" | givmoo.com/wholesale/ page title |
| Reviews (Linda, Erica Bingham) | live homepage "What Our Customers Say" |
| FAQ answers | live homepage FAQ, lightly edited for length |
| Address, email, social links | live homepage footer |

**Products (name, price and "Sold By" checked on each live product page 2026-09-28; images are the 600x600 versions from each page):**

| Product | Price on live page | Sold by |
|---|---|---|
| Women's Columbia® Fleece Vest, Veteran Flag Design | $75.00 to $80.00 | GivMoo GiveBack Fund |
| Men's Columbia® Fleece Vest, Veteran Flag Design | $75.00 to $85.00 | GivMoo GiveBack Fund |
| Veterans Collaborative Minimal Canvas Tote | $24.99 | Veterans Collaborative |
| TAD Foundation All-Over Print Bandana | $24.99 | TAD Foundation |
| God Said Go Youth Hoodie | $34.99 | God Said Go Missions, Inc. |
| GivMoo Cow Logo Unisex Long-Sleeve Shirt | $29.99 to $35.99 | GivMoo GiveBack Fund |
| Funny Cat Mug, Orange Kitty | $26.99 | GivMoo GiveBack Fund |
| Theodore Roosevelt Tuba Solo Graphic Tee | $24.99 to $34.99 | GivMoo GiveBack Fund |

Display names are the first half of each live title (before the `|`). The full live title is on the linked product page.

## Not live yet, or needs your confirmation

- **Harvest of Savings is Evan's proposed October promo, not a live offer.** Wording from the call: send us your last quote and we beat it, or we give you a $100 gift card. It carries a "Proposed October promo" tag on the page. Confirm the terms before it goes on the real site.
- **Trust numbers are your claims to substantiate:** 5K happy customers, 4.9★ average rating, 328+ products, 7,000+ subscribers. They are copied from the live page. Keep them only if you can back them up (an AI assistant or a buyer may ask where the 4.9 comes from).
- **"Free" for nonprofits:** the mockup says "Open a GivMoo store for your cause" and does not say free, because the live site never says it. If stores cost a nonprofit nothing, say so. It is the strongest line you have for that door.
- **"Your logo on apparel, drinkware and gifts" and "No inventory to buy or store"** are read from the live catalog and About page, not quoted. Confirm.
- **Profits vs proceeds:** the About page says "100% of the retail profits" in one paragraph and "100% of proceeds" in another. They mean different things to a donor. The mockup uses "retail profits". Pick one and use it everywhere.
- **Hero photo** is the stock shopping-bags image from the live site. A photo of a real nonprofit partner with their merch would do more.

## Things on the live site this build tripped over

- About Us still carries theme demo content below the team: "45 M Products for sale", "1.8 M Sellers Active on Martfury", a timeline about "Martin Garrix", and seven "Robert Downey Jr, CEO Founder" cards.
- The God Said Go product page links to `/store/godsaidgo/`, which returns 404. The working store is `/store/gsg/`.
- `/wholesale/` renders its content with JavaScript, so a crawler that does not run JavaScript sees an empty body.
- The footer links to `linkedin.com/company/109520400/admin/dashboard/` (the admin view).
- Typos: "For Nonprofitss" (footer heading), "complementary" for "complimentary" (returns FAQ), "Customer love these winning products".

## AI search readiness built in

All copy is in the static HTML body (no JavaScript rendering), one H1, one heading per section, meta description, and JSON-LD for `Organization` and `FAQPage` built only from facts on the live site. The FAQ answers in the JSON-LD match the visible answers.

**This preview is set to noindex** (`<meta name="robots" content="noindex,nofollow">` plus a `robots.txt` that disallows everything) so it never competes with givmoo.com in search. Remove both in production.

## Hosting it on GitHub Pages

1. Push this folder to a GitHub repo.
2. Settings, Pages, Source: deploy from branch `main`, folder `/ (root)`.
3. The page appears at `https://<owner>.github.io/<repo>/` in a minute or two. `.nojekyll` is included so the files are served as-is.

Fonts load from Google Fonts. Product images and the logo are copies in `assets/`, taken from givmoo.com for GivMoo's own review.
