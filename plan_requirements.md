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
- Use a structure that makes dependencies explicit (e.g. phases, numbered steps with “after step N”, or a Mermaid diagram).

  **Example (Mermaid):**
  ```mermaid
  flowchart LR
    subgraph parallel1["Phase 1 (parallel)"]
      A[API contracts]
      B[DB schema]
      C[Auth module]
    end
    subgraph sequential["Phase 2 (sequential)"]
      D[Backend API] --> E[Frontend]
    end
    parallel1 --> D
  ```

  **Example (list):**
  - **Phase 1 (parallel):** Set up repo, define API contracts, design DB schema.
  - **Phase 2 (after Phase 1):** Implement backend API; then implement frontend (sequential after API).

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
