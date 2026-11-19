# Task 4 Printing Implementation Plan

> **For agentic workers:** Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Print an all-level furniture table and one plan page per viewable level, preserving screen state.

**Architecture:** PlanComponent maps plan page indexes to viewable levels in home order, fitting each level to one page. FurnitureTable constructs a print-only Level column and temporarily removes its furniture filter. HomePrintableComponent delegates without a selected-level filter and restores transient printing state on failure.

**Tech Stack:** Java 8, Swing Printable, Maven/JUnit 5, the application's existing iText PDF printer.

**Spec:** ASSIGNMENT.md, Task 4.

## Global Constraints

- Do not edit assignment-tests.
- Print furniture from every viewable level, with a Level column.
- Restore the originally selected level after successful, out-of-range, and failed rendering.
- Preserve on-screen Level column visibility and filters.
- Fit each viewable level to one plan page; preserve existing pagination for homes without levels.

## Review Focus

- Skip hidden levels; keep home order; include an empty viewable level's page.
- A home without levels retains its original printing behavior.
- Exceptions restore selected level, table filter, column model, grid color, and page format.
- Print-only Level column appears once whether or not already displayed on screen.
- Preview, PDF, headers, and repeated page requests remain consistent.

## Task: All-level printing

**Files:** swing/PlanComponent.java, FurnitureTable.java, HomePrintableComponent.java under SweetHome3D/src/com/eteks/sweethome3d/.

- [x] Run provided Task 4 test; confirm failure for the second plan page.
- [x] Map `PlanComponent.print` indexes to viewable levels and restore selection with try/finally.
- [x] Extend only the printable furniture columns with Level; print all viewable furniture and restore table state with try/finally.
- [x] Remove selected-level filtering from HomePrintableComponent and protect outer print state.
- [x] Verify the public suite and temporary checks for hidden/empty levels, exceptions, table contents, filters, and column preservation.
- [x] Generate the sample's four-page PDF using the application's actual printing path; render and inspect every page.
- [x] Obtain independent code review and run final build/submission checks.

## Execution record

- Task 3 code and user screenshots preserved in commit 8d5e3af; Task 4 branch is task4-print-all-levels.
- Use Latin-1 reads/writes where source encoding prevents apply_patch.
- Use the pdf skill to visually inspect generated acceptance evidence; do not substitute the provided reference PDF.

- Final verification: Maven package succeeded; all 6 public tests passed; test_submission.py passed; git diff --check passed.
- Supplementary checks: hidden and empty levels, no-level homes, negative/out-of-range pages, runtime and PrinterException restoration, all-level furniture contents, Level column visibility, worker-thread EDT safety, and effective scale/level headers passed.
- Independent review identified EDT mutation and stale configured scale headers; both were reproduced with failing checks, fixed, and re-reviewed with no remaining important findings.
- Acceptance PDF was generated from samples/MultiLevelHome.sh3d using the actual Swing view and HomePDFPrinter, not copied from the reference. All four rendered pages were inspected; furniture names, headers and Level values are visible.
- Local verification drivers and intermediate renders are under ignored .local/. GitHub Issue closure and remote integration remain outside the local implementation.
