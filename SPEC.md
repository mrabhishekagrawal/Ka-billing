# Kishorilal Amarchand — Billing Software Spec

Master feature list and the decisions behind the app. (Also kept in the Claude "Ka" project.)

_Last updated: 2026-10-30_

**Format:** one self-contained file, `shop-billing.html`, opened in **Chrome or Edge on the shop laptop**. Runs offline; all data stored on that device.

**Product workflow (important):** the shop bills by a short list of **generic item-names** (Mens Full Shirt, Mens Half Shirt, Jeans, Kurti, Saree, Fabric…), not individual SKUs. The rate + code is read off the tag and typed on each bill. So features that need a full per-item catalog don't apply (see Key decisions).

---

## Billing
- GST-inclusive pricing; **no GST / CGST / SGST shown anywhere**. Bill heading: "CASH MEMO" (editable).
- Currency ₹ (INR), Indian number formatting. Round total to nearest rupee (toggle).

## Discount codes (Codes tab — all amounts editable anytime)
- **Letter codes** = prefix, before the MRP. e.g. `A500` → code A, MRP ₹500.
- **Number codes** = single digit, at the end. e.g. `1204` → code 4, MRP ₹120.
- Defaults: A = ₹100, B = ₹50, C = ₹500 (plus any added).

## Item entry
- Select or type a product → one **combined dialog**: Code & MRP, Discount (₹ / %, auto-filled from the code), Quantity, live net preview, then Add.

## Per item — cart columns: Item name · Qty · MRP · Discount · Sale price
- MRP shown **with its code** (e.g. A500). Discount per item in ₹ or %.
- Quantity supports **decimals for fabric** (1.20 = 1 m 20 cm); whole numbers for pieces.
- Sale price = (MRP − discount) × qty. Tap an item to edit it.

## Bill level
- **Extra discount** on the whole bill, in ₹ or %. Totals: Total MRP, Item discounts, Extra discount, Round off, TOTAL.
- **Payment mode:** Cash / UPI / Card / **Split** (part amounts that sum to the total).

## People
- Customer and Staff chosen via **search bars**. Walk-in default.
- Customers deduped by **phone only**; multiple same-name customers allowed (name-only entries are fine, useful for finding a bill by customer name + date).
- Adding a customer whose phone already exists → "already exists" dialog → OK selects them.
- Customer records + purchase history. Staff selected per bill, printed, tracked in reports.

## Products
- Catalog of names + optional saved MRP (suggestion only) + **department**. Can bill an unlisted name on the fly.

## Receipt (thermal)
- **58 mm or 80 mm**. Columns match screen: item name, then Qty · MRP (with code) · Disc · Sale. Shop header, bill no + date/time, customer, staff, payment, totals, footer.

## Hold / find / reprint / returns
- **Hold & recall** bills (multiple, kept until recalled).
- **Reprint last** (F9) and a **bill finder** by number / name / phone / date.
- **Returns & exchange** against a past bill: refund (cash/UPI/card), or exchange (return items + new items, bill the difference or refund it).

## Reports
- Range: Today / This month / Custom. Net sales, bills, discount given, returns.
- **Sales by department**, Sales by staff, Top products, bill list (view/reprint). CSV export.

## Day close
- For a chosen day: net sales, payment-mode split (Cash/UPI/Card), returns.
- **Expected cash in drawer** = opening cash (entered) + cash received − cash refunded. Printable.

## Import / export
- Products & Customers each have **Export CSV** and **Import CSV** (the export is the template).
- Products deduped by name; customers deduped by phone (no-phone rows always added).

## Data safety
- Auto-saves after every action. Half-finished bill survives a shutdown.
- Automatic backup to a chosen folder (live + dated-on-close, Chrome/Edge).
- Manual Download / Restore / Reset. **Restore a specific dated backup** from the folder.

## Keyboard (laptop)
- Search auto-focused. Type → ↑/↓ → Enter opens item → code + MRP → Enter adds → back to search.
- F2 / Ctrl+Enter = Save & print. F3 = search. F9 = reprint last. Esc = cancel. Alt + 1–8 = tabs. ? = help.

---

## Not built yet (available anytime)
Cash out / expenses · bill note/remark · round-off to ₹5/₹10 · invoice-number reset · deeper reports (top customers, peak hours, month-vs-month, basket size, returns rate) · cash tendered & change · khata/udhaar · WhatsApp the bill · UPI QR on receipt · amount in words · gift receipt · loyalty points · birthday reminders · sales charts · stitching-charge line · owner PIN lock · shop logo on receipt · exchange-policy line · optional GST-invoice mode.

## Key decisions
- **Products = generic item-names, not SKUs.** Dropped (don't fit this workflow): barcode/article-code, per-product stock, per-product cost/profit, size & colour variants.
- **Quick-pick button grid:** skipped — keyboard entry is faster.
- Item entry stays one combined dialog.
- No GST breakup on bills (prices are GST-inclusive, shop's choice).
- Browser-based app that behaves like installed software — not a signed `.exe`.
- Number-code caveat: a plain price whose last digit matches a number-code digit is read as code + MRP; the live preview shows what it did.
