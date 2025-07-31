AI request:
Give me a list of the features I wrote about formatted as though they were being given to a programming team, a list of the recommended tools (including things like which IDE I might use) I would use to build said program, as a website only but with the plan of taking it bigger later, recommended programming languages, and anything else I should have in place to build this software. Also, give me a list of the recommended classes I should include in this program. For this project, I will build tests for all code. Give your recommendations following the best coding practices that result in the highest quality code over the long term. 

Ministering Project Requirements and Recommendations
Feature Requirements
Data Management
    • Local Data Storage: All data must remain on the end user's computer, with no external data transmission.
    • Password Protection: Option to password-protect data for security.
    • Import Functionality: Ability to import a list of names to populate individuals in the system.
    • Export and Print: Export ministering assignments as a printable list or segmented lists for emailing to companionship members or district leaders.
Card-Based Interface
    • Individual Cards:
        ○ Two cards per individual: Minister card (white for adults, pink for youth) and Individual card (green).
        ○ Minister cards can be dragged to form companionships or added to existing ones.
        ○ Individual cards can be dragged to form families or added to ministering assignments.
    • Family Cards:
        ○ Support families of one or more individuals.
        ○ Created by dragging individual cards together or via a dedicated button.
    • Companionship Cards:
        ○ Default to two individuals, with the ability to add more.
        ○ Created by dragging one minister card onto another or via a dedicated button.
    • Ministering Assignment Cards:
        ○ Created by dragging a family or individual card onto a companionship card.
    • District Organization:
        ○ Board divided into districts, each with an assigned leader.
        ○ Ministering assignment cards can be dragged into districts to assign them.
Drag-and-Drop Functionality
    • All cards (individuals, families, companionships, ministering assignments) are draggable.
    • Dragging cards together combines them (e.g., individuals into families, ministers into companionships, families into assignments).
    • Dragging cards apart disassembles them (e.g., removing an individual from a family or companionship).
Notes
    • Add notes to individuals, families, companionships, or districts.
Output
    • Automatically organize districts into printable lists on standard paper.
    • Segment lists for emailing to companionship members or district leaders.
Scalability and Standards
    • Build as a website with enterprise-grade quality.
    • Plan for future integration with tools for the Church of Jesus Christ of Latter-day Saints.
    • Include comprehensive unit and integration tests for all code to ensure reliability.
Recommended Tools
Programming Languages
    • JavaScript (with TypeScript): For type safety, better code organization, and enterprise-grade development.
    • HTML/CSS: For structuring and styling the web interface.
    • No backend language: Since all processing is local, no server-side language is needed initially.
Frameworks and Libraries
    • React with TypeScript: For building a component-based, scalable UI with drag-and-drop support.
    • React-DnD: For drag-and-drop functionality, supporting complex interactions like card combining and separation.
    • Tailwind CSS: For responsive, utility-first styling of the interface.
    • Dexie.js: For local IndexedDB storage, enabling structured data management in the browser.
    • CryptoJS: For client-side encryption to support password-protected data.
    • html2pdf.js: For generating printable PDF lists from the web interface.
    • Vite: For fast development and optimized production builds.
Development Tools
    • IDE: Visual Studio Code (VS Code)
        ○ Extensions: ESLint, Prettier, TypeScript, React Snippets, Tailwind CSS IntelliSense.
    • Version Control: Git with GitHub for source control and collaboration.
    • Testing Frameworks:
        ○ Vitest: For fast unit testing with TypeScript support.
        ○ React Testing Library: For testing React components.
        ○ Cypress: For end-to-end testing of the web application.
    • Linting and Formatting:
        ○ ESLint: For JavaScript/TypeScript code quality.
        ○ Prettier: For consistent code formatting.
    • Build Tool: Vite for development and production builds.
    • Package Manager: npm for dependency management.
Other Tools
    • Figma: For designing the UI/UX of the board and card system.
    • JSDoc: For documenting code to maintain clarity for future enterprise integration.
