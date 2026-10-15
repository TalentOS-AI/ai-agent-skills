# Examples: state-path-tool-menus

Both examples work on paper or with a small script over your tool schemas. Numbers in SKILL.md (ToolBench 0.737 → 0.898; 32 vs 128 tools) are paper-reported and do not carry over to your stack; measure your own.

## Example 1: Receipt email with only an order_id

**Input prompt**
> Using state-path-tool-menus: my agent has 40 tools. The user says "email me the receipt for order 1234". Visible state: `order_id`. Tools include `send_receipt_email(email, receipt_pdf)`, `get_order(order_id) -> customer_id, items`, `get_customer(customer_id) -> email`, `render_receipt(order_id) -> receipt_pdf`, plus unrelated tools. Build an 8-tool menu and explain the order.

**Expected behavior**
- Traces the state path: `order_id` → `get_order` → `get_customer` (email) and `render_receipt` (pdf) → `send_receipt_email`.
- Orders producers before the consumer, and the first tool can be called with the visible state.
- Uses the remaining slots for route coverage, not near-duplicate tools.

**Acceptance checks**
- [ ] `send_receipt_email` is in the menu but after its producers (SKILL.md acceptance test 1).
- [ ] The first tool's required inputs are all visible (acceptance test 2).

## Example 2: A/B plan for an MCP gateway

**Input prompt**
> With state-path-tool-menus, plan an A/B test for our MCP gateway (3 servers, over 100 tools). The task class is "research a question, fetch sources, cite them". Compare a relevance-only menu to a state-path menu.

**Expected behavior**
- Keeps the same agent and call budget, and changes only the menu builder.
- Logs `menu_ids`, `menu_order`, `path_roles`, and whether the first call was schema-feasible.
- Measures executable-entry rate, complete-chain coverage@k, and producer-before-consumer violations, plus task success.
- Keeps high-impact tools behind permission checks.

**Acceptance checks**
- [ ] The state-path menu contains search, fetch, and cite in that order (acceptance test 4).
- [ ] The plan says the result must be measured locally and does not reuse the paper's numbers as a promise.
