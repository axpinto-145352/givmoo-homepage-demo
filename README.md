# GivMoo homepage: storefront concept (v3)

v3, 2026-09-29. Direction from Anthony: think Amazon, but for GivMoo. Get each shopper to the right place at the right time without overwhelming them.

v1 had 5 sections and read as a lot. v2 cut to 3 but read like a landing page, not a store. v3 is a storefront. The page runs about 2.3 phone screens (the live homepage is about 11.7).

## How it routes people

| Shopper | Where they go | On the page |
|---|---|---|
| Knows what they want | Search | Search bar in the header, sent to GivMoo's real product search (`/?s=...&post_type=product`) |
| Browsing a type of thing | Departments | Dark department bar (Best sellers, Fall, Apparel, Drinkware, Accessories, Pets, Bath & body, Home décor, Shop by cause), plus 4 "Shop by what you need" tiles |
| Here for the season | The one banner | Fall favorites now. Rotates by season (below) |
| Wants what others buy | Best sellers | 8 products in the store's real popularity order, swipe on a phone |
| Starts from a cause | Shop by cause | 8 cause chips + All causes |
| Runs a nonprofit | Side door | "For nonprofits" in the header, one band at the bottom. Kept out of the shopper path |

One line under the department bar says what GivMoo is: "Every purchase supports a cause. Free shipping on orders over $50."

## The right-time banner: suggested rotation (from GivMoo's own categories)

| When | Banner | Category size today |
|---|---|---|
| Aug | Back to School | 51 products |
| Sep to Oct | Fall | 50 products |
| Nov to Dec | Holiday gifts | ⚠️ Christmas has 4 products, Kwanzaa 1. Build this out before November |
| Mar to May | Spring | 38 products |
| Jun to Jul | Summer + 4th of July | 54 + 9 products |

## Data behind the page
Prices, names, images, categories and the best-seller order come from GivMoo's WooCommerce Store API (`/wp-json/wc/store/v1/products?orderby=popularity`), pulled 2026-09-29. The WAG cap's "Sold By" was confirmed on its product page. Product names are shortened for the cards.

## Things this build found on the live store
- The #1 best seller's main photo (Mootilda socks) still carries a "FREE Pair, July 20 to Aug 31" ribbon. That offer is over. The mockup uses the product's second photo.
- The IISE mug and tumbler titles say "Professional Engineering Society." IISE Global is the International Institute for Sexual Empowerment (iiseglobal.org). The titles describe the wrong organization.
- Only 2 of the 30 best sellers have a review (1 each). Amazon-style star ratings aren't possible yet, so the cards don't show them.
- The #3 best seller is titled "LoveShackFancy® Inspired." A brand name in a product title is worth a second look.

## What was cut from the live homepage

Second H1 ("GivMoo" and "Every Small Purchase Has BIG Impact." are both H1s on the live page), Featured Favorites category tabs, the "Your shortcut to best sellers" carousel, "Favorite Finds Only On GivMoo", the Buy Now Pay Later banner (Afterpay, Klarna, Zip), the shipping banner, Smart Finds tiles, the full "Shop All Over 328 items" catalog with filters and 37 pages, the Live Shipping / Great Gifts / Quality Guarantee strip, Shop by Collection tiles, and three of the FAQs (size waitlist, gift wrapping, order tracking). All of it still exists one click away on /shop/ and the category pages.

## Sources

| What | Source |
|---|---|
| Colors, font | `--gm-*` tokens in the live stylesheet (primary `#e84a1a`, dark `#c13a0e`, accent `#f4831e`, light `#fff4ee`, font Nunito Sans) |
| Logo, favicon | givmoo.com theme assets |
| "Every purchase supports a cause", retail profits go to the organization | givmoo.com/about-us/ ("every product purchased directly supports a cause") |
| "We build and run a store for your cause" | givmoo.com/about-us/ ("a fully managed solution... from product creation to fulfillment") |
| Bulk merch for programs and fundraisers | givmoo.com/wholesale/ page title |
| Free shipping over $50 | live site top bar |
| Department and cause links, product names, prices, images, best-seller order | Store API, pulled 2026-09-29 |
| Search | GivMoo's own product search, `https://givmoo.com/?s=mug&post_type=product` returned 12 products on 2026-09-29 |

