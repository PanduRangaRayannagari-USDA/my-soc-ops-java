# Soc Ops Project Guidelines

## Development Checklist

Before finishing a code change:

1. Run the relevant tests.
2. Run `cd socops && ./mvnw clean package` for build-impacting changes.
3. Confirm the application starts with `cd socops && ./mvnw spring-boot:run` when runtime behavior changes.
4. Keep changes focused and update related documentation when behavior or workflows change.

## Architecture

- This is a Spring Boot 3.4.2 application targeting Java 21.
- The application entry point is `socops/src/main/java/com/socops/SocOpsApplication.java`.
- Keep game rules and board construction in `com.socops.service` and `com.socops.model`; keep HTTP concerns in `com.socops.web`.
- The web UI is a Thymeleaf template in `socops/src/main/resources/templates/game.html`, with static assets under `socops/src/main/resources/static`.
- Preserve the existing browser-facing behavior and REST contract when changing backend or template code.

## Code Style

- Follow existing Java naming, package structure, and Spring conventions.
- Prefer small, typed methods and existing domain types over duplicated logic or unchecked casts.
- Keep CSS changes in `socops/src/main/resources/static/css/app.css` and compose the utility classes documented in `.github/instructions/css-utilities.instructions.md`.
- Follow `.github/instructions/frontend-design.instructions.md` for UI work.

## Design Guide

- Treat `game.html` as a focused game interface: preserve clear board state, readable controls, and responsive behavior across desktop and mobile layouts.
- Build visual hierarchy with the existing CSS utilities and theme variables instead of introducing a new styling framework or scattered inline styles.
- Prefer a distinctive, cohesive visual direction over generic dashboard patterns; use typography, color, spacing, and subtle motion intentionally.
- Keep animations purposeful and lightweight, with CSS-first transitions that do not interfere with gameplay or accessibility.
- Verify UI changes in a running application and preserve keyboard access, readable contrast, and visible selected or marked states.
- See `.github/instructions/frontend-design.instructions.md` for the visual direction and `.github/instructions/css-utilities.instructions.md` for available styling utilities.

## Build and Test

- Use the Maven Wrapper from the `socops` directory:
  - `./mvnw clean package`
  - `./mvnw test`
  - `./mvnw spring-boot:run`
- Tests are under `socops/src/test/java` and use Spring Boot's test dependencies.
- The default development server runs on port 8080.
- Read `README.md` and `workshop/GUIDE.md` for the user-facing project workflow.
