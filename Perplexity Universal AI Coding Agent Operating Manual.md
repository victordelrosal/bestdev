# Universal AI Coding Agent Operating Manual

## Architecture & Design

1. **Apply Modular Patterns:**  
   Decompose all functionality into discrete, reusable modules. Favor composable APIs and keep service boundaries explicit.  
   *Rationale: Enables maintainability, scalability, and rapid iteration.*

2. **Enforce SOLID Principles:**  
   Design components to follow SOLID: single responsibility, open/closed, substitution, interface segregation, dependency inversion.  
   *Rationale: Prevents unnecessary coupling and supports future-proof extensibility.*

3. **Maintain Clean Boundaries:**  
   Separate business logic, infrastructure, and interface layers. Use dependency injection and domain-driven design where possible.  
   *Rationale: Minimizes leakage and technical debt across layers.*

4. **Design for Scalability:**  
   Write stateless code by default. Use asynchronous patterns, batch processing, and horizontal scaling in cloud-friendly environments.  
   *Rationale: Prepared for growth, minimizes performance bottlenecks.*

## Code Quality

5. **Consistent Naming Conventions:**  
   Follow widely recognized naming standards for chosen language (PEP8, camelCase, etc.). Name everything for clarity of intent.  
   *Rationale: Improves legibility and team consistency.*

6. **Prioritize Self-Documenting Code:**  
   Write code whose structure and nomenclature communicate purpose and flow without excessive commentary.  
   *Rationale: Reduces ambiguity, aids review and onboarding.*

7. **Enforce Inline Documentation:**  
   Where logic or intent cannot be inferred, annotate with succinct docstrings or contextual comments above functions/classes.  
   *Rationale: Supports fast comprehension and safe modification.*

8. **Trigger Refactoring Proactively:**  
   Refactor whenever encountering duplicated logic, over-complexity, large functions, or stale patterns.  
   *Rationale: Maintains code health, prevents compounding debt.*

## User Experience

9. **Code Accessibility-First:**  
   For UI code, implement WCAG 2.2 guidelines and proper ARIA roles. For APIs, return standard error codes and human-readable messages.  
   *Rationale: Guarantees usability and compliance for all users.*

10. **Progressive Enhancement as Default:**  
    Build robust basic experiences, then layer advanced features.  
    *Rationale: Ensures broader compatibility and graceful degradation.*

11. **Set and Monitor Performance Budgets:**  
    Define budgets early for load times, resource usage, and latency. Instrument code to monitor and alert on breaches.  
    *Rationale: Drives reliability and optimal user experience.*

12. **Handle Error States Gracefully:**  
    Always code for failure. Return actionable errors, preserve workflows, and avoid silent or obscure failures.  
    *Rationale: Improves troubleshooting and user trust.*

## Security & Reliability

13. **Validate All Inputs Rigorously:**  
    Apply allowlist validation, enforce data types and bounds, and reject on first invalid input.  
    *Rationale: Blocks injection and reduces attack surface.*

14. **Implement Secure Auth & Access Control:**  
    Default to least privilege; use proven libraries for authentication and authorization.  
    *Rationale: Reduces exposure and compliance risk.*

15. **Protect Data at All Stages:**  
    Encrypt sensitive data at rest and in transit. Store credentials securely with robust hashing.  
    *Rationale: Ensures privacy and regulatory adherence.*

16. **Add Resilient Recovery Mechanisms:**  
    Code for retries, graceful rollbacks, circuit breakers, and thorough logging.  
    *Rationale: Fault tolerance minimizes downtime.*

17. **Automate Security Checks:**  
    Integrate static/dynamic analysis, dependency scanning, and security tests in CI/CD pipelines.  
    *Rationale: Catches vulnerabilities before release; enforces continuous compliance.*

## Development Lifecycle

18. **Practice Clean Version Control Hygiene:**  
    Use semantic branch names (feat/, fix/, chore/), write descriptive commit messages, and open pull requests for all code changes.  
    *Rationale: Facilitates traceability and collaboration.*

19. **Follow the Testing Pyramid:**  
    Favor high-coverage unit tests, with integration and end-to-end tests for mission-critical paths. Coverage should remain above 70%.  
    *Rationale: Prevents regressions and supports rapid iteration.*

20. **Embed CI/CD Readiness:**  
    Automate builds, tests, and deployments; enforce trunk-based development where possible.  
    *Rationale: Accelerates shipping and feedback loops.*

21. **Instrument for Debugging:**  
    Code with logs, traces, and metrics hooks (OpenTelemetry or similar standards) as defaults.  
    *Rationale: Supports observability, diagnosis, and optimization.*

## Operating Directives

22. **Human Validation at Critical Steps:**  
    Always request explicit human review for high-risk changes.  
    *Rationale: Mitigates AI hallucination and hidden errors.*

23. **Iterate, Refine, and Document Promptly:**  
    Treat all AI-generated code as provisional. Incorporate structured feedback and document rationale for changes.  
    *Rationale: Supports iterative improvement and knowledge transfer.*

24. **Align with Project-Specific Standards:**  
    Adapt style, auxiliary tools, and conventions to the project, but never compromise on core rules above.  
    *Rationale: Delivers context-aware yet consistent code quality.*

---

**Agents must load, parse, and honor this manual before generating code. Any output must reflect these rules and underlying rationales.**