**Products on the page (price and organization from the Store API, 2026-09-29):**

| Where | Product | Price | Supports |
|---|---|---|---|
| Banner | Women's Columbia® Fleece Vest (in the Fall category) | not shown | GivMoo GiveBack Fund |
| Tile: Apparel | God Said Go Youth Hoodie | not shown | God Said Go Missions, Inc. |
| Tile: Mugs & tumblers | IISE Insulated Tumbler | not shown | IISE Global |
| Tile: Hats | WAG Women's Mesh-Back Cap | not shown | WAG History Preservation |
| Tile: For your pet | NASP Pink Pet Tank Top | not shown | Nebraska Association of Service Providers |
| Best seller 1 | Mootilda Cow Print Knee-High Socks | $27.99 | GivMoo GiveBack Fund |
| Best seller 2 | Sleep Essential Oil Combo, 3 Piece | $15.00 | GivMoo GiveBack Fund |
| Best seller 3 | Blue & White Checker Mini Dress | $42.99 | GivMoo GiveBack Fund |
| Best seller 4 | WAG Women's Mesh-Back Cap | $29.99 | WAG History Preservation (Sold By, product page) |
| Best seller 5 | IISE Logo Ceramic Mug, 11 oz | $19.99 | IISE Global |
| Best seller 6 | IISE Insulated Tumbler, 20 oz | $44.99 | IISE Global |
| Best seller 7 | Fall Press-On Nails with Manicure Kit | $15.00 to $15.99 | GivMoo GiveBack Fund |
| Best seller 8 | Boomer Retro Graphic Tee | $19.99 to $24.99 | GivMoo GiveBack Fund |

## Needs your confirmation
- **"Free" for nonprofits:** the page says "Get a store" and doesn't say free, because the live site never says it. If a store costs a nonprofit nothing, say so. It's the strongest line you have for that door.
- **Profits vs proceeds:** the About page says "100% of the retail profits" in one place and "100% of proceeds" in another. This page sidesteps it ("supports a cause"). Pick one and use it everywhere.
- **Harvest of Savings** (your October promo idea) belongs on the wholesale page, where the bulk buyer already is, so it isn't on this page.

## Things on the live site this build tripped over

- About Us still carries theme demo content below the team: "45 M Products for sale", "1.8 M Sellers Active on Martfury", a timeline about "Martin Garrix", and seven "Robert Downey Jr, CEO Founder" cards.
- The God Said Go product page links to `/store/godsaidgo/`, which returns 404. The working store is `/store/gsg/`.
- `/wholesale/` renders its content with JavaScript, so a crawler that does not run JavaScript sees an empty body.
- The footer links to `linkedin.com/company/109520400/admin/dashboard/` (the admin view).
- Typos: "For Nonprofitss" (footer heading), "complementary" for "complimentary" (returns FAQ), "Customer love these winning products".

## AI search readiness built in

All copy is in the static HTML body (no JavaScript rendering), one H1, a heading per section, a meta description, and JSON-LD for `Organization` plus a `WebSite` `SearchAction` pointing at GivMoo's real product search.

**This preview is set to noindex** (`<meta name="robots" content="noindex,nofollow">` plus a `robots.txt` that disallows everything) so it never competes with givmoo.com in search. Remove both in production.

## Hosting it on GitHub Pages

1. Push this folder to a GitHub repo.
2. Settings, Pages, Source: deploy from branch `main`, folder `/ (root)`.
3. The page appears at `https://<owner>.github.io/<repo>/` in a minute or two. `.nojekyll` is included so the files are served as-is.

Fonts load from Google Fonts. Product images and the logo are copies in `assets/`, taken from givmoo.com for GivMoo's own review.
