# Shiftwell Swap Rules: prototype

**Live demo:** https://abhiready.github.io/shiftwell-swap-rules/main.html

A working prototype built for a product case study. Shiftwell (a fictional company) sells shift-scheduling software to restaurants, clinics, retail stores and gyms.

## The problem

Three customers asked for three different features:

- **FreshBowl:** approve shift swaps on WhatsApp
- **CarePoint Clinics:** block staff with expired certificates
- **UrbanMart:** require regional approval past 48 hours a week

The data showed one underlying problem: **every swap waits for a manager to approve it by hand.** Every account approving fewer than 42% of swaps within 24 hours was at risk or already lost.

## The solution: one rules engine

Instead of three one-off features, every swap is checked against rules the customer's Admin sets:

| Check | If it fails |
|---|---|
| Colleague is trained for the role or station | Sent to the Location Manager |
| Required certificates are valid on the shift date | Blocked (managers can't override) |
| Weekly hours stay within the limit (e.g. 48) | Sent to an approver, or blocked |

If every check passes, the swap is **approved instantly**.

![Overview](screenshots/overview.png)

## What you can try

1. **Switch customers:** FreshBowl, CarePoint and UrbanMart each have their own rules.
2. **Check a swap:** pick a shift and a colleague to see the decision and the reason for each check.
3. **Turn off auto-approval:** see how Shiftwell works today, with every swap waiting for a manager.
4. **Replay a month:** run 300 sample swaps through the rules to see how many still need a person.
5. **Decision log:** every decision is recorded with its reason, for compliance audits.

| Sent for approval | Blocked |
|---|---|
| ![Sent for approval](screenshots/sent-for-approval.png) | ![Blocked](screenshots/blocked.png) |

![Replay a month](screenshots/replay.png)

## Result

At FreshBowl, about **73% of swaps are approved automatically**, cutting manual approvals from about 2,900 to about 700 a month.

## Notes

- Staff, shifts and the replayed month are **sample data**, not real customer data.
- Monthly swap volumes come from the case study's data pack.
- Assumes a manual approval takes a manager about 2 minutes.

## What a real version would need

- Certificate and station-training fields with expiry dates on staff profiles
- A rules service called on every swap and roster publish
- Rule settings per customer for Admins, and an approver role
- Notifications, manager override with a reason, and a tamper-proof decision log
- A feature flag to pilot with one customer first

## Built with

HTML, CSS and JavaScript in a single page, with no backend. Built with help from Claude (Anthropic) for the prototype code; the analysis and product decisions were tested and verified by me.

**Author:** Abhishek Reddy · [GitHub](https://github.com/Abhiready) · [LinkedIn](https://www.linkedin.com/in/abhishek-reddy-pm/)
