# F110 — Automatic Payment Program

## What it does

F110 pays open vendor (and customer) items automatically: it selects the items due for payment, applies the payment method, and posts the payment documents. It is the last step of the P2P flow: PO → MIGO → MIRO → F110.

## Menu path

Accounting → Financial Accounting → Accounts Payable → Periodic Processing → Payments → F110

## Steps

1. **Parameters**: enter the run date, an identification (a name for this run), the company code, and the payment method (check, transfer, etc.).
2. **Free selection / vendor range**: limit the run to the vendors or the items you want to pay (or leave it open for all due items).
3. **Run the proposal first**: F110 first creates a payment proposal — a list of what it would pay and what it would skip, with the reasons.
4. **Review the proposal log**: check the exceptions (items not paid and why: blocked invoices, missing bank data, payment terms not yet due, amounts below the minimum).
5. **Run the payment run**: only when the proposal looks right. F110 posts the payment documents and clears the open vendor items.
6. **Check the results**: payment list, accounting documents, and the vendor open items in FBL1N to confirm the clearing.

## Proposal vs. payment run

- The **proposal run** only simulates: nothing is posted. Review it, fix the exceptions, and run it again if needed.
- The **payment run** posts the payments. It cannot be undone by re-running — corrections go through manual clearing or reversals.

## Common exceptions

- **Invoice blocked (MIRO)**: fix the block in MRBR first; F110 will not pay blocked items.
- **Payment terms not due**: the item is not due yet — it will be picked up in a later run.
- **Missing bank details**: the vendor master data has no bank account — complete it before the run.
- **Payment method not allowed for the vendor**: check the vendor master data and the payment method configuration.

## Tips

- Never skip the proposal review. The proposal log is where you catch the mistakes before money moves.
- Run F110 on a fixed schedule (for example, weekly) and keep the run identification consistent so the runs are easy to trace.
- After the payment run, reconcile the bank statement against the payments posted — that is the bank reconciliation step that closes the loop.
- Keep the proposal log and the payment list with the month-end close documentation.
