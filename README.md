# Alan Abraham - ePortfolio

Welcome to my professional ePortfolio. This was developed as the capstone for my BSc Computer Science at Southern New Hampshire University. My focus is on high-performance systems engineering, bare-metal game engine architecture, and robust application development.

## Professional Self-Assessment

TODO:

## Code Review

An initial professional code review assessing existing software architecture and identifying areas for algorithmic and structural enhancement.
[Code Review](https://youtu.be/edd7aiS1Zto)

## Artifact I: Software Design and Engineering

**Project:** Milestone: Weight Tracking Android Application  
**Description:** A mobile application originally developed for CS360: Mobile Architecture and Programming, demonstrating modern Android architecture, decoupled models, and asynchronous coroutine flows.
**Enhancement:** The original application was designed using Java, which, while foundational, has largely been superseded by Kotlin in modern Android development. Transitioning the codebase to Kotlin allowed me to demonstrate industry-standard practices, including null-pointer safety, reduced boilerplate (via Kotlin data classes rather than manual getters and setters), and native asynchronous execution using Coroutines. The most significant software engineering improvement was the architectural restructuring of the application. The original artifact suffered from a “God Activity” anti-pattern, where the Android Activity acted as both the View and the Controller, resulting in tight coupling. To resolve this, I implemented the Model-View-Intent (MVI) architecture. I introduced feature-specific ViewModels (e.g., AuthViewModel, GoalViewModel), decoupling the UI from the business logic. Furthermore, I implemented Kotlin Flows to establish a reactive programming paradigm. Instead of the UI manually requesting data updates, it now observes a continuous, unidirectional data stream from the data layer. Beyond the initial plan, I extended the refactoring to include strict layer separation. I divided the classes into distinct Data, Domain, and Presentation layers. This modular architecture minimizes dependency circulation, sets a clear path for future Dependency Injection implementation, and makes the application highly testable.

- [Milestones](https://github.com/alan-j316/milestones)

## Artifact II: Algorithms and Data Structures

**Project:** ABCU Course Manager  
**Description:** A console-based C++ application originally developed for CS-300. The architecture was restructured from an O(log N) Binary Search Tree to an O(1) `std::unordered_map` hash table to optimize runtime performance for high-frequency lookups, alongside a C++17 `<filesystem>` upgrade for robust validation.
**Enhancement:** The primary enhancement involved replacing a custom-built Binary Search Tree (BST) with a hash table implementation using `std::unordered_map`. The original BST yielded O(log N) lookups, which was a bottleneck for the application's most frequent operation. Additionally, the BST relied heavily on recursive traversal for sorted printing, which introduced theoretical risks of stack overflow crashes at high call depths. Transitioning to a hash map reduced insertion and lookup time complexities to near O(1). This architectural shift also allowed for the removal of a redundant `std::unordered_set` that was previously required to cache and filter invalid prerequisites for the BST. By streamlining the data flow, data structure redundancy was eliminated. Beyond the core algorithmic improvements, the application was upgraded to the C++17 standard to leverage `std::string_view` for efficient string parsing and the `std::filesystem` library for robust error handling. Quality-of-life guardrails were implemented, including runtime file existence checks and an automatic fallback to a default CSV file, preventing hard crashes upon faulty user input.

- [ABCU Course Manager](https://github.com/alan-j316/abcu_course_manager)

## Artifact III: Databases

**Project:** Milestones: Weight Tracking Android Application (Database Migration)  
**Description:** An enhancement of the local data persistence layer, migrating from raw SQLite to the Room framework to establish a robust Single Source of Truth, ensuring thread-safe database operations.
**Enhancement:** A significant component of this enhancement involved data structuring and model decoupling. Previously, the application was tightly coupled to a single data model, making it brittle and difficult to maintain if the database schema or external data sources changed. To improve this, I completely redesigned the architecture to isolate the Room entity classes strictly to the data and repository layers. When data exits this layer, it is mapped to a pure Kotlin domain model devoid of any database logic, ensuring decoupled and independent schema migrations. Additionally, I refactored the database operations to utilize Kotlin Coroutines (suspend functions) and reactive Flow streams. Because database I/O operations are expensive and often cause UI stuttering if executed on the main thread, adopting this reactive, multi-threaded architecture ensures a fluid user interface while automatically emitting updated states without requiring constant, manual database querying.

- [Milestones](https://github.com/alan-j316/milestones)
