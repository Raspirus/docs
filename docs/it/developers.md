# DEVELOPERS

## Navigating the Architecture

![Raspirus Architecture Graph](link_to_graph_image)

Raspirus is structured into two integral components: frontend and backend. These components, built using distinct languages and frameworks, are interconnected via a third-party framework called [Tauri](https://tauri.app/). This framework not only facilitates communication between the frontend and backend but also enables us to incorporate Rust functions into the frontend. Furthermore, Tauri empowers the distribution of Raspirus across various operating systems.

## Starting Your Development Journey

=== "Windows" An in-depth guide for Windows users is currently in the works.

     - Stay tuned for updates.

=== "Linux" If you're using Linux, follow the provided Makefile for a seamless start.

     - Utilize the provided Makefile for guidance.

=== "macOS" Detailed instructions for macOS users are coming soon.

     - Keep an eye out for upcoming information.

Should you encounter any hiccups during your initial run or build, ensure that you've followed each step diligently. Confirm the accurate creation of both logs and config files.

## Exploring the Backend

![Backend Structure Graph](link_to_backend_graph_image)

The backend, an essential cog in the Raspirus machinery, is meticulously crafted in Rust for superior performance. The primary file houses functions accessible from the frontend, which must yield JSON-compatible outcomes. For a detailed breakdown, reference the graph above outlining the backend's modular arrangement.

## Unpacking the Frontend

![Frontend Structure Graph](link_to_frontend_graph_image)

Our frontend, developed with JavaScript via the Next.js framework, emphasizes user-friendliness and functionality. Comprising components and pages, it mirrors the simplicity and robustness of Next.js. Refer to the illustrated graph above for an approximate visual representation of the frontend's architecture.

## Evaluating Test Coverage

- Backend tests, authored in Rust, can be executed via the `cargo test` command. Access these tests in the [tests directory](https://github.com/Raspirus/Raspirus/tree/main/src-tauri%2Fsrc%2Ftests). Check test coverage on [Codecov](https://app.codecov.io/gh/Raspirus/Raspirus).
- Frontend tests, created with Selenium, are currently in development.

Thank you for your interest in contributing to Raspirus's development. Your expertise fuels our progress.