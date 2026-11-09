# MIGO — Goods Receipt

## What it does

MIGO posts a goods receipt against a purchase order. It increases stock, creates a material document, and posts the goods receipt / invoice receipt (GR/IR) accounting entry. No invoice is needed at this step.

## Menu path

Logistics → Materials Management → Inventory Management → Goods Movement → Goods Receipt → MIGO

## Common movement types

- **101** — Goods receipt for a purchase order (the usual one)
- **102** — Reversal of a goods receipt
- **103** — Goods receipt into blocked stock
- **105** — Release from blocked stock

## Steps

1. Enter the movement type (usually 101) and the purchase order number.
2. Check the PO items, quantities and plant / storage location.
3. Enter the quantity received and the batch, if the material is batch-managed.
4. Post. SAP creates a material document number — save it: it is the proof of receipt and the reference MIRO will use.
5. Check the stock in MMBE and the document in MB51 if you need to trace it.

## What gets posted

- Stock increases by the received quantity.
- Accounting: inventory (debit) against GR/IR (credit). The GR/IR account clears later, when MIRO posts the invoice.

## Common problems

- **Quantity does not match the PO**: check the PO quantity and the delivery note before posting; post only what physically arrived.
- **Wrong movement type**: a 101 posts stock as unrestricted; if the goods are damaged or pending quality check, use blocked stock (103) instead.
- **PO not released**: the PO must be released/approved before you can post the receipt.
- **Wrong plant or storage location**: stock lands in the wrong place and the next counts will not match.

## Tips

- Always keep the material document number — it is the link between the receipt, the invoice and the payment.
- If a receipt was posted by mistake, reverse it with movement type 102 (or MBST to cancel the material document) instead of posting a second receipt.
