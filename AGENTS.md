# Agent Guide

This repository contains a TinTin++ client configuration specifically tailored for the **Nukefire** MUD.

## Project Structure

- **Entry Point**: `nuke.tin` is the main entry point. Always start here when tracing execution flow.
- **Modules**: Located in `modules/`.
    - **Core**: `modules/nukefire.tin` is the primary module for Nukefire-specific logic.
    - **Sub-modules**: `modules/nukefire/` contains specialized components (e.g., `combat.tin`, `map.tin`).
    - **Shared**: `modules/events.tin`, `modules/functions.tin`, `modules/syslog.tin` are shared utilities.
- **Libraries**: Located in `lib/`. `modloader.tin` handles the dynamic module loading system.

## Key Conventions

1.  **Nukefire Priority**: This project supports multiple MUDs, but the current focus is **Nukefire**.
    -   **Relevant**: Files with `nuke` in the name (e.g., `nuke.tin`, `nukefire.tin`, `mapnuke.tin`).
    -   **Irrelevant**: Files related to "Kallisti" (e.g., `main.tin`, `kallisti.tin`, `modules/kallisti/`). **Do not modify or reference these unless explicitly instructed.**

2.  **Module System**:
    -   Modules are loaded using `load_module <name>`.
    -   The `modloader` (in `lib/modloader.tin`) manages dependencies and registration.
    -   Modules typically register themselves using `register_module` or `nukefire-register`.

3.  **Event Driven**:
    -   The project relies heavily on events (`modules/events.tin`).
    -   Look for `event_raise` and `event_register` patterns.

## Development Guidelines

-   When adding new functionality, prefer creating a new module in `modules/nukefire/` and loading it from `modules/nukefire.tin`.
-   Ensure all new code is compatible with TinTin++ syntax.
-   Respect the existing variable naming conventions (mostly snake_case).