Recommended Classes/Interfaces (TypeScript)
Core Data Models
    • Individual:
        ○ Properties: id, name, isYouth, notes.
        ○ Represents a person with minister and individual cards.
    • Family:
        ○ Properties: id, name, members (array of Individuals), notes.
        ○ Manages a group of individuals as a family unit.
    • Companionship:
        ○ Properties: id, members (array of Individuals), notes.
        ○ Represents a ministering companionship (default two members).
    • MinisteringAssignment:
        ○ Properties: id, companionship, family (or Individual), notes.
        ○ Links a companionship to a family or individual.
    • District:
        ○ Properties: id, name, leader (Individual), assignments (array of MinisteringAssignments), notes.
        ○ Organizes ministering assignments under a leader.
UI Components
    • Card:
        ○ Properties: id, type (individual, minister, family, companionship, assignment), data, draggable.
        ○ Base component for all draggable cards.
    • Board:
        ○ Properties: districts, unassignedCards.
        ○ Manages the layout and drag-and-drop interactions.
    • DistrictPanel:
        ○ Properties: district, cards.
        ○ Displays a district and its assigned cards.
    • NoteEditor:
        ○ Properties: entity (Individual, Family, Companionship, District), onSave.
        ○ Handles note creation and editing.
Utility Classes
    • DataManager:
        ○ Methods: importNames, exportAssignments, saveData, loadData, encryptData, decryptData.
        ○ Manages local storage and data operations.
    • PrintManager:
        ○ Methods: generatePrintableList, generateEmailSegments.
        ○ Handles printing and email segmentation.
Best Practices for High-Quality Code
    • Type Safety: Use TypeScript interfaces for all data models and components to prevent runtime errors.
    • Modular Architecture: Organize code into reusable React components and utility modules.
    • Testing:
        ○ Write unit tests for all utility functions and components using Vitest and React Testing Library.
        ○ Write end-to-end tests with Cypress to simulate user interactions (e.g., dragging cards, creating assignments).
        ○ Aim for >90% test coverage.
    • Code Quality:
        ○ Enforce ESLint rules for consistent code style and error prevention.
        ○ Use Prettier for automatic code formatting.
        ○ Follow React best practices (e.g., functional components, hooks, memoization).
    • Documentation:
        ○ Use JSDoc for all functions and components.
        ○ Maintain a README with setup, usage, and testing instructions.
    • Security:
        ○ Implement client-side encryption with CryptoJS for password-protected data.
        ○ Validate all imported data to prevent injection attacks.
    • Performance:
        ○ Use React.memo and useCallback to optimize rendering.
        ○ Index data in Dexie.js for fast queries.
    • Scalability:
        ○ Design components to be reusable for future integration with Church tools.
        ○ Use a modular folder structure (e.g., components/, utils/, models/).
    • Accessibility:
        ○ Ensure the UI is keyboard-accessible for drag-and-drop and navigation.
        ○ Use ARIA attributes for screen reader support.
Additional Recommendations
    • Project Structure:
ministering-project/
├── src/
│   ├── components/
│   │   ├── Card.tsx
│   │   ├── Board.tsx
│   │   ├── DistrictPanel.tsx
│   │   └── NoteEditor.tsx
│   ├── models/
│   │   ├── Individual.ts
│   │   ├── Family.ts
│   │   ├── Companionship.ts
│   │   ├── MinisteringAssignment.ts
│   │   └── District.ts
│   ├── utils/
│   │   ├── DataManager.ts
│   │   └── PrintManager.ts
│   ├── tests/
│   │   ├── components/
│   │   ├── utils/
│   │   └── e2e/
│   └── App.tsx
├── public/
├── package.json
├── vite.config.ts
├── tsconfig.json
├── .eslintrc.json
├── .prettierrc
└── README.md

    • Development Workflow:
        ○ Use Git branching (e.g., main, develop, feature branches).
        ○ Implement CI/CD with GitHub Actions for automated testing and linting.
    • Future Considerations:
        ○ Plan for offline support using Service Workers.
        ○ Design APIs for potential future integration with Church systems, even if local-only for now.
    • Testing Strategy:
        ○ Unit tests for all model methods and utility functions.
        ○ Integration tests for component interactions (e.g., drag-and-drop).
        ○ End-to-end tests for key workflows (e.g., creating a companionship, assigning a family, printing a list).

From <https://grok.com/chat/df4cab3e-9c98-40c2-9da1-d0b7f4955374> 

