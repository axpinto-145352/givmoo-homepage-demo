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

## Tested on (2026-09-30, live URL)
WebKit (Safari and every iPhone/iPad browser) and Chrome 152 (Android Chrome, desktop Chrome and Edge) at 16 sizes: phones 320 to 430 wide, two phones on their side, three tablets, desktops 1280 to 2560. Firefox 154 at 1280, 1366, 1920 and a 400px window. Each run checks: no sideways page scroll, fonts and images load, no clipped labels, tap targets at least 24px (nav targets 44px), one H1, search submits to `givmoo.com/?post_type=product&s=...`, and the last best seller can be reached (arrows at 720px and up, swipe below).

Only the search bar stays pinned when you scroll (like Amazon's mobile site). The department bar scrolls away. On phones, "For nonprofits" moves into the department bar.

## The right-time banner
Each banner product carries the name of the nonprofit it supports, so the cause is concrete at first glance.
- **Now to Oct 31: "Cozy hoodies that back a real nonprofit."** Veterans Collaborative, Capital Cabaret and Nebraska Association of Service Providers hoodies (all in the Fall category, $49.50 to $62.00).
- **Nov 1 to Dec 31: "Gifts under $25 that give back."** Veterans Collaborative mug ($19.99), Capital Cabaret koozie ($12.99), Veterans Collaborative tote ($24.99). Links to the Holidays category.
- The page switches on the visitor's date. Preview either one now: add `?season=gifts` or `?season=fall` to the link. Crawlers and no-JavaScript visitors see Fall.

Suggested rotation for the rest of the year, from GivMoo's own categories:

| When | Banner | Category size today |
|---|---|---|
| Aug | Back to School | 51 products |
| Sep to Oct | Fall (built) | 50 products |
| Nov to Dec | Gifts that give back (built) | ⚠️ Christmas has 4 products, Kwanzaa 1. The Holidays category is mostly Veterans Collaborative merch and koozies. Build a real gift collection before November |
| Mar to May | Spring | 38 products |
| Jun to Jul | Summer + 4th of July | 54 + 9 products |

## Data behind the page
Prices, names, images, categories and the best-seller order come from GivMoo's WooCommerce Store API (`/wp-json/wc/store/v1/products?orderby=popularity`), pulled 2026-09-29. The WAG cap's "Sold By" was confirmed on its product page. Product names are shortened for the cards.

## Things this build found on the live store
- **The delivery promise contradicts itself.** Every product card on the live homepage says "Get it in 2-4 days". The FAQ says "it takes 2-5 days to produce and standard shipping takes 3-5 business days." The mockup uses the FAQ numbers. Pick the true one and use it everywhere.
- **"®-Inspired" product titles are a pattern, not a one-off.** The Fall category alone has "Adidas® Inspired" (6 shoes), "Converse® Inspired", "REI® Inspired" (2 tees) and "Mead® Inspired", plus "LoveShackFancy® Inspired" in best sellers. Worth a lawyer's look.
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
| Fall banner | Veterans Collaborative / Capital Cabaret / NASP unisex hoodies | $49.50 to $62.00 each | Veterans Collaborative (Sold By, product page) / Capital Cabaret DC / NASP |
| Gift banner | Veterans Collaborative mug / Capital Cabaret koozie / Veterans Collaborative tote | $19.99 / $12.99 / $24.99 | Veterans Collaborative / Capital Cabaret DC / Veterans Collaborative |
| Tile: Apparel | GivMoo Cow Logo Unisex Long-Sleeve Shirt | not shown | GivMoo GiveBack Fund |
| Tile: Mugs & tumblers | Funny Cat Mug, Orange Kitty | not shown | GivMoo GiveBack Fund |
| Tile: Hats | WAG Women's Mesh-Back Cap | not shown | WAG History Preservation |
| Tile: For your pet | Tuxedo Pet Sweater with Red Bow Tie | not shown | GivMoo GiveBack Fund |
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

**This preview is set to noindex** (`<meta name="robots" content="noindex,nofollow">`) so search engines that honor it never list it against givmoo.com. The `robots.txt` in this folder has no effect: crawlers only read robots.txt at the root of a host (`axpinto-145352.github.io/robots.txt`), not in a project subfolder. Remove the noindex tag in production.

## Hosting it on GitHub Pages

1. Push this folder to a GitHub repo.
2. Settings, Pages, Source: deploy from branch `main`, folder `/ (root)`.
3. The page appears at `https://<owner>.github.io/<repo>/` in a minute or two. `.nojekyll` is included so the files are served as-is.

Fonts load from Google Fonts. Product images and the logo are copies in `assets/`, taken from givmoo.com for GivMoo's own review.
