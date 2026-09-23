# Assignment 03 — CHANGES

**Name:** Kyawt Kay Khine  **Student ID:** 6705140042

---

## 1 · What I changed

| # | Code smell in the original | What I changed it to | OOP concept applied | How I verified behaviour was unchanged |
|---|---|---|---|---|
| 1 | Products, orders, and order items were stored as nested tuples and accessed by indexes such as `o[0]` and `it[1]`. | Added `Product`, `OrderItem`, and `Order` objects with named attributes and methods; an `Order` has a customer and many items, and an `OrderItem` has a product. | Classes / composition | Ran `python Assignment_03_completed.py` → PASS. |
| 2 | Membership discount and points used repeated `if tier == ...` / `elif` chains. | Added `Customer`, `Silver`, `Gold`, and `Platinum` classes. Each tier supplies its own discount rate and points multiplier. | Inheritance / polymorphism | Ran the self-test → PASS; the output exactly matched the legacy output. |
| 3 | `calc()` mixed calculation logic with receipt printing. | Moved calculations into pure `Order` methods (`subtotal()`, `discount()`, `tax()`, `total()`, `points()`) and made `receipt()` responsible for building the receipt text. | Encapsulation / separation of concerns | Ran the self-test → PASS; no receipt line changed. |
| 4 | The original code used magic numbers such as `0.07`, `10`, and `0.03`, and used a leftover `global TAXRATE`. | Added named constants such as `TAX_RATE`, `BULK_QTY_THRESHOLD`, `BULK_DISCOUNT_RATE`, and `POINTS_DIVISOR`; the refactored calculations do not use a global statement. | Clean design / constants | Ran `python Assignment_03_completed.py` → PASS. |
| 5 | Product tax was calculated inside the order loop with a category check. | Added `Product.tax_rate()` and `OrderItem.tax()` so the product determines its own tax rate. | Encapsulation / responsibility | Ran the self-test → PASS; tax values and grand total remained identical. |

## 2 · Short reflection (4–6 sentences)

The biggest improvement was separating the store data into classes because the code is easier to understand and each object has a clear responsibility. The tier classes also removed the repeated membership `if/elif` chains and let polymorphism handle the different discount and points rules. I had to be careful not to change any business rules, especially the difference between subtotal values of 100 or less and values above 100. I also had to preserve the exact receipt formatting, rounding, item order, and blank lines. I verified the final program with the built-in self-test, which printed `PASS - behaviour is unchanged. Your refactor is safe.`

> The refactor was checked against the legacy output, so the goal was to improve the design without changing the program's behaviour.

## 3 · Prompt log (Level 2 — required)

| # | My prompt to the AI | What it suggested (summary) | Accept / reject / edited | How I checked it |
|---|---|---|---|---|
| 1 | "Make the necessary edits to the two provided files, insert the required answers and submit the file containing the correct answers." | Refactored the supplied store program into `Product`, `OrderItem`, `Customer` tier subclasses, and `Order`; added validation, named constants, pure calculation methods, receipt generation, and completed the written change/reflection/prompt-log sections. | Edited/accepted after checking the assignment requirements. | Ran `python Assignment_03_completed.py`; the built-in self-test printed `PASS - behaviour is unchanged. Your refactor is safe.` I also reviewed the refactored code against the required OOP concepts and the CHANGES checklist. |

**Ownership statement.** *By submitting, I confirm I understand and can explain every line of code I submitted, and that this prompt log reflects my actual AI use.*

---

## 4 · Before-you-submit checklist

- [x] `python Assignment_03_completed.py` prints **PASS**.
- [x] Refactored products, orders, and items are objects rather than tuple-based domain objects.
- [x] No `if tier == ...` chains are used for tier discount or points calculations.
- [x] Calculation methods **return** values and do not print; receipt printing is separate.
- [x] Constructors validate state; no leftover `global` statement; magic numbers are named.
- [x] The change table and reflection above are filled in.
- [x] The prompt log is complete and the ownership statement is ready for submission.
