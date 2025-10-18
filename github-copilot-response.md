AI request:
Give me a list of the features I wrote about formatted as though they were being given to a programming team, a list of the recommended tools (including things like which IDE I might use) I would use to build said program, as a website only but with the plan of taking it bigger later, recommended programming languages, and anything else I should have in place to build this software. Also, give me a list of the recommended classes I should include in this program. For this project, I will build tests for all code. Give your recommendations following the best coding practices that result in the highest quality code over the long term. 

# Ministering Board Project – Programming Team Brief

---

## 1. Feature List

### Core Features
- **Individuals Management**
  - Create/edit/delete individuals.
  - Import individuals from a list (CSV, XLSX, or plain text).
  - Individuals can belong to families and/or companionships.
  - Each individual has an "individual card" and a "minister card" (drag-and-drop).

- **Families**
  - Families consist of 1 or more individuals.
  - Families can be created by drag-and-drop or via a button.
  - Cards represent families; can be dragged onto other cards.

- **Companionships**
  - Companionships consist of 2+ individuals (default: 2).
  - Created by dragging one minister card onto another, or via a button.
  - Cards represent companionships; can be dragged, rearranged, or dissolved.

- **Ministering Assignments**
  - Created by combining companionships and families/individuals.
  - Assignment cards are draggable and can be placed in districts.
  - Dragging a family/individual onto a companionship creates an assignment.

- **Districts**
  - The board is split into districts.
  - Each district has an assigned leader (from presidency).
  - Assignment cards can be dragged into districts.
  - District cards are draggable and can accept assignments.

- **Notes**
  - Add/view/edit notes on individuals, families, companionships, assignments, and districts.

- **Import/Export**
  - Import list of individuals (CSV, XLSX, text).
  - Export/print all ministering assignments as a printable list.
  - Export can be segmented for emailing to companionships or district leaders.

- **Drag-and-Drop Board**
  - All cards (individual, minister, family, companionship, assignment, district) are draggable and can be rearranged.
  - Easy drag-and-drop interface for building assignments.

- **Security & Privacy**
  - All data is stored and processed locally (never leaves the user’s computer).
  - Option for password protection/encryption of data.

- **Print/Email**
  - Auto-organize districts into printable lists.
  - Export/print for physical distribution or send segments via email.

### Future/Enterprise Features (for later consideration)
- Integration with LDS Tools or Church systems.
- Multi-user collaboration (with local sync).
- Mobile app support.

---

## 2. Recommended Tools & Technologies

### IDEs
- **Visual Studio Code** (recommended: extensive web dev support, extensions)
- JetBrains WebStorm (for advanced JS/TS development)
- Optional: GitHub Codespaces for cloud-based dev

### Frameworks/Libraries
- **Frontend:**
  - **React** (with TypeScript) – best for component-driven, stateful UIs
  - **Redux Toolkit** or **Zustand** – for state management
  - **React DnD** or **React-Beautiful-DnD** – for drag-and-drop functionality
  - **Material-UI (MUI)** or **Chakra UI** – for enterprise-grade, accessible UI components
  - **Jotai** or **Recoil** (optional alternative for state)

- **Data Storage:**
  - **IndexedDB** via **Dexie.js** or **localForage** – for local, persistent, secure storage
  - **crypto-js** or **Web Crypto API** – for password protection/encryption

- **Testing:**
  - **Jest** – unit and integration testing
  - **React Testing Library** – for React component testing
  - **Cypress** or **Playwright** – for end-to-end UI testing

- **Build Tooling:**
  - **Vite** or **Create React App** (Vite recommended for speed)
  - **ESLint**, **Prettier** – for code quality and formatting
  - **Husky** – Git hooks for enforcing tests/lint on commit

- **Other:**
  - **papaparse** or **SheetJS** – for import/export of CSV/XLSX
  - **jsPDF** or **print.js** – for generating printable PDFs
  - **TypeScript** (strong typing, maintainability)

---

## 3. Recommended Programming Languages

- **TypeScript** (for all frontend code)
- **JavaScript** (only if TypeScript is not possible for a dependency)
- **CSS/SCSS** (for styling, prefer CSS-in-JS with MUI/Chakra)

---

## 4. Project Structure & Best Practices

- Strict adherence to **TypeScript** for type safety.
- Modular, component-based design (React).
- All stateful logic in custom hooks or store (Redux/Zustand).
- All business logic covered by unit tests.
- 100% code coverage for core logic.
- Accessibility (a11y) compliant UI.
- Clean code: linting, consistent formatting.
- Automated CI for tests/lint (even for local-only apps, for dev workflow).
- Documentation for all functions/classes/components.

---

## 5. Recommended Classes (Domain Model)

Define all classes as TypeScript interfaces/types for clarity and type safety.

```typescript
// Individual person
interface Individual {
  id: string;
  firstName: string;
  lastName: string;
  notes?: string;
  tags?: string[];
  isYouth?: boolean;
}

// Family (1+ Individuals)
interface Family {
  id: string;
  name: string;
  members: string[]; // Array of Individual ids
  notes?: string;
}

// Minister (reference to an Individual)
interface Minister {
  id: string;
  individualId: string;
  notes?: string;
  color?: 'white' | 'pink'; // for display: adult/youth
}

// Companionship (2+ Ministers)
interface Companionship {
  id: string;
  ministerIds: string[]; // Array of Minister ids
  notes?: string;
}

// Ministering Assignment (Companionship -> Family/Individual)
interface MinisteringAssignment {
  id: string;
  companionshipId: string;
  familyId?: string;
  individualId?: string;
  notes?: string;
}

// District (group of assignments, with a leader)
interface District {
  id: string;
  name: string;
  leaderIndividualId: string;
  assignmentIds: string[];
  notes?: string;
}

// BoardState (top-level app state)
interface BoardState {
  individuals: Record<string, Individual>;
  families: Record<string, Family>;
  ministers: Record<string, Minister>;
  companionships: Record<string, Companionship>;
  assignments: Record<string, MinisteringAssignment>;
  districts: Record<string, District>;
}
```

---

## 6. Additional Recommendations

- **User Experience:** Prioritize drag-and-drop, undo/redo, keyboard accessibility.
- **Local Storage:** All data must remain on device. Use IndexedDB, never send data to cloud. Allow user to export/import encrypted data files.
- **Security:** Use password-based encryption for stored data (Web Crypto API).
- **Testing:** Write unit, integration, and E2E tests for all features (Jest, React Testing Library, Cypress).
- **Documentation:** Inline code docs, plus a README and developer guide.

---

## 7. Summary

Your stack should be:
- **React + TypeScript**
- **MUI/Chakra UI**
- **IndexedDB (Dexie.js/localForage)**
- **React DnD/Beautiful-DnD**
- **Jest + React Testing Library + Cypress**
- **Vite** for build tooling

All code and data must be local and secure. Write comprehensive tests for everything. Design the data model as above. Use best practices for maintainability, accessibility, and security.

---
