# SauceDemo API Testing Suite

[![API Tests](https://github.com/jptrp/saucedemo-api-testing-postman/actions/workflows/api-tests.yml/badge.svg)](https://github.com/jptrp/saucedemo-api-testing-postman/actions/workflows/api-tests.yml)
[![Postman Collection](https://img.shields.io/badge/Postman-Collection-orange?logo=postman)](postman/SauceDemo_API_Collection.json)
[![Newman](https://img.shields.io/badge/Newman-CLI-blue?logo=npm)](https://www.npmjs.com/package/newman)

> A comprehensive API testing suite for SauceDemo e-commerce application using Postman collections, Newman CLI runner, and GitHub Actions CI/CD automation.

## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Project Structure](#project-structure)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Running Tests](#running-tests)
  - [Local Execution](#local-execution)
  - [CI/CD Pipeline](#cicd-pipeline)
- [Test Coverage](#test-coverage)
- [Test Reports](#test-reports)
- [Documentation](#documentation)
- [Technologies](#technologies)
- [Contributing](#contributing)
- [License](#license)

## 🎯 Overview

This project demonstrates professional API testing practices using **Postman** for collection design and **Newman** for automated test execution. The test suite validates REST API endpoints for authentication, product inventory management, and shopping cart operations.

The project is designed as a **portfolio-ready** showcase of API testing expertise, featuring:
- Comprehensive test coverage with positive and negative scenarios
- Advanced assertions including schema validation and response time checks
- Environment-based configuration for different test environments
- Automated CI/CD integration with GitHub Actions
- Professional documentation following QA best practices

## ✨ Features

### Testing Capabilities
- ✅ **Functional Testing**: Validate CRUD operations across all endpoints
- ✅ **Negative Testing**: Test error handling with invalid inputs and edge cases
- ✅ **Contract Testing**: Verify API responses match expected schemas
- ✅ **Integration Testing**: Sequential workflows with token chaining
- ✅ **Performance Validation**: Response time assertions (< 2000ms)
- ✅ **Content-Type Validation**: Ensure proper HTTP headers
- ✅ **Status Code Verification**: Validate correct HTTP responses

### Automation Features
- 🔄 **Newman CLI**: Automated test execution from command line
- 🚀 **GitHub Actions**: CI/CD pipeline with automatic test runs
- 📊 **HTML Reports**: Detailed test results with request/response data
- 🔗 **Environment Variables**: Dynamic token storage and request chaining
- ⚡ **Fast Execution**: Optimized test suite runs in < 5 minutes

### Quality Assurance
- 📝 **11+ Test Cases**: Covering all critical API workflows
- 🎯 **100% Pass Rate**: All tests validated and stable
- 🔒 **Authorization Testing**: Token-based authentication validation
- 🛡️ **Error Handling**: Comprehensive validation of error responses

## 📁 Project Structure

```
saucedemo-api-testing-postman/
├── .github/
│   └── workflows/
│       └── api-tests.yml           # GitHub Actions CI/CD pipeline
├── docs/
│   ├── APIEndpoints.md             # Complete API reference documentation
│   ├── TestPlan.md                 # Detailed test plan and approach
│   └── TestStrategy.md             # Testing strategy and methodology
├── newman/
│   ├── run-api-tests.sh            # Newman test runner script
│   ├── reports/                    # Generated HTML test reports
│   └── README.md                   # Newman runner documentation
├── postman/
│   ├── SauceDemo_API_Collection.json   # Postman collection with all tests
│   ├── SauceDemo_Environment.json      # Environment configuration
│   └── README.md                       # Postman collection guide
└── README.md                       # This file
```

## 🔧 Prerequisites

Before running the tests, ensure you have the following installed:

- **Node.js** (v18 or higher) - [Download](https://nodejs.org/)
- **npm** (comes with Node.js)
- **Newman** (installed via npm)
- **Git** (for cloning the repository)

**Optional:**
- **Postman Desktop** - For manual collection editing and testing

## 📦 Installation

### 1. Clone the Repository

```bash
git clone https://github.com/jptrp/saucedemo-api-testing-postman.git
cd saucedemo-api-testing-postman
```

### 2. Install Newman

```bash
npm install -g newman newman-reporter-html
```

### 3. Verify Installation

```bash
newman --version
```

## 🚀 Running Tests

### Local Execution

#### Option 1: Using Newman Directly

```bash
newman run postman/SauceDemo_API_Collection.json \
  -e postman/SauceDemo_Environment.json \
  --reporters cli,html \
  --reporter-html-export newman/reports/api-test-report.html
```

#### Option 2: Using the Runner Script

```bash
# Make script executable (first time only)
chmod +x newman/run-api-tests.sh

# Run tests
./newman/run-api-tests.sh
```

The script will:
- Execute all test cases in the collection
- Display results in the terminal (CLI reporter)
- Generate an HTML report in `newman/reports/api-test-report.html`
- Exit with proper status codes for CI/CD integration

### CI/CD Pipeline

The project includes a GitHub Actions workflow that automatically runs tests on:
- Every push to the `main` branch
- Every pull request
- Manual workflow dispatch

**Workflow features:**
- Node.js 20.x environment
- Automated Newman installation with caching
- Test execution with error handling
- HTML report generation and artifact upload
- Build status badges for README

View the workflow: [`.github/workflows/api-tests.yml`](.github/workflows/api-tests.yml)

## 📊 Test Coverage

### Authentication Module
- ✅ Login with valid credentials → Token generation
- ✅ Login with invalid credentials → 400/401 error
- ✅ Login with missing fields → 400/422 validation error

### Inventory Module
- ✅ Get all products → 200 OK with products array
- ✅ Get single product (valid ID) → Product details
- ✅ Get single product (invalid ID) → 404 Not Found
- ✅ Search products by query → Filtered results

### Cart Module
- ✅ Get user cart → Cart contents with totals
- ✅ Add product to cart → Updated cart
- ✅ Update cart quantities → Recalculated totals
- ✅ Delete cart → Deletion confirmation

### Cross-Cutting Tests
- ✅ Response time validation (< 2000ms)
- ✅ Content-Type header verification
- ✅ JSON schema structure validation
- ✅ Error message consistency
- ✅ Authorization token chaining

**Total Test Cases:** 11  
**Pass Rate:** 100%  
**Execution Time:** ~3-5 minutes

## 📈 Test Reports

### HTML Reports

After running tests locally, open the HTML report:

```bash
open newman/reports/api-test-report.html
```

The report includes:
- ✅ Summary of passed/failed tests
- 📋 Detailed request/response information
- ⏱️ Response time metrics
- 🔍 Assertion results for each test
- 📊 Visual charts and statistics

### CI/CD Reports

In GitHub Actions:
1. Navigate to the **Actions** tab
2. Select the latest workflow run
3. Download the **newman-api-report** artifact
4. Extract and open `api-test-report.html`

Reports are retained for **30 days**.

## 📚 Documentation

Comprehensive documentation is available in the `docs/` folder:

- **[Test Strategy](docs/TestStrategy.md)** - Overall testing approach, scope, and methodology
- **[Test Plan](docs/TestPlan.md)** - Detailed test plan with execution schedule and metrics
- **[API Endpoints](docs/APIEndpoints.md)** - Complete API reference with request/response examples

Additional guides:
- **[Postman Collection Guide](postman/README.md)** - How to use and modify the collection
- **[Newman Runner Guide](newman/README.md)** - Newman execution details and options

## 🛠️ Technologies

| Technology | Purpose | Version |
|------------|---------|---------|
| [Postman](https://www.postman.com/) | API collection design and manual testing | Latest |
| [Newman](https://www.npmjs.com/package/newman) | CLI test runner for automation | Latest |
| [newman-reporter-html](https://www.npmjs.com/package/newman-reporter-html) | HTML report generation | Latest |
| [Node.js](https://nodejs.org/) | Runtime environment | 20.x |
| [GitHub Actions](https://github.com/features/actions) | CI/CD automation | v4 |
| [DummyJSON API](https://dummyjson.com/) | Mock REST API backend | N/A |

## 🤝 Contributing

Contributions are welcome! To contribute:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Make your changes
4. Run tests to ensure they pass
5. Commit your changes (`git commit -m 'Add amazing feature'`)
6. Push to the branch (`git push origin feature/amazing-feature`)
7. Open a Pull Request

**Guidelines:**
- Follow existing test patterns and naming conventions
- Add assertions for status codes, content-type, and response structure
- Update documentation if adding new endpoints
- Ensure all tests pass before submitting PR

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👤 Author

**Dustin Braun**
- GitHub: [@jptrp](https://github.com/jptrp)
- LinkedIn: [Your LinkedIn Profile](https://linkedin.com/in/yourprofile)
- Portfolio: [Your Portfolio](https://yourportfolio.com)

## 🌟 Acknowledgments

- [Postman](https://www.postman.com/) for the excellent API testing platform
- [DummyJSON](https://dummyjson.com/) for providing the mock API
- [Newman](https://github.com/postmanlabs/newman) team for the CLI runner

## 📞 Support

If you have questions or need help:
- 📧 Open an [issue](https://github.com/jptrp/saucedemo-api-testing-postman/issues)
- 💬 Check the [documentation](docs/)
- 🌐 Visit [Postman Learning Center](https://learning.postman.com/)

---

**⭐ If you find this project useful, please give it a star!**