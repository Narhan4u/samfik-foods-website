# Samfik Foods Website: Handover Guide

This guide is for the owner of the Samfik Foods website. It explains what the site does, how to make everyday changes, and how hosting and the domain are set up.

- **Website address:** https://samfikfoods.co.uk/
- **Business:** Samfik Foods, Unit B4, Macclesfield Market Hall, Grosvenor Centre, Macclesfield, SK11 6AJ
- **Orders go to:** WhatsApp on 07404 531445

---

## 1. What the website does

The site is a single page with these sections, from top to bottom:

1. **Header:** logo, menu links, an "Open now / Closed" badge (worked out from UK time and your opening hours) and a "Call to Order" button.
2. **Hero:** "A taste of home. Right here in Macclesfield." over a photo of the stall, with a form for orders, pre-orders and catering.
3. **Our crowd favourites:** a grid of dishes. Each "Order →" link opens that dish's options.
4. **Order Online:** the full menu with prices. Customers tap a dish, choose options, add it to their order, then send the whole order on WhatsApp.
5. **Services, Why Us, and Pre-order in 3 steps.**
6. **Visit:** address, map, directions link, opening hours (today is highlighted) and phone number.
7. **FAQ, call-to-action band and footer.**
8. **On phones:** a bar fixed to the bottom of the screen with Call, Order Now and Directions buttons.

### How ordering works
- There's **no online payment and no database**. When a customer presses "Send order on WhatsApp" (or "Send My Request" in the hero form), WhatsApp opens on their phone with the order already typed out. They press send and it arrives on 07404 531445.
- The message lists each item with its options and price, the total, and the customer's name, phone number and collection time.
- You confirm the order and collection time by replying on WhatsApp. Customers pay at the stall.
- **Check WhatsApp regularly during opening hours.** That's where every online order arrives.

---

## 2. The files

| File | What it is |
|---|---|
| `index.html` | The page itself: all the text, sections, address, hours and phone links. |
| `menu.js` | **The menu: dishes, descriptions, options and prices.** Most changes happen here. |
| `styles.css` | The look: colours, fonts, layout. |
| `script.js` | Small behaviours: open/closed badge, mobile menu, hero form, scroll animations. |
| `images/` | Logo, stall photo and food photos. |
| `CNAME` | Holds the domain name (`samfikfoods.co.uk`) for GitHub Pages. |
| `.github/workflows/pages.yml` | Publishes the site automatically whenever changes are saved to the `main` branch. |

You can edit any of these in the browser on GitHub: open the file, click the pencil icon, make your change, then click **Commit changes**. The live site updates about a minute later.

---

## 3. Everyday changes

### Change a price
Open `menu.js` and find the dish. For example:

```js
{ name: "Jollof Rice", price: 9.00, ...
```

Change `9.00` to the new price. Write just the number, without the £ sign.

Paid extras on rice plates are near the top of `menu.js`:

```js
var EXTRAS = { name: "Add a little extra", required: false, options: [{ name: "Meat Pie", price: 1.99 }, { name: "Puff Puff (3)", price: 1.50 }] };
```

### Current prices

| Dish | Price |
|---|---|
| Jollof Rice | £9.00 |
| Rice & Beans | £9.00 |
| Chicken Suya | £6.99 |
| Lamb Suya | £7.99 |
| Peppered Chicken | £6.99 |
| Peppered Turkey | £8.99 |
| Loaded Fries | £5.99 |
| Meat Pie | £1.99 |
| Puff Puff (3 pieces) | £1.50 |
| Extra on a rice plate: Meat Pie | +£1.99 |
| Extra on a rice plate: Puff Puff (3) | +£1.50 |

Proteins, free coleslaw and spice level don't add to the price.

### Change the protein choices for rice plates
In `menu.js`, edit the list under `var PROTEINS`. Each choice is one line:

```js
{ name: "Jerk Chicken" },
```

To charge extra for a choice, add a price: `{ name: "Lamb Suya", price: 1.00 },`

### Add a new dish
In `menu.js`, copy an existing dish (everything from `{ name:` to the matching `}`), paste it into the right category, and change the name, price, description and photo filename. Make sure there's a comma between dishes.

### Hide a dish for the day
Easiest: delete the dish from `menu.js` and add it back later. You can find the old version in the file's history on GitHub (the **History** button).

### Change opening hours
Hours appear in **three places**:
1. `index.html`, the **Visit** section's hours table (search for `10:00 – 16:30`), plus the hero ("Mon–Sat 10:00 – 4:30") and the footer.
2. `index.html`, near the top in the business details for Google (`"opens"` and `"closes"`).
3. `script.js`, which drives the Open/Closed badge. The times are in minutes after midnight: `600` = 10:00 and `990` = 16:30. Days run from `1` (Monday) to `6` (Saturday). Also update the "till 4:30pm" text on the same line.

