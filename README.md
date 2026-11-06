# Shop Billing App (demo)

A simple bill / invoice maker for a sanitary & electric shop. One file (`index.html`), no database, no server code, no internet needed.

## What it does
- Search a product → pick a size → set quantity and unit price → Add to bill
- Bill table with editable qty / price, discount, paid, due, total
- Total in words (English), customer name / phone / address
- Save & Print (A4 or A5, uses the normal browser print dialog; "Save as PDF" also works)
- Saved bills list: reopen, reprint, delete. Invoice numbers count up automatically
- Products screen: add / edit / delete products; one line per size: `size, price`
- Shop settings: shop name, address, phone, footer note (Bengali works), next invoice number
- Backup: Export / Import JSON (products + settings + saved bills)

## Run on his own computer (free, forever)
**Easiest:** double-click `index.html`. It opens in Chrome/Edge and works fully offline.

**As a small local server** (so other phones/PCs on the shop Wi-Fi can use it too):
```
cd billing-app
python -m http.server 8000
```
Then open `http://localhost:8000` (or `http://<shop-pc-ip>:8000` from another device).

## Deploy free on Render
1. Put the folder in a GitHub repo (just `index.html` is enough).
2. Render → New → **Static Site** → connect the repo.
3. Build command: leave empty. Publish directory: `.`
4. Deploy. Render gives a free `https://....onrender.com` link. Static sites don't sleep.

(Netlify, Cloudflare Pages or GitHub Pages work the same way.)

## Important: where data is stored
Products and saved bills are stored in the **browser's localStorage** on each device. That means:
- Use the same browser on the same device every day, or the list will look empty.
- Clearing browser data deletes it. **Press "Export backup" in Products regularly** (e.g. weekly).
- A phone and a PC have separate data. Use Export / Import to copy between them.
If he later needs one shared product list and bill history across devices, the next step is a small Node/SQLite backend.

## Add real products
Products → **+ New product** → name, then sizes like:
```
1/2", 30
3/4", 45
1", 65
```
Use "Reset to demo products" only if you want to wipe the list.
