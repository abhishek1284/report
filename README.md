# - Two Month QA Engineer Report

##  What I Learned
- **Playwright Automation (POM):**
  - Built Page Object Model (POM) classes for login, registration, reviews, search, and product comparison.
  - Practiced writing reusable selectors and methods for test scalability.
- **Pre-Deployment Testing:**
  - Automated tests before deployment to catch regressions early.
  - Validated both **frontend (UI)** and **backend (API)** layers.
- **.NET Project Testing:**
  - Ran projects locally in Visual Studio using IIS Express and localhost.
  - Wrote test cases for backend services and integrated them with frontend flows.
- **CI/CD Pipeline:**
  - Learned how to configure pipelines for automated builds and deployments.
  - Integrated Playwright tests into CI/CD for continuous validation.

## What I Liked
- Building modular Playwright POM classes improved my confidence in automation.
- CI/CD integration showed how QA fits into DevOps workflows.
- Exposure to both backend and frontend testing gave me a full-stack QA perspective.
- Supportive team culture made learning smoother.

##  What I Didn’t Like
- Initial Playwright setup was time-consuming.
- Debugging CI/CD pipeline errors required extra guidance.
- Switching between backend and frontend testing was overwhelming at times.
- Documentation gaps slowed down progress.

## Office Environment
- Friendly and collaborative team atmosphere.
- Seniors are approachable and provide mentorship.
- Encouragement to experiment and learn from mistakes.
- Balanced focus on productivity and learning.

---

##  Sample Code Snippets

### Playwright POM Example (Login Page)
```typescript
// login.page.ts
import { Page } from '@playwright/test';

export class LoginPage {
  constructor(private page: Page) {}

  async goto() {
    await this.page.goto('https://www.saucedemo.com/');
  }

  async login(username: string, password: string) {
    await this.page.fill('#user-name', username);
    await this.page.fill('#password', password);
    await this.page.click('#login-button');
  }

  async getErrorMessage() {
    return this.page.textContent('[data-test="error"]');
  }
}

