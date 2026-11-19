# Task 3 Volume Implementation Plan

> **For agentic workers:** Use superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox syntax for tracking.

**Goal:** Display calculated furniture volume and expose ascending/descending sorting and column visibility controls.

**Architecture:** Follow Height through the existing furniture model, table, controller actions, and shared menu builders. Calculate volume from current dimensions rather than storing it.

**Tech Stack:** Java 8, Swing, Maven, JUnit 5.

**Spec:** ASSIGNMENT.md, Task 3.

## Global Constraints

- Do not edit assignment-tests.
- English-only UI updates are sufficient.
- Volume equals width * depth * height; use the application's existing length-based number formatting.
- Preserve existing homes' saved column selections; show Volume by default for new homes.

## Review Focus

- Resizing furniture updates rendered volume and sorting.
- Equal volumes compare equally; descending sorting reverses the order.
- Hiding and showing Volume restores its intended position after Height.
- Both menu bar and context menus expose the same actions and selected state.
- Existing home files can save and reopen Volume visibility and sorting.

## Task: Add calculated volume throughout the existing property path

**Files:** model/PieceOfFurniture.java, CatalogPieceOfFurniture.java, HomePieceOfFurniture.java, Home.java; viewcontroller/HomeView.java, HomeController.java, FurnitureController.java; swing/FurnitureTable.java, HomePane.java, package.properties (all under SweetHome3D/src/com/eteks/sweethome3d/).

- [x] Run the provided volume tests and confirm missing API, column, and actions fail.
- [x] Add `float getVolume()` to the furniture interface and both implementations; add `SortableProperty.VOLUME` and its comparator.
- [x] Add Volume to new-home defaults and controller column ordering.
- [x] Add the header, width, renderer, and copied-table value using the existing length format.
- [x] Add enabled sort/display actions and wire the shared menu builders, English labels, and tooltips.
- [x] Run all provided tests; only the unfinished Task 4 printing test may fail.
- [x] Check rendering, resizing, both sort directions, visibility, resources, and serialization using a temporary local verification program.
- [x] Review the complete diff, then launch for manual screenshot acceptance.

## Execution record

- Task 2 screenshot is an existing untracked user file; preserve it.
- Work is isolated on branch task3-volume in the current checkout to preserve the existing local Java/Maven installation.
- GitHub Issue creation and screenshot capture require an available external/UI connection; report any concrete blockers.

- Verification: public suite 5/6 pass; the sole failure is unfinished Task 4 (`planPrintingIncludesEveryLevelAndRestoresSelection`). Temporary local checks passed for rendering, resizing, sorting, visibility, serialization, and resources. Independent review reported no findings.
- Manual acceptance remains: capture the populated Volume column and a Volume menu control in submissions/task3-volume.png, then finish the GitHub Issue workflow.
