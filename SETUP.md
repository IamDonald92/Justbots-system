# Just Bots quotes and invoices

A single page app for building quotations and invoices from your product list,
saving them to a Google Sheet, downloading a PDF and sending on WhatsApp.

Two files matter:

- `index.html` is the whole app. Nothing else is needed to run it.
- `Code.gs` is the Google Apps Script backend that writes to your sheet.

---

## 1. Put the app on GitHub Pages

1. On github.com, create a new repository. Call it `justbots-docs`.
2. Upload these six files to it, all in the root, not in a folder:
   `index.html`, `manifest.webmanifest`, `icon-192.png`, `icon-512.png`,
   `apple-touch-icon.png`. `Code.gs` and `SETUP.md` can go up too but are
   not used by the site.
3. In the repo, open **Settings > Pages**.
4. Under **Build and deployment**, set Source to **Deploy from a branch**,
   branch **main**, folder **/ (root)**. Save.
5. Wait about a minute. Your app is live at
   `https://YOURUSERNAME.github.io/justbots-docs/`

Bookmark that on your phone. On iPhone use Share then Add to Home Screen,
on Android use the browser menu then Add to Home screen. It installs with
the Just Bots icon and opens full screen, without browser bars.

**Read this before you upload.** On a free GitHub account, Pages only works
from a public repository, which means anyone who finds the repo can read
`index.html`. That is fine for the product list because your retail prices
are already public. It is not fine for cost prices, margins, banking details
or client information, so none of those live in the file. Your banking
details and your records URL are entered in the app's Settings screen and
stay on your own device.

If you would rather the repository were private, GitHub Pro is about four
US dollars a month and enables Pages on private repos.

---

## 2. Connect the records sheet

1. Create a new Google Sheet. Name it something like `Just Bots records`.
2. **Extensions > Apps Script**. Delete whatever is in the editor.
3. Paste in everything from `Code.gs`. Save.
4. **Deploy > New deployment**. Click the gear, choose **Web app**.
   - Description: anything
   - Execute as: **Me**
   - Who has access: **Anyone**
5. Deploy, authorise when Google asks, and copy the **Web app URL**.
   It ends in `/exec`.
6. Open your app, tap **Settings**, paste the URL into
   *Apps Script web app URL*, fill in your banking details, then save.

Do this on both your phone and Precious's, since settings live per device.

The sheet and its headers are created automatically the first time
something saves.

---

## 3. Day to day

- Search or filter to find a product, tap **Add**. Tap again to add another.
- Adjust quantity with the plus and minus buttons, or type a number.
- **change price** on any line overrides the price for that document only.
  It does not change your list.
- **Add custom line** covers anything not in the list, including services.
- Switch between **Quotation** and **Invoice** at the top. Numbering follows
  `JB-Q-2026-001` and `JB-I-2026-001`, counted per year from what is already
  in the sheet.
- **Send PDF on WhatsApp** builds the PDF and hands it to your phone's share
  sheet, where you pick WhatsApp and the contact. The PDF goes as a real
  attachment with a short covering message. On a laptop, browsers are not
  allowed to attach files to WhatsApp, so it saves the PDF and opens the chat
  with the full breakdown as text, ready for you to drag the file in.
- **Save to records** writes to the sheet. Saving the same number twice
  updates that row rather than creating a duplicate, so you can revise a
  quote safely.
- **History** loads any saved document back into the app. To turn a quote
  into an invoice, load it, switch the toggle to Invoice, press **New**
  next to the number, then save.
- Your work in progress is kept on the device, so closing the tab by
  accident does not lose it.

---

## 4. About the prices

Every price in `index.html` has been checked line by line against your
August 2026 price lists. Forty three products are loaded and priced.

To change a price permanently, edit the `PRODUCTS` block near the top of the
script in `index.html` and re-upload. Each entry looks like this:

```js
{c:'Pantry', b:'Sheroo', n:'Motlopi Coffee, 150g', p:80},
```

`c` is the category, `b` is the brand, `n` is the product name, `p` is the
price. Add a line to add a product, delete a line to remove one.

Three products are deliberately not in the app, because they have no price
on any list yet. Send me the prices and I will add them:

- Sheroo Motlopi Coffee 150g. The list carries 100g at P70 and 200g at P90,
  but the pack you actually stock reads 150g.
- Aneela Cranberry Trail Mix 120g. The list has Peanuts and Cranberry at 70g
  for P25, which is a different product.
- Donut Heart Cookies. These are inside Package 3 but priced nowhere, which
  also means Package 3 cannot be costed properly.
