# Kishorilal Amarchand — Billing Software

A simple, offline billing app for the Kishorilal Amarchand family-wear & fabric shop.
It is a **single HTML file** (`shop-billing.html`) that runs in a web browser. No internet,
no installation, no monthly fee. All data stays on the shop's own computer.

---

## How to run it

1. Download **`shop-billing.html`** (on GitHub: open the file → **Download raw file**).
2. Put it somewhere safe on the shop laptop — **not** the Downloads folder.
3. Open it in **Google Chrome** or **Microsoft Edge** (double-click the file).
4. Make it feel like an installed app (optional):
   - **Chrome:** ⋮ menu → *Cast, save and share* → **Create shortcut…** → tick **Open as window**.
   - **Edge:** ⋯ menu → *Apps* → **Install this site as an app**.

First time: go to **Settings** and enter the shop name, address, phone, receipt width
(58 mm / 80 mm), and your starting bill number. Add your products and staff, and check the
discount codes.

---

## What it does

- **Billing** — GST-inclusive, no tax lines. Prints a thermal receipt (58/80 mm).
- **Discount codes** — letter codes before the price (`A500` = MRP ₹500, code A = ₹100 off)
  and number codes at the end (`1204` = MRP ₹120, code 4 = ₹20 off). All editable.
- **Per item** — Item · Qty · MRP (with code) · Discount (₹ or %) · Sale price.
  Quantity takes decimals for fabric (`1.20` = 1 m 20 cm).
- **Extra discount** on the whole bill (₹ or %).
- **Payment mode** — Cash / UPI / Card / **Split**.
- **Hold & recall** bills, **reprint last**, and a **bill finder** (by number, name, phone, date).
- **Returns & exchange** against a past bill (refund, or swap and bill the difference).
- **Customers** (deduped by phone) & **staff**, with history.
- **Reports** — sales, discounts, returns, by staff, by department, top products, CSV export.
- **Day close** — payment-mode split + **expected cash in drawer** (opening cash + cash in − cash out).
- **Import / export** products & customers as CSV.
- **Keyboard-first** — type → arrows → Enter → code → Enter → **F2** to save & print.

---

## Your data & backups (important)

- Data is saved **in the browser, on that one computer**. It is **not** in this file and
  **not** on GitHub.
- Set up **automatic backup to a folder** (Settings → Automatic backup folder). Point it at a
  **Google Drive / OneDrive** folder for off-site safety. It writes a live backup as you work
  and a dated backup when you close the app.
- You can also **Download backup** manually and **Restore** any backup (including a specific
  dated one).
- Clearing the browser's site data **erases** un-backed-up bills — so keep backups.

> This repo stores the **program**, not the shop's sales data. Updating the app from GitHub
> never touches your saved bills.

---

## Files

- `shop-billing.html` — the app (this is the whole program).
- `SPEC.md` — full feature spec and the decisions behind them.

---

## Updating

When the app is improved, a new `shop-billing.html` is committed here. Download the latest and
replace your copy — your saved data carries over automatically (the app upgrades old data on open).
