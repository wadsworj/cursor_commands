# Plan Requirements

A plan must contain the following:

## 1. Text UI mockups

- Include text UI mockups of any visual elements/pages.

  **Example:**
  ```
  +------------------+
  |  [Logo]  Sign In |
  +------------------+
  | Email: [________] |
  | Pass:  [________] |
  | [  Log in  ]      |
  +------------------+
  ```

## 2. User diagram flow

- Include a user diagram flow.

  **Example (Mermaid):**
  ```mermaid
  flowchart TD
    A[Landing] --> B[Sign In]
    A --> C[Register]
    B --> D[Dashboard]
    B --> E[Forgot Password]
  ```

## 3. Text file directory list

- Include a text file directory list with: new projects, new folders, new files, edited files.

  **Example:**
  ```
  src/
  ├── auth/                    (NEW folder)
  │   ├── Login.tsx            (NEW)
  │   └── useAuth.ts           (NEW)
  ├── App.tsx                  (EDIT)
  package.json                 (EDIT)
  ```

## 4. Test strategy

- Number of tests and specific edge cases covered.

## 5. Work order

- Give a detailed view of the order in which work can/must be completed.
- Clearly distinguish:
  - **In parallel:** Tasks that have no dependency on each other and can be done at the same time (e.g. by one agent in any order, or by multiple agents).
  - **Sequential:** Tasks that depend on earlier steps and must be done in a defined order.
- Use a vertical breakdown by phase. Within each phase, list components and their dependencies on earlier phases so it is clear what can be done in parallel.

  **Example (vertical breakdown):**
  ```
  Phase 1 (all in parallel)
  ├── 1A  Repo / project setup
  └── 1B  API contracts + DB schema

  Phase 2 (depends on Phase 1; 2A/2B/2C in parallel with each other)
  ├── 2A  Backend API          (depends on 1B)
  ├── 2B  Auth module          (depends on 1A)
  └── 2C  Seed data / migrations (depends on 1B)

  Phase 3 (depends on Phase 2; 3A/3B in parallel)
  ├── 3A  Frontend app         (depends on 2A, 2B)
  └── 3B  E2E tests / docs    (depends on 2A)
  ```

  Within a phase, items with no dependency on each other can be done in parallel. Items that depend on different prior items become available as soon as their prerequisites are done.

  **Example (Mermaid, vertical):**
  ```mermaid
  flowchart TB
    subgraph P1["Phase 1 (parallel)"]
      1A[1A Repo / project setup]
      1B[1B API contracts + DB schema]
    end
    subgraph P2["Phase 2 (parallel)"]
      2A[2A Backend API]
      2B[2B Auth module]
      2C[2C Seed data / migrations]
    end
    subgraph P3["Phase 3 (parallel)"]
      3A[3A Frontend app]
      3B[3B E2E tests / docs]
    end
    1B --> 2A
    1B --> 2C
    1A --> 2B
    2A --> 3A
    2B --> 3A
    2A --> 3B
  ```

## 6. Steps at end of implementation

- **a)** Run any code review files found in `.cursor` or `cursor-files` that are relevant.
- **b)** Fix results of code review.
- **c)** Build the projects.

## 7. Build steps

- Include a concise list of build steps for each component/project.

  **Example:**
  #### Backend
  1. cd api
  2. npm install
  3. npm run build

  #### Frontend
  1. cd web
  2. npm install
  3. npm run build

## 8. Release updates

- Include a step to **update release versions/release notes** (check `.cursor` or `cursor-files` for relevant config/instructions).

## 9. Screenshots (web/UI changes only)

- Tell the agent: "Run the app, open the local URL in the browser, and take a screenshot of the homepage so I can see the UI."
