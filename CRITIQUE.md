# Critique: reviewed as a Toast product designer

Product, UX and PM-level critique only. The UI and visual design are yours and stay as they are.

## Rating

| Area | Before | After fixes |
|---|---|---|
| Visual craft, Toast look and feel | 8 | 8 (unchanged on purpose) |
| Product framing vs. what Toast already ships | 3 | 7 |
| Inventory / accounting logic (receipt vs. bill) | 4 | 7 |
| AI judgment (confidence, uncertainty) | 6 | 8 |
| Safety of money actions | 4 | 7 |
| Honesty of claims | 5 | 8 |
| **Overall for this role** | **5.5 / 10** | **7.5 / 10** |

## What you got right
- One journey, end to end, in a UI that really feels like Toast's back office.
- Evidence highlighted on the paper; questions instead of codes.
- Roles with real limits: the receiver can't approve bills.
- Word labels like "Exact match · UPC matches" instead of numbers in the main UI.
- Rejecting the naive "98% everywhere" approach in the story.

## Product critique, and what was changed

1. **Pitched existing Toast features as the idea.** Toast already documents AI invoice scanning, import with mapping, and PO receiving.
   → The case study now has a "What Toast already does" note. The pitch is what happens *after* the read.
2. **The avocado case was a guess about handwriting, not a receiving problem.**
   → It's now a short delivery: ordered 2, received 1, billed 2. Stock keeps what arrived and $68.40 is held with a credit request.
3. **"Approve & send to books" implied approval adds stock.**
   → The button is now "Approve bill". The summary says stock came from the receipt and approval doesn't change it, and shows the held amount separately from what goes to QuickBooks.
4. **A 7-second undo was the safety model for money.**
   → Removed. Bulk approve now lists the bills, the zero open questions, that stock won't change, and how to correct after the sync. Approvals can be reopened until 2 AM; after that, corrections go through QuickBooks.
5. **Inbox tabs didn't add up to All.** Approved and synced invoices had no tab.
   → Added Approved and In QuickBooks tabs. Needs + Ready + Sync failed + Approved + In QuickBooks = All.
6. **Percentages still leaked into the mapping UI** ("Likely · 71%", "18%" candidates).
   → Words only. Evidence stays as the reason.
7. **Retry after a sync failure didn't say it was safe.**
   → The remap dialog now says the retry checks QuickBooks first, so a bill can't post twice.
8. **"WCAG 2.2 AA · 0 issues" was over-claimed** from one automated scan.
   → It now says what was checked and what wasn't.

## UX / UI audit (round 2): found and fixed

| Area | Issue | Fix |
|---|---|---|
| Decision card | Answers came before the evidence; the title was crushed into a narrow 4-line column | Title full width → ordered / received / billed → answers, on desktop and phone |
| Invoice paper | Line 14 read “2 1 rec’d CS” | “2 CS 1 rec’d”: quantity and unit stay together |
| Item mappings | Item names and match reasons cut off with “…” | Wrap to two lines; the evidence is always readable |
| Toast IQ panel | Pushed the page on laptops, so the inbox wrapped; sat under the top bar on phones | Overlays on laptops; full-screen sheet on phones |
| Toast IQ copy | To-do and answer still described the old handwriting question | Short-delivery wording everywhere |
| Toolbar | Search box pushed off the card when space was tight | Wraps at any width |
| Keyboard | Rows and cards had a button role but Enter/Space did nothing; links without `href` were unreachable | Enter/Space activate; links reachable by Tab |
| Screen readers | No main / navigation / header landmarks, an unnamed button, empty table headers, a skipped heading level, invalid ARIA | All fixed. axe-core is clean on 5 screens × 2 widths (automated scan only) |
| Responsive | Cramped below 1100px; sideways scroll on phones | Auto-collapsed rail, wrapping toolbars, stacked layouts; no sideways scroll at 375px |
| Icons | Phosphor set; thin, uneven weight across sizes | Hugeicons everywhere, at one optical weight (1.35–1.75px by size) |
| AI identity | Generic purple and an orb | One multicolor Toast IQ sparkle, with its colors on labels, borders, tints, buttons and hovers |

Case-study images are rebuilt with Stageshow (`../stageshow-shots/`, rerun `export-shots.sh`). Real prototype screens are recaptured with `capture-prototype.mjs`.

## Still open (only you can do these)
- Talk to 5–8 operators and bookkeepers before calling anything validated.
- Make the Figma file viewable by link.
- Run a VoiceOver pass and a full keyboard-only walkthrough, then update the accessibility card.
- `img/m1–m5.jpg` (iOS Figma screens) still use the old icon style; re-export them from Figma.
