# Hills to Heights

## Development Practices

Our development and release process follows a **structured and transparent flow** to ensure stability, accountability, and clear visibility across environments. Every change goes through multiple checkpoints, from a developer’s local machine to staging environment and then live production environment, ensuring quality and consistency at each stage.

---

### Environment Flow

| Environment | Purpose | Source Branch | Hosted On |
|--------------|----------|----------------|------------|
| **Local (Developer Machines)** | Active feature development, unit testing, and debugging. Each developer works on isolated branches for specific features or bug fixes. | `feature/*` | Developer’s system (macOS / Windows) |
| **UAT (Staging)** | Central environment for QA testing, client review, and integration testing. Reflects the production setup closely to catch potential issues before release. | `develop` | AWS EC2 (Staging Server) |
| **Production** | Live environment for end users. Only thoroughly reviewed and tested code is deployed here. | `main` | AWS EC2 (Production Server) |

---

### Flow Summary

1. **Local Development**
   - Developers create or update code on their local machines.
   - Each new feature, improvement, or bug fix is developed on a dedicated branch following the naming convention:  
     ```
     feature/<feature-name> or fix/<issue-name>
     ```
   - Developers ensure their local environments mirror production as closely as possible using environment variables, or local configs.

2. **Code Review & Merge to `develop`**
   - Once a feature is complete, the developer creates a **Pull Request (PR)** for review.
   - Code is reviewed by peers or leads for:
     - Functionality correctness  
     - Code quality and standards  
     - Security and performance checks  
   - After approval, the branch is merged into `develop`.

3. **UAT (User Acceptance Testing)**
   - The `develop` branch is deployed to the **UAT environment**.
   - QA engineers test end-to-end functionality, API integrations, data integrity, and UI/UX.
   - After approval from QA client also review and provide feedback on this environment before the final release.

4. **Pre-Production Review**
   - Final verification of all merged changes.
   - Backup and version tagging are done before production deployment

5. **Production Deployment**
   - Approved changes from `develop` are merged into the `main` branch.
   - Deployment to the **Production server** is done manually (currently) using secure CI/CD practices:
     - Backup existing data and configurations.
     - Deploy updated code.
     - Perform quick smoke testing post-deployment.

6. **Post-Deployment Verification**
   - Validates that all core functionalities are intact.
   - If any issues are found, rollback procedures are available.

---

### Branching Strategy

We follow a simplified **Git Flow** model with three main branches:

- `main` → Stable production-ready code
- `develop` → Active integration branch for next release  
- `feature/*` → Individual developer branches  

---

### Configuration Management

Environment-specific configurations (API keys, DB credentials, etc.) are stored securely using `.env` files (excluded from version control).

---

### Automation Roadmap

CI/CD (GitHub Actions) is planned to automate:

- Linting & testing during pull requests  
- Automatic UAT deployments on merge to `develop`  
- Version tagging and changelog generation  
- Auto-deployments to production upon approval  

---

### Responsibilities Per Environment

| Role | Local | UAT | Production |
|------|--------|------|-------------|
| **Developers** | Build and test features | Verify UAT fixes and integration | Support during release |
| **QA Team** | Local smoke testing (optional) | Execute full test suite | Validate release |
| **Client / Stakeholders** | — | Review and approve features | Final user acceptance |

---

### Visual Flow

```text
Local (feature/*)
        ↓
     Pull Request
        ↓
  Merge to develop
        ↓
   UAT Deployment
        ↓
     QA + Client Review
        ↓
   Merge to main
        ↓
 Production Deployment
