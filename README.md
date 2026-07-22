# TWO-MONTH QA ENGINEER INTERNSHIP REPORT

## Intern Details

**Name:** Abhishek Pradhan
**Position:** QA Engineer Intern
**Duration:** Two Months

---

# 1. Introduction

This report summarizes my two-month internship as a QA Engineer. During this period, I gained practical experience in software testing, database validation, API testing, automation testing, and deployment verification. I worked with SQL Server databases, .NET backend APIs, frontend applications, Playwright automation, GitHub, and CI/CD pipelines.

The internship provided hands-on exposure to the Software Development Life Cycle (SDLC) and Software Testing Life Cycle (STLC). I learned how quality assurance activities help ensure software reliability before production deployment.

---

# 2. Objectives of the Internship

The primary objectives of the internship were:

* Understand the software development and testing process.
* Learn manual and automation testing techniques.
* Validate data stored in SQL Server databases.
* Test .NET backend APIs.
* Perform frontend UI testing.
* Create and execute Playwright automation scripts.
* Participate in pre-deployment testing activities.
* Gain exposure to CI/CD pipelines.
* Improve bug reporting and documentation skills.

---

# 3. Technologies and Tools Used

## Testing Tools

* Playwright
* Postman
* Chrome DevTools
* Swagger

## Development Tools

* Visual Studio
* Visual Studio Code

## Database

* Microsoft SQL Server
* SQL Server Management Studio (SSMS)

## Programming Languages

* TypeScript
* JavaScript
* SQL
* C#

## Version Control

* Git
* GitHub

## CI/CD Tools

* Azure DevOps
* GitHub Actions

---

# 4. Understanding the Application Architecture

The application architecture tested during the internship followed the structure below:

```text
Frontend Application
        ↓
.NET Backend API
        ↓
SQL Server Database
```

As a QA Engineer, I validated each layer to ensure data accuracy and proper functionality before deployment.

---

# 5. Database Testing Using SQL Server (SSMS)

Database testing was an important part of my responsibilities. I used SQL Server Management Studio (SSMS) to verify data stored in the database and compare it with API responses.

## Sample Employee Table

```sql
CREATE TABLE Employees (
    EmployeeId INT PRIMARY KEY,
    EmployeeName VARCHAR(100),
    Department VARCHAR(50),
    Salary DECIMAL(10,2)
);
```

## Sample Data

```sql
INSERT INTO Employees
VALUES
(1,'John Smith','IT',50000),
(2,'Sarah Khan','HR',45000),
(3,'David Lee','Finance',60000);
```

## Verification Query

```sql
SELECT EmployeeId,
       EmployeeName,
       Department,
       Salary
FROM Employees;
```

## Activities Performed

* Verified database records.
* Validated inserted and updated data.
* Executed SQL queries.
* Checked relationships between tables.
* Compared database records with API responses.
* Confirmed data consistency before deployment.

---

# 6. .NET Backend API Testing

The backend application was developed using .NET APIs. These APIs retrieved data from SQL Server and provided responses to the frontend application.

## Employee Model

```csharp
public class Employee
{
    public int EmployeeId { get; set; }

    public string EmployeeName { get; set; }

    public string Department { get; set; }

    public decimal Salary { get; set; }
}
```

## Employee Controller

```csharp
using Microsoft.AspNetCore.Mvc;

[ApiController]
[Route("api/[controller]")]
public class EmployeesController : ControllerBase
{
    [HttpGet]
    public IActionResult GetEmployees()
    {
        var employees = new List<Employee>
        {
            new Employee
            {
                EmployeeId = 1,
                EmployeeName = "John Smith",
                Department = "IT",
                Salary = 50000
            },
            new Employee
            {
                EmployeeId = 2,
                EmployeeName = "Sarah Khan",
                Department = "HR",
                Salary = 45000
            }
        };

        return Ok(employees);
    }
}
```

## API Endpoint

```http
GET https://localhost:5001/api/employees
```

## Sample API Response

```json
[
  {
    "employeeId": 1,
    "employeeName": "John Smith",
    "department": "IT",
    "salary": 50000
  },
  {
    "employeeId": 2,
    "employeeName": "Sarah Khan",
    "department": "HR",
    "salary": 45000
  }
]
```

## API Validation Activities

* Verified status codes.
* Validated JSON responses.
* Checked API response time.
* Compared API responses with SQL Server records.
* Tested error handling.
* Verified authentication and authorization.

---

# 7. Data Flow Validation

One of my major responsibilities was validating data flow from SQL Server to the frontend application.

## Data Flow Process

```text
SQL Server Database
        ↓
.NET Backend API
        ↓
JSON Response
        ↓
Frontend Application
        ↓
QA Validation
        ↓
Deployment
```

## Validation Steps

1. Verify records in SSMS.
2. Run backend APIs locally.
3. Send requests using Postman or Playwright.
4. Compare API response with database data.
5. Verify frontend displays correct information.
6. Execute automation tests.
7. Approve deployment after successful validation.

---

# 8. Frontend Testing

Frontend testing ensured that users could interact with the application successfully.

## Modules Tested

