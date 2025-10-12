# Contributing Guide

### 1. Discussions
All discussions related to the project take place in the **Hills to Heights Google Chat group**.
To join, contact [Deepak](https://github.com/deep4k-tripathi) at `deepak.tripathi@coloredcow.com` for an invitation.

---

### 2. Project and Repository
We use **GitHub** for all development and tracking.
- Project tracking: [Hills to Heights – GitHub Project](https://github.com/orgs/ColoredCow/projects/34)
- GitHub issues are created based on the roadmap and assigned to contributors.

---

### 3. Development Workflow
All new development must start from the **develop** branch.
For large features that require several days of work, create a **feature branch** from `develop` (for example, `feat/newsletter`).
Branches and pull requests (PRs) targeting these feature branches keep development organized and simplify reviews.

---

### 4. Branch Naming
Use clear, consistent branch names following the patterns below:
- `feat/` – for new features or enhancements
- `fix/` – for bug fixes
- `docs/` – for documentation updates
- `ci/` – for CI/CD or GitHub Actions changes
- `test/` – for test-related work

Use **kebab-case** (lowercase words separated by hyphens).
Keep names short—no more than five words.

**Examples:**
```
feat/blog-template-update
fix/missing-categories
```

---

### 5. Pull Requests
After completing development, create a **Pull Request (PR)** for review.

Before assigning a reviewer, make sure:
- You have **self-reviewed** your PR to confirm it includes only intended changes.
- All **CI checks** are passing.
- There are **no conflicts** with the target branch.

When creating a PR:
- Reference the related **GitHub Issue**.
- Clearly explain your approach and reasoning.
- Avoid repeating what is already clear from the code.
- Ensure the PR is **ready for review** (not in draft).
- Assign a reviewer:
  - If the reviewer is mentioned in the issue, assign that person.
  - If not, assign [Tarun](https://github.com/tarunnjoshi) as the default reviewer.

It is your responsibility to ensure your PR gets merged.
Follow up respectfully in the Google Chat group if needed.

---

### 6. Coding Style
This project builds on top of **WordPress**, so we will be writing code inside a theme (our own theme or a child theme) or inside our own plugin.
WordPress has well-defined [coding standards](https://developer.wordpress.org/coding-standards/wordpress-coding-standards/).

You are encouraged to read and understand them, but you are not expected to memorize or manually format your code to match them.
Automated tools exist that can be run from the command line to handle formatting.
If you are using **Visual Studio Code**, follow this [guideline](https://github.com/ColoredCow/resources/blob/master/wordpress/WPCS.md) to automatically format PHP code from your editor.

---

### 7. Reviews
If the reviewer leaves comments, always respond collaboratively.
When discussions get long or unclear, consider having a short call instead of extended comment threads.

Once the PR looks good, the reviewer will merge it.
After merging into `develop`, the changes are deployed to the **staging site** for QA review.
After successful QA, they are planned for **release to production**.

---

### 8. Best Practice
Breaking large features into smaller PRs makes reviews faster and easier to understand.
Smaller, focused changes lead to higher-quality feedback and smoother merges.
