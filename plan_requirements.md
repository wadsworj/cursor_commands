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

## 4. Steps at end of implementation

- **a)** Run any code review files found in `.cursor` or `cursor-files` that are relevant.
- **b)** Fix results of code review.
- **c)** Build the projects.

## 5. Build steps

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

## 6. Release updates

- Include a step to **update release versions/release notes** (check `.cursor` or `cursor-files` for relevant config/instructions).