### Change the phone / WhatsApp number
Change it everywhere:
- `script.js`: `var PHONE = "447404531445";` (country code 44, no leading 0, no spaces)
- `menu.js`: the same `var PHONE = ...` line
- `index.html`: search for `7404531445` and `7404 531445` and replace every match, including the `tel:` links and the WhatsApp link in the footer.

### Change wording
All visible text is in `index.html`. Use your browser's search (Ctrl+F) to find the sentence, then edit it.

---

## 4. Photos

### Food photos
Put photos in the `images/` folder with these **exact** names, and they appear automatically on the matching dish cards and pop-ups:

`jollof.jpg`, `rice-and-beans.jpg`, `chicken-suya.jpg`, `lamb-suya.jpg`, `peppered-chicken.jpg`, `peppered-turkey.jpg`, `loaded-fries.jpg`, `meat-pie.jpg`, `puff-puff.jpg`

- **Best size:** landscape, about 1200 × 900 pixels, and under 300 KB each. Shrink large phone photos first, for example with https://squoosh.app.
- Until a photo is added, the card shows a coloured block.
- **To upload on GitHub:** open the `images` folder, choose **Add file → Upload files**, then commit.

### Stall photo (hero background)
`images/stall.jpg` (desktop) and `images/stall-960.jpg` (phones). To replace it, upload new files with the same names. The photo was cropped and colour-corrected from a photo of the stall. A professional photo, taken straight on with the stall lights on, would look even better.

### Logo
- `images/logo.svg`: the main logo, used in the header, hero, footer and browser tab. It stays sharp at any size.
- `images/logo-512.png`: shown when the website link is shared on WhatsApp or Facebook.
- `images/logo-180.png`: icon when someone saves the site to their phone's home screen.

The logo is a clean vector redraw of the Samfik Foods sign. The fonts it uses are free for commercial use: Kaushan Script for "Samfik" and Montserrat for "FOODS", both under the SIL Open Font License. If you get original artwork from your designer, replace these three files.

---

## 5. Hosting (GitHub Pages)

The site is hosted for free on **GitHub Pages**.

### Setting up in your own GitHub account
1. Create a free account at https://github.com, or use an existing one.
2. Accept the transfer of the website repository, or upload these files to a new repository.
3. In the repository, go to **Settings → Pages**. Under **Build and deployment → Source**, choose **GitHub Actions**.
4. Go to the **Actions** tab and run **Deploy site to GitHub Pages**, or make any small change on `main`. The site publishes in about a minute.
5. **Settings → Pages → Custom domain:** enter `samfikfoods.co.uk` and save. Do this only **after** the DNS records in section 6 are in place.
6. Once GitHub shows the DNS check has passed, tick **Enforce HTTPS**.

Every time a change is saved to the `main` branch, the site republishes automatically. You can watch progress in the **Actions** tab.

---

## 6. Domain: samfikfoods.co.uk

The domain should be registered **in the business owner's name and email**. Whoever is named on the domain controls it.

At the company where the domain is registered, add these DNS records:

| Type | Name / Host | Value |
|---|---|---|
| A | @ | 185.199.108.153 |
| A | @ | 185.199.109.153 |
| A | @ | 185.199.110.153 |
| A | @ | 185.199.111.153 |
| CNAME | www | *your-github-username*.github.io |

- Delete any other A records on `@` first, such as a "parked page" record.
- Changes can take from a few minutes to 24 hours to work.
- **Renewal:** domains renew yearly. Turn on auto-renew and keep the payment card up to date, or the website stops working when the domain expires.

---

## 7. Test after any change

1. The page loads with the logo and the stall photo.
2. Prices on the dish cards are correct.
3. Open a rice plate and try to add it without a protein; it should ask you to choose one.
4. Add a few dishes, open the basket and check the total.
5. Send a test order to WhatsApp and check the message.
6. Check on a phone too: the bottom bar works and the category bar scrolls sideways.
7. The Open/Closed badge matches the real time.

If something breaks after a change, open the file's **History** on GitHub to see what changed, or restore the previous version.

---

## 8. Accounts the owner should control

| What | Where | Notes |
|---|---|---|
| Domain | Your domain company | Owner's name and email, auto-renew on |
| Website code and hosting | GitHub | Owner's account; add a helper as a collaborator if needed |
| WhatsApp | 07404 531445 | Where online orders arrive |
| Google Business Profile | business.google.com | Add the website address; ask happy customers for reviews |

Never share passwords by chat or email. If someone else helped set things up, remove their access once the handover is complete.

---

## 9. Ideas for later

- Add food photos (biggest impact on orders).
- Add real customer reviews from Google once you have a few.
- Add a "Today's specials" note at the top of the menu.
- Online card payments, which would need a service such as Stripe or Square.
- Business email such as orders@samfikfoods.co.uk.
