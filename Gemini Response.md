AI request:
Give me a list of the features I wrote about formatted as though they were being given to a programming team, a list of the recommended tools (including things like which IDE I might use) I would use to build said program, as a website only but with the plan of taking it bigger later, recommended programming languages, and anything else I should have in place to build this software. Also, give me a list of the recommended classes I should include in this program. For this project, I will build tests for all code. Give your recommendations following the best coding practices that result in the highest quality code over the long term. 

This is an excellent, detailed concept for a ministering assignment management tool! Building this as an enterprise-grade web application with an eye toward future integration is a strong approach.
Here's a breakdown of your request, structured for a programming team, along with recommendations:

Ministering Project: Digital Assignment Board
Project Goal: To create a digital, interactive web application that streamlines the process of managing ministering assignments within The Church of Jesus Christ of Latter-day Saints, providing a highly visual, drag-and-drop interface with robust data management, reporting, and security features.

I. Feature List for Programming Team
This section outlines the core functionalities, user interactions, and system requirements.
A. Core Data Structures & Relationships:
    1. Individuals:
        ○ Basic information (Name).
        ○ Ability to add notes to each individual.
        ○ Each individual can exist as:
            § An "Individual Card" (for families).
            § A "Minister Card" (for companionships).
    2. Families:
        ○ Composed of one or more "Individual Cards."
        ○ Ability to add notes to each family.
        ○ Represented as a draggable "Family Card."
    3. Companionships:
        ○ Composed of two or more "Minister Cards" (defaulting to 2).
        ○ Ability to add notes to each companionship.
        ○ Represented as a draggable "Companionship Card."
    4. Ministering Assignments:
        ○ Created by dragging an "Individual Card" or "Family Card" onto a "Companionship Card."
        ○ Represents the assigned ministering pair(s) to individuals/families.
        ○ Ability to add notes to each ministering assignment.
        ○ Represented as a draggable "Ministering Assignment Card."
    5. Districts:
        ○ Divisions of the main board.
        ○ Each district has one "Individual Card" designated as the person in charge.
        ○ "Ministering Assignment Cards" can be dragged into districts to assign them.
        ○ Ability to add notes to each district.
        ○ Represented as a visual section on the board.
B. User Interface & Interaction:
    1. Digital Board:
        ○ A primary canvas for organizing assignments.
        ○ Visually represents districts and allows for dynamic rearrangement of cards.
    2. Card System (Drag-and-Drop Functionality):
        ○ All "Individual," "Family," "Minister," "Companionship," and "Ministering Assignment" cards must be draggable.
        ○ Creating Companionships:
            § Drag one "Minister Card" on top of another "Minister Card" to form a "Companionship Card."
            § Alternatively, a "Create Companionship" button can be used, then "Minister Cards" dragged into it.
            § Ability to add additional "Minister Cards" to an existing "Companionship Card" by dragging.
            § Ability to drag "Minister Cards" out of a "Companionship Card" to disassociate them.
        ○ Creating Families:
            § Drag an "Individual Card" onto another "Individual Card" (or an empty "Family Card" if created via button) to form a "Family Card."
            § Alternatively, a "Create Family" button can be used, then "Individual Cards" dragged into it.
            § Ability to add additional "Individual Cards" to an existing "Family Card" by dragging.
            § Ability to drag "Individual Cards" out of a "Family Card" to disassociate them.
        ○ Creating Ministering Assignments:
            § Drag an "Individual Card" or "Family Card" onto a "Companionship Card" to create a "Ministering Assignment Card."
            § Dragging an "Individual Card" onto an existing "Ministering Assignment Card" adds that individual to the existing assignment.
            § Dragging a "Family Card" onto an existing "Ministering Assignment Card" adds that family to the existing assignment.
            § Ability to drag components out of a "Ministering Assignment Card" to break the assignment.
        ○ Assigning to Districts:
            § Drag "Ministering Assignment Cards" into a designated district area on the board.
    3. District Management:
        ○ Ability to create and name new districts.
        ○ Ability to assign a "person in charge" (from an "Individual Card") to each district.
        ○ Ability to rearrange districts on the board.
    4. Notes:
        ○ A clear mechanism to add, edit, and view notes associated with any "Individual," "Family," "Companionship," or "District."
