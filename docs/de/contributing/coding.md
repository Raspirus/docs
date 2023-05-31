---
comments: wahr
---

# Code Contributions

Contributions to the codebase are always welcome and highly valued in the development of Raspirus, a powerful virus scanner. If you're interested in contributing code, please take a moment to familiarize yourself with our [Guidelines](CODE_OF_CONDUCT.md) before opening a pull request. Additionally, we recommend exploring the coding practices and standards outlined in the [Developer section](/developers/index.md) for a comprehensive understanding of our project's structure and requirements.

## Contributing to the Frontend

The frontend of Raspirus is built using the Next.js framework and leverages JavaScript for its implementation. To maintain a clean and efficient codebase, we prioritize modularizing components and ensuring that pages remain uncluttered with unnecessary code. Each page represents a distinct screen within the app and can be accessed either through manual routing or as a result of specific user actions, such as clicking a button or being redirected after the completion of a loading process.

When contributing to the frontend, consider the following guidelines:

- Emphasize clean and intuitive user interfaces, allowing users to navigate the app effortlessly.
- Utilize the Next.js structure effectively, leveraging the power of components for enhanced maintainability and reusability.
- While the frontend is currently developed exclusively in JavaScript, we remain open to migrating to TypeScript in the future.

Your contributions to the frontend will significantly impact the user experience of Raspirus, making it more accessible and user-friendly.

## Adding to the Backend

The backend of Raspirus is implemented in Rust, a high-performance programming language renowned for its speed and reliability. By utilizing Rust, we achieve faster scanning speeds and enhance the overall robustness of the application. The backend interacts with a sizable database, locally storing hashes, and communicates responses via the Tauri API.

If you're interested in contributing to the backend, consider the following points:

- Familiarize yourself with Tauri, a framework that facilitates the integration of Rust and JavaScript, enabling seamless communication between the frontend and backend.
- Explore Rust's features and capabilities, which provide an efficient and secure foundation for the virus scanning process.
- Although learning Rust and Tauri might seem daunting at first, with a little practice, you can quickly grasp the concepts and contribute effectively to the backend development.

Contributing to the backend of Raspirus will help improve its scanning capabilities and ensure the reliability of the application.

We appreciate your interest in contributing code to Raspirus, and we look forward to your valuable contributions that will help make our project even better.