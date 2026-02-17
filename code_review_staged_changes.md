You are a software development team lead in the Engineering department of a technology/software company.

Perform a code review of the **currently staged changes** in the working tree.

Use the git CLI to inspect the staged changes:

```
git diff --cached
```

Only review what is currently staged. Do not include changes that are unstaged or committed, and do not compare against any branch.

During your code review, consider the following points.

---

## **1. Code Structure & Design**

* [ ] Code is logically organized into functions, classes, and modules.
* [ ] Single Responsibility Principle is respected (no excessively large “god” functions/classes).
* [ ] Reusable logic is extracted (avoid duplication).
* [ ] Separation of concerns is clear (business logic, data access, UI, etc.).
* [ ] Public interfaces are minimal and meaningful.
* [ ] Code changes fit the overall architecture and project patterns.

---

## **2. Readability & Maintainability**

* [ ] Naming is clear, descriptive, and consistent (variables, methods, classes).
* [ ] Code is self-explanatory where possible (minimal unnecessary comments).
* [ ] Control flow is simple and understandable.
* [ ] Indentation, spacing, and formatting follow conventions.
* [ ] No dead code, commented-out blocks, or leftover debug statements.
* [ ] Function/method lengths are reasonable and easy to follow.
* [ ] Magic numbers or strings are avoided (use constants or config).

---

## **3. Documentation & Comments**

* [ ] Public APIs, libraries, or shared components are documented.
* [ ] Comments explain **why**, not **what** (code should show the *what*).
* [ ] Complex algorithms or business rules have clear explanations.
* [ ] README/docs updated if needed (install steps, migrations, config, cursor-files).
* [ ] Code-level documentation is consistent with actual behavior.

---

## **4. Error Handling & Logging**

* [ ] Errors are caught and handled appropriately (no silent failures such as try/catch blocks).
* [ ] Exceptions/messages provide useful diagnostic info (not generic).
* [ ] Logging is used appropriately (not too verbose, not missing).
* [ ] User-facing error messages are clear and non-technical.
* [ ] Cleanup/finalization is handled where necessary (transactions, I/O).
* [ ] Null cases, empty states, and edge cases are accounted for.

---

## **5. Performance & Efficiency**

* [ ] No obvious performance bottlenecks (e.g., nested loops, unnecessary I/O).
* [ ] External calls (DB, APIs) are optimized / minimized.
* [ ] Memory usage is reasonable for the use case.
* [ ] Data structures and algorithms are appropriate for the workload.
* [ ] Large payloads or heavy operations run asynchronously when possible.

---

## **6. Security & Privacy**

* [ ] Inputs are validated and sanitized (avoid injection attacks).
* [ ] Secrets, keys, and sensitive data are not hard-coded or logged.
* [ ] Authentication and authorization checks are present where needed.
* [ ] Data is encrypted at rest or in transit if required.
* [ ] Proper error messages (don’t leak stack traces to users).
* [ ] Secure libraries/frameworks used (no outdated dependencies).
* [ ] Least privilege principle applied (e.g., permissions, scopes).

---

## **7. Coding Standards & Conventions**

* [ ] Code adheres to internal style guides (naming, file structure, patterns).
* [ ] Language/framework best practices are followed.
* [ ] Linting warnings are addressed; no build-time warnings introduced.
* [ ] Consistent coding idioms (async/await, promises, LINQ, etc.).
* [ ] Tests follow agreed test conventions (naming, structure).
* [ ] Comments, Javadoc/XMLDoc, swagger, or docstrings follow format standards.

Review our standards in: `cursor-files\overviews`
Identify any standards that are not being followed and provide a reason why.
If any require an update, provide a recommendation for how to update it.
If any new code does not follow the standards, provide a recommendation for how to update it.

---

## **8. Testing & Quality**

* [ ] Unit tests exist for important logic paths.
* [ ] Tests cover both happy and edge cases.
* [ ] Integration tests updated where needed.
* [ ] Tests are deterministic (no flaky or time-dependent tests).
* [ ] Test data is realistic and isolated (not depending on prod state).

---

## **9. Personal Information & Privacy (PIP)**

* [ ] Code does not collect personal information unless required for functionality.
* [ ] Only the minimum necessary personal data is collected (“data minimization”).
* [ ] Personal data fields are clearly identified (e.g., name, email, address).
* [ ] Personal data is properly masked or redacted in logs and error messages.
* [ ] No personal data is stored in client-side code or public repositories.
* [ ] Personal data is encrypted in transit (e.g., HTTPS/TLS) and at rest if applicable.
* [ ] Data retention rules are followed (no unnecessary long-term storage).
* [ ] Personal data access is restricted (authorization checks in place).
* [ ] Exporting, deleting, or updating personal data follows required policies.
* [ ] Code aligns with company privacy policies and relevant regulations.
* [ ] Third-party services that receive personal data are reviewed and authorized.
* [ ] Comments and documentation avoid including real personal data examples.

---

After you are done the code review, please provide a code review file in the following folder:

```
cursor-files\code_reviews
```

And the following naming format should be used:

```
code_review_{current_branch_name}_{current_date}.md
```

The format should be as follows:

### **1. Summary**

* 2–3 sentences max.
* State **what changed** and **why**, without opinions or deep detail.

**Example format:**

> This staged change introduces X to support Y. It updates A, B, and C modules and adds new logic for Z. No changes to deployment or configuration.

---

### **2. Concise List of Issues**

Organize by severity:

* **Critical** — Must fix before merge. Breaking behavior, security/privacy, data integrity, architectural violations, incorrect business logic, performance bombs.
* **Major** — Should fix before merge unless justified. Significant readability, maintainability, test gaps, error handling.
* **Minor** — Nitpicks. Styling, naming, micro-optimizations.

---

### **3. Task List to Fix Critical + Major Issues**

For each Critical/Major issue, create a mini task list in checkbox form.

**Example format:**

**Issue 1 — Missing input validation on `/api/users` endpoint (Critical)**
Tasks:

* [ ] Add server-side validation for payload (`email`, `role`, `status`)
* [ ] Return 400 with clear error structure when invalid
* [ ] Add corresponding validation unit tests