C. Data Management & Persistence:
    1. Import Functionality:
        ○ Import a list of names (e.g., from a CSV or JSON file) to populate the individuals.
        ○ Upon import, automatically create both "Individual Cards" and "Minister Cards" for each person.
    2. Export Functionality:
        ○ Export a "ready-to-print" list of all ministering assignments, organized by district and companionship.
        ○ Ability to export data in a structured format (e.g., JSON) for backup/transfer.
    3. Local Data Storage:
        ○ All user data must remain on the end-user's computer. No data is to be transmitted to external servers.
        ○ Data should be stored securely and persistently (e.g., using IndexedDB or local file system access).
    4. Password Protection:
        ○ Option to password-protect the stored data. This implies encryption of the locally stored data using a user-provided password.
D. Output & Communication:
    1. Direct Printing:
        ○ Print functionality for the organized ministering assignment lists.
    2. Emaileable Segments:
        ○ Ability to generate easily copy-and-pasteable (or perhaps directly emailable via client-side mailto links) segments of assignments:
            § For individual companionships.
            § For district leaders (listing all assignments within their district).
E. Enterprise-Grade Considerations:
    1. Scalability: Design for potential large numbers of individuals, families, and assignments.
    2. User Experience (UX): Intuitive, responsive, and visually appealing interface.
    3. Performance: Smooth drag-and-drop interactions and quick data loading/saving.
    4. Accessibility: Consider accessibility standards (WCAG) for all users.
    5. Maintainability: Clean, modular code, easily understood and updated by future developers.
    6. Security (Local): Robust local data encryption and password handling (hashing, salting) without server-side interaction.

II. Recommended Tools & Technologies (Website Only, with Future Expansion in Mind)
A. Programming Languages:
    • Frontend:
        ○ JavaScript (with TypeScript): Essential for interactive web applications. TypeScript adds static typing, significantly improving code quality, maintainability, and scalability for enterprise projects.
        ○ HTML5: For structuring the content.
        ○ CSS3: For styling and layout.
    • Backend (Local-only context):
        ○ Since all processing is local, there's no traditional server-side backend. However, for future integration with the Church's tools (which might involve APIs), a strong grasp of a server-side language will be beneficial. For this local-only web app, the "backend" logic will reside within the client-side JavaScript.
B. Frontend Framework/Library:
    • React.js (with Redux/Zustand for State Management): Highly recommended for building complex, interactive user interfaces with a component-based architecture. Its virtual DOM provides excellent performance, and its vast ecosystem and community support are invaluable for enterprise-grade applications.
        ○ Alternative: Vue.js or Angular. Each has its strengths, but React is a very strong choice for interactive, drag-and-drop UIs.
C. Drag-and-Drop Library:
    • react-beautiful-dnd (for React): Excellent accessibility, performance, and user experience for drag-and-drop lists and grids. It's well-maintained and provides a robust API.
        ○ Alternative: react-dnd (more flexible, but steeper learning curve), Dnd-kit.
D. Local Data Storage:
    • IndexedDB API: Browser-native, robust NoSQL database for client-side storage of large amounts of structured data. This is crucial for your requirement that "no data is to ever leave the end user's computer."
    • Web Cryptography API: For client-side encryption and decryption of data using the user's password. You'll need to carefully implement strong cryptographic practices (e.g., AES-GCM for symmetric encryption, key derivation functions like PBKDF2 or Argon2 for password hashing).
E. Styling Framework/Library:
    • Tailwind CSS: A utility-first CSS framework that allows for rapid UI development and highly customizable designs. It encourages consistent styling and can be highly performant.
        ○ Alternative: Styled Components, Emotion (for CSS-in-JS), or a component library like Material-UI or Ant Design if you prefer pre-built components.
F. IDE (Integrated Development Environment):
    • Visual Studio Code (VS Code): The de facto standard for web development. It's lightweight, highly extensible (thousands of plugins for all languages, frameworks, linters, debuggers), and has excellent integration with Git. It's used by a vast majority of web developers for both personal and enterprise projects.
        ○ Alternative: WebStorm (from JetBrains, a more feature-rich, paid IDE specifically for JavaScript development).