* Login Page
* Registration Page
* Dashboard
* Employee Management
* Search Functionality
* Navigation Menu
* Profile Page

## Activities Performed

* UI validation
* Form validation
* Browser compatibility testing
* Responsive testing
* Functional testing
* Regression testing

---

# 9. Playwright Automation Testing

I learned Playwright automation using the Page Object Model (POM) framework.

## Features Automated

* Login
* Registration
* Search
* Product Comparison
* Reviews
* Employee Data Validation

---

## Playwright POM Example

```typescript
import { Page } from '@playwright/test';

export class LoginPage {

    constructor(private page: Page) {}

    async navigate() {
        await this.page.goto('https://www.saucedemo.com/');
    }

    async login(username: string, password: string) {

        await this.page.fill('#user-name', username);

        await this.page.fill('#password', password);

        await this.page.click('#login-button');
    }
}
```

---

## Playwright Login Test

```typescript
import { test, expect } from '@playwright/test';

test('Verify Login', async ({ page }) => {

    await page.goto('https://www.saucedemo.com/');

    await page.fill('#user-name', 'standard_user');

    await page.fill('#password', 'secret_sauce');

    await page.click('#login-button');

    await expect(page).toHaveURL(/inventory/);
});
```

---

## Playwright API Test

```typescript
import { test, expect } from '@playwright/test';

test('Verify Employee API Data', async ({ request }) => {

    const response = await request.get(
        'https://localhost:5001/api/employees'
    );

    expect(response.status()).toBe(200);

    const data = await response.json();

    expect(data.length).toBeGreaterThan(0);

    expect(data[0].employeeName).toBe('John Smith');

    expect(data[0].department).toBe('IT');
});
```

---

# 10. Pre-Deployment Testing

Before every deployment, testing activities were performed to ensure application stability.

## Pre-Deployment Process

1. Database Validation
2. API Validation
3. Frontend Validation
4. Smoke Testing
5. Regression Testing
6. Automation Execution
7. Bug Verification
8. Deployment Approval

## Deployment Checklist

| Test Area             | Status |
| --------------------- | ------ |
| Database Testing      | Passed |
| API Testing           | Passed |
| UI Testing            | Passed |
| Smoke Testing         | Passed |
| Regression Testing    | Passed |
| Automation Testing    | Passed |
| Deployment Validation | Passed |

---

# 11. CI/CD Pipeline Exposure

I gained practical exposure to Continuous Integration and Continuous Deployment (CI/CD).

## Activities Performed

* Understanding build pipelines.
* Reviewing build logs.
* Monitoring deployment status.
* Running automated Playwright tests in pipelines.
* Investigating failed builds.
* Supporting release validation.

## Benefits Observed

* Faster releases.
* Reduced manual effort.
* Early bug detection.
* Improved software quality.
* Continuous validation of application functionality.

---

# 12. Defect Management

During testing, defects were identified, documented, and tracked.

## Defect Lifecycle

```text
Defect Found
      ↓
Reported
      ↓
Assigned
      ↓
Fixed
      ↓
Retested
      ↓
Closed
```

## Information Included in Bug Reports

* Bug ID
* Module Name
* Steps to Reproduce
* Expected Result
* Actual Result
* Severity
* Priority
* Screenshot Evidence

---

# 13. Skills Developed

## Technical Skills

* SQL Server
* SSMS
* SQL Queries
* .NET API Testing
* Playwright Automation
* TypeScript
* API Validation
* Postman
* GitHub
* CI/CD Validation

## Soft Skills

* Teamwork
* Communication
* Problem Solving
* Time Management
* Documentation
* Analytical Thinking

---

# 14. What I Learned

* Database testing using SQL Server.
* API testing using Postman and Playwright.
* Frontend and backend integration testing.
* Playwright automation framework with POM.
* Pre-deployment testing strategies.
* CI/CD workflow and automated testing.
* Bug reporting and defect management.
* End-to-end application validation.

---

# 15. What I Liked

* Building Playwright automation frameworks.
* Validating data flow from database to frontend.
* Learning .NET backend API testing.
* Working with SQL Server.
* Understanding deployment processes.
* Receiving mentorship from experienced engineers.

---

# 16. Challenges Faced

* Initial Playwright setup and configuration.
* Debugging automation failures.
* Understanding CI/CD pipeline errors.
* Managing test data across environments.
* Learning backend and frontend testing simultaneously.

---

# 17. Office Environment

The working environment was professional, collaborative, and supportive.

### Observations

* Friendly team culture.
* Helpful senior engineers.
* Open communication.
* Learning-oriented environment.
* Encouragement to explore new technologies.

The positive atmosphere helped me improve both technical and interpersonal skills.

---

# 18. Conclusion

The two-month QA Engineer internship provided valuable industry experience in software quality assurance. I gained practical knowledge of SQL Server database testing, .NET backend API validation, frontend testing, Playwright automation, CI/CD processes, and pre-deployment verification.

By validating data from SQL Server through backend APIs and ensuring correct frontend behavior, I learned the importance of quality assurance in delivering reliable software. This internship strengthened my technical expertise, improved my problem-solving abilities, and prepared me for future opportunities in Quality Assurance and Test Automation Engineering.

