# MIRO — Invoice Verification

## What it does

MIRO verifies a vendor invoice against the purchase order and the goods receipt — the three-way match. If everything matches, it posts the vendor liability and clears the GR/IR account. If something does not match, SAP blocks the invoice.

## Menu path

Logistics → Materials Management → Logistics Invoice Verification → Invoice Verification → MIRO

## Steps

1. Enter the invoice date, the vendor invoice number and the gross amount.
2. Reference the purchase order (enter the PO number) so SAP pulls the PO items and the goods receipts.
3. Check the amounts, quantities and tax code line by line.
4. Post. SAP creates an accounting document (and a material document if there are stock postings). Save the invoice document number.
5. If the invoice is blocked, find out why before paying anything (see below).

## The three-way match

SAP compares three things:

- **Purchase order** — what was ordered and at what price.
- **Goods receipt (MIGO)** — what actually arrived.
- **Invoice** — what the vendor charged.

If price or quantity differ beyond the tolerance limits, the invoice is blocked for payment.

## Common blocks

- **Price variance**: the invoice price is higher than the PO price. Check the PO and the vendor's price list; ask the buyer to correct the PO or the vendor to correct the invoice.
- **Quantity variance**: the invoice quantity is higher than the quantity received. Check the goods receipt in MIGO — only pay for what arrived.
- **Missing goods receipt**: the invoice arrived before the goods. Wait for the receipt or check whether the goods were received under a different PO item.
- **Tax code wrong**: the tax code on the invoice does not match the PO. Correct it before posting.

## Payment block R: quantity discrepancy

If your SAP configuration uses payment block **R** for an invoice variance, confirm the block reason in your system; payment-block keys can vary by configuration. For example, the supplier invoices 6 packages but only 5 were received. Do not pay the invoice or post a receipt for goods that have not arrived.

1. In **ME21N**, check the PO item, ordered quantity and price.
2. In **MIGO**, compare the posted goods receipt with the delivery note and the quantity physically received. Keep the receipt accurate; follow your local correction process if it was posted incorrectly.
3. Contact **Purchasing** to reconcile the PO, receipt and invoice. If the sixth package is still owed, ask Purchasing to arrange delivery with the supplier. If it will not be delivered, have Purchasing request a corrected invoice or credit note from the supplier.
4. In **MIRO**, verify or correct the invoice according to your company's process once the discrepancy is resolved.
5. In **FBL1N**, check that the vendor item remains blocked until resolution. Use **MRBR** to release it only after the discrepancy is resolved and the invoice is approved under your local process.

## Tips

- Use **MRBR** to release blocked invoices once the difference is resolved.
- Use **FBL1N** to check the vendor's open items and confirm the invoice posted.
- Never pay a blocked invoice — it is blocked for a reason. Fix the difference first.
- Keep the invoice document number with the vendor invoice number: that pair is what you will trace in F110 and in the month-end close.