G. Testing Frameworks:
    • Unit/Component Testing:
        ○ Jest: A JavaScript testing framework (often used with React) that is fast, easy to set up, and includes mocking and assertion libraries.
        ○ React Testing Library: Focuses on testing components from the user's perspective, encouraging more robust and maintainable tests.
    • End-to-End (E2E) Testing:
        ○ Cypress: Excellent for E2E testing of web applications. It's fast, reliable, and provides a great developer experience with real-time reloads and debugging.
        ○ Alternative: Playwright.
H. Version Control:
    • Git: Absolutely essential for team collaboration, tracking changes, and managing different versions of your codebase.
    • GitHub/GitLab/Bitbucket: For hosting your Git repositories and facilitating collaboration (even if you're the sole developer initially, it's good practice).
I. Package Manager:
    • npm (Node Package Manager) or Yarn: For managing project dependencies and running scripts.

III. Recommended Classes/Modules (Conceptual Structure)
This outlines a potential object-oriented design for your application, following best coding practices for maintainability and scalability. These can be implemented as JavaScript classes or functional components with hooks, depending on your chosen framework.
// Core Data Models
class Individual {
    id: string; // Unique identifier (UUID recommended)
    name: string;
    type: 'individual' | 'minister'; // To differentiate between individual cards and minister cards
    notes: string;
    // Potentially other attributes like contact info, specific roles, etc.
}
class Family {
    id: string;
    name: string; // Family name (e.g., "Smith Family")
    members: Individual[]; // Array of Individual objects
    notes: string;
}
class Companionship {
    id: string;
    ministers: Individual[]; // Array of Minister (Individual) objects
    notes: string;
}
class MinisteringAssignment {
    id: string;
    companionship: Companionship;
    assignedTo: (Individual | Family)[]; // Array of Individual or Family objects
    notes: string;
    districtId: string | null; // ID of the district it belongs to, null if unassigned
}
class District {
    id: string;
    name: string; // District name (e.g., "North District")
    leader: Individual | null; // The Individual object assigned as leader
    assignments: MinisteringAssignment[]; // Array of MinisteringAssignment objects
    notes: string;
}
// Data Management / Persistence Layer
class DataService {
    // Manages interaction with IndexedDB
    // Methods for:
    // - saveData(data: AppData): Promise<void>
    // - loadData(): Promise<AppData>
    // - encryptData(data: string, password: string): Promise<string>
    // - decryptData(encryptedData: string, password: string): Promise<string>
    // - generateKey(password: string, salt: Uint8Array): Promise<CryptoKey>
    // - generateSalt(): Uint8Array
}
// Application State Management (e.g., using Redux or Zustand)
interface AppState {
    individuals: Record<string, Individual>; // Map for quick lookup by ID
    families: Record<string, Family>;
    companionships: Record<string, Companionship>;
    ministeringAssignments: Record<string, MinisteringAssignment>;
    districts: Record<string, District>;
    // Other UI-related state like:
    // - selectedCardId: string | null;
    // - isModalOpen: boolean;
    // - isLoading: boolean;
    // - currentPassword: string | null; // For encryption/decryption
}
// UI Components (React Components)
class App {
    // Main application component
    // Manages overall layout, routing (if any), and global state
}
class DigitalBoard {
    // Renders the main board, districts, and draggable cards
    // Handles drag-and-drop logic and dispatches state updates
}
class IndividualCard {
    // Renders an individual's information
    // Handles click events for notes, drag source
}
class FamilyCard {
    // Renders family information and member list
    // Handles click events for notes, drag source/target
}
class CompanionshipCard {
    // Renders companionship members
    // Handles click events for notes, drag source/target
}
class MinisteringAssignmentCard {
    // Renders assignment details (companionship, assigned to)
    // Handles click events for notes, drag source/target
}
class DistrictContainer {
    // Renders a single district, its leader, and assignments
    // Handles drag target for ministering assignments
}
class ImportExportModal {
    // UI for importing/exporting data
}
class PrintManager {
    // Logic for formatting and initiating prints
    // Methods for:
    // - generatePrintableList(): string // Returns HTML or text
    // - printCurrentAssignments(): void
    // - generateEmailSegment(type: 'companionship' | 'district', id: string): string
}
class SecurityManager {
    // Handles password input, key derivation, and calls to DataService encryption/decryption.
    // Manages local password state (e.g., transiently for decryption operation).
}
// Utility Classes/Functions
class UUIDGenerator {
    // Helper to generate unique IDs
}
class DragDropHelper {
    // Abstraction for drag-and-drop logic if using a lower-level library
}
class Validator {
    // For input validation (e.g., import data format)
}

IV. Other Recommendations for Building Enterprise-Grade Software
A. Development Methodology:
    • Agile (Scrum or Kanban): Given the iterative nature of refining a user-centric application like this, an Agile methodology is ideal.
        ○ Scrum: Work in short sprints (1-2 weeks), with daily stand-ups, sprint planning, reviews, and retrospectives. This allows for continuous feedback and adaptation.
        ○ Kanban: If development flow is more continuous and less structured by fixed sprints, Kanban can visualize workflow, limit work-in-progress, and maximize efficiency.
B. Design & Prototyping:
    • User Experience (UX) Design: Before writing much code, invest time in UX research, user flows, wireframes, and high-fidelity mockups. Tools like Figma or Adobe XD can be invaluable. This ensures the drag-and-drop interface is truly intuitive.
    • Information Architecture (IA): Clearly define how all the different "cards" and "districts" relate to each other visually and functionally.
    • Design System: Even for a single-person project, consider defining a small design system (colors, typography, spacing, component styles) to ensure consistency.
C. Code Quality & Standards:
    • Linting (ESLint): Enforce consistent code style and identify potential errors early. Configure it with a strong set of rules (e.g., Airbnb style guide).
    • Code Formatting (Prettier): Automatically format your code to a consistent style, reducing bikeshedding during development.
    • Code Reviews: If working with others, implement code reviews. Even for solo development, periodically review your own code with a fresh perspective.
    • Documentation:
        ○ In-code comments: Explain complex logic or non-obvious parts.
        ○ README.md: Comprehensive project setup, how to run, and basic usage.
        ○ API documentation: For the different classes/modules, what they do, their inputs, and outputs.
        ○ User documentation: As the project progresses, outline how users will interact with the application.
D. Testing Strategy (as requested, all code will have tests):
    • Unit Tests: Test individual functions, methods, and small components in isolation. (Jest, React Testing Library)
    • Integration Tests: Test how different units or components work together. (Jest, React Testing Library)
    • End-to-End (E2E) Tests: Simulate real user interactions across the entire application to ensure flows work as expected. Crucial for drag-and-drop functionality. (Cypress, Playwright)
    • Performance Testing (client-side): Ensure the drag-and-drop and data operations remain smooth even with a large dataset. Browser developer tools can help here.
    • Security Testing (client-side): Focus on the integrity of local data storage and encryption. Try to break your password protection.
    • Accessibility Testing: Use tools and manual checks to ensure the application is usable by individuals with disabilities.
E. Deployment (Local Web App):
    • For a purely local web application, the "deployment" primarily involves distributing the static HTML, CSS, and JavaScript files.
    • Consider using tools like webpack or Vite for bundling and optimizing your frontend assets for production.
    • You might package it as a Progressive Web App (PWA) to allow users to "install" it on their desktop/mobile devices for an app-like experience, even offline.
F. Future Considerations (for Church Integration):
    • API Design: Even if not built initially, think about how an API would expose and consume data for ministering assignments if it were to integrate with Church tools.
    • Authentication/Authorization: How would users log in and what permissions would they have? (This would require a server-side component).
    • Data Synchronization: If data were to be synced, how would conflicts be resolved?
    • Scalability: While focusing on local now, remember that enterprise-grade scalability often means distributed systems and cloud infrastructure.
By following these recommendations, you'll be well on your way to building a high-quality, maintainable, and robust ministering assignment management application. Good luck with this meaningful project!

From <https://gemini.google.com/app/b6198920c0fc1c95> 

