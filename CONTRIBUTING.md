# Contributing to Notification Service

First off, thank you for considering contributing to Notification Service! It's people like you that make this service a great tool for everyone. This document provides guidelines and steps for contributing.

## Code of Conduct

By participating in this project, you are expected to uphold our [Code of Conduct](CODE_OF_CONDUCT.md). Please make sure to read and follow it.

## How Can I Contribute?

### Reporting Bugs

This section guides you through submitting a bug report. Following these guidelines helps maintainers and the community understand your report, reproduce the behavior, and find related reports.

**Before Submitting A Bug Report:**

* Check the [issues](https://github.com/yourusername/notification-service/issues) for a list of known issues.
* Perform a [search](https://github.com/yourusername/notification-service/issues) to see if the problem has already been reported. If it has, add a comment to the existing issue instead of opening a new one.
* Ensure the bug is not caused by a third-party provider (SendGrid, Twilio, Firebase) being temporarily unavailable.

**How Do I Submit A Good Bug Report?**

Bugs are tracked as [GitHub issues](https://github.com/yourusername/notification-service/issues). Create an issue and provide the following information:

* **Use a clear and descriptive title** for the issue to identify the problem.
* **Describe the exact steps which reproduce the problem** in as much detail as possible.
* **Provide specific examples to demonstrate the steps**. Include links to files or GitHub projects, or copy/pasteable snippets, which you use in those examples.
* **Describe the behavior you observed after following the steps** and point out what exactly is the problem with that behavior.
* **Explain which behavior you expected to see instead and why.**
* **Include screenshots and animated GIFs** which show you following the described steps and clearly demonstrate the problem.
* **If the problem is related to performance or memory**, include a CPU profile capture with your report.
* **If the problem wasn't triggered by a specific action**, describe what you were doing before the problem happened.

### Suggesting Enhancements

This section guides you through submitting an enhancement suggestion, including completely new features and minor improvements to existing functionality.

**Before Submitting An Enhancement Suggestion:**

* Check the [issues](https://github.com/yourusername/notification-service/issues) for a list of proposed features.
* Perform a [search](https://github.com/yourusername/notification-service/issues) to see if the enhancement has already been suggested. If it has, add a comment to the existing issue instead of opening a new one.

**How Do I Submit A Good Enhancement Suggestion?**

Enhancement suggestions are tracked as [GitHub issues](https://github.com/yourusername/notification-service/issues). Create an issue and provide the following information:

* **Use a clear and descriptive title** for the issue to identify the suggestion.
* **Provide a step-by-step description of the suggested enhancement** in as much detail as possible.
* **Provide specific examples to demonstrate the steps**. Include copy/pasteable snippets which you use in those examples.
* **Describe the current behavior** and **explain which behavior you expected to see instead** and why.
* **Explain why this enhancement would be useful** to most Notification Service users.
* **List some other applications where this enhancement exists** if applicable.
* **Include screenshots and animated GIFs** which help you demonstrate the steps or point out the part which the suggestion is related to.

### Pull Requests

The process described here has several goals:

- Maintain code quality
- Fix problems that are important to users
- Engage the community in working toward the best possible Notification Service
- Enable a sustainable system for maintainers to review contributions

Please follow these steps to have your contribution considered by the maintainers:

1. Follow all instructions in [the template](PULL_REQUEST_TEMPLATE.md)
2. Follow the [styleguides](#styleguides)
3. After you submit your pull request, verify that all [status checks](https://help.github.com/articles/about-status-checks/) are passing

While the prerequisites above must be satisfied prior to having your pull request reviewed, the reviewer(s) may ask you to complete additional design work, tests, or other changes before your pull request can be ultimately accepted.

## Getting Started with Development

### Prerequisites

- .NET 8 SDK
- Docker and Docker Compose
- Your favorite IDE (Visual Studio, VS Code, JetBrains Rider)

### Setting Up the Development Environment

1. Fork the repository
2. Clone your fork locally:
   ```bash
   git clone https://github.com/YOUR_USERNAME/notification-service.git
   cd notification-service
   ```
3. Add the original repository as a remote:
   ```bash
   git remote add upstream https://github.com/yourusername/notification-service.git
   ```
4. Create a branch for your changes:
   ```bash
   git checkout -b feature/your-feature-name
   ```
5. Start the required services with Docker Compose:
   ```bash
   docker-compose -f docker-compose.dev.yml up -d
   ```
6. Build the project:
   ```bash
   dotnet build
   ```
7. Run the tests to make sure everything is working:
   ```bash
   dotnet test
   ```

### Development Workflow

1. Make your changes
2. Test your changes with both unit and integration tests:
   ```bash
   dotnet test
   ```
3. Run code analysis:
   ```bash
   dotnet format
   ```
4. Commit your changes with a descriptive commit message following [conventional commits](https://www.conventionalcommits.org/):
   ```bash
   git commit -m "feat: add support for new notification channel"
   ```
5. Push to your fork:
   ```bash
   git push origin feature/your-feature-name
   ```
6. Create a Pull Request

## Styleguides

### C# Styleguide

* Follow the [Microsoft C# Coding Conventions](https://docs.microsoft.com/en-us/dotnet/csharp/fundamentals/coding-style/coding-conventions)
* Use the `.editorconfig` settings defined in the repository
* Follow the naming conventions used throughout the project
* Use XML documentation comments for public APIs
* Keep methods small and focused on a single responsibility
* Write readable code over clever code

### Unit Test Styleguide

* Test class names should end with `Tests`
* Test method names should be descriptive and follow the pattern `MethodName_Scenario_ExpectedResult`
* Use the AAA (Arrange-Act-Assert) pattern in test methods
* Use mock objects appropriately
* Each test should be independent and not rely on other tests
* Don't test trivial code (e.g., simple getters and setters)

### Documentation Styleguide

* Use [Markdown](https://guides.github.com/features/mastering-markdown/) for documentation
* Use clear, concise language
* Include code examples when relevant
* Update documentation when you change code
* Document public APIs with XML comments

### Commit Message Guidelines

We follow the [Conventional Commits](https://www.conventionalcommits.org/) specification:

* Use the format `<type>(<scope>): <description>`
* Types: `feat`, `fix`, `docs`, `style`, `refactor`, `perf`, `test`, `chore`, etc.
* Scope is optional and should be the name of the component affected
* Description should be in the imperative, present tense: "change" not "changed" nor "changes"
* Don't capitalize the first letter
* No dot (.) at the end

Examples:
```
feat(push): add support for topic-based notifications
fix(email): resolve issue with template variables not being replaced
docs: update README with new environment variables
test(sms): add tests for international number formatting
```

## Branch Naming Convention

* Use lowercase letters, numbers, and hyphens
* Use one of these prefixes:
  * `feature/` for new features
  * `fix/` for bug fixes
  * `docs/` for documentation updates
  * `test/` for test improvements
  * `refactor/` for code refactoring
  * `chore/` for routine tasks, dependency updates, etc.
* Include a brief description of what you're working on
* Include the issue number if applicable

Examples:
```
feature/topic-based-push-notifications
fix/email-template-variable-replacement
docs/update-push-notification-docs
test/sms-international-formatting
refactor/notification-provider-interface
chore/update-sendgrid-package
```

## Adding a New Provider

If you are adding a new notification provider:

1. Create a new class in the `Application/Providers` directory that implements the `INotificationProvider` interface
2. Update the `NotificationChannel` enum in the `Domain/Enums` directory
3. Add provider configuration to the environment variables section in the README
4. Register the provider in the DI container in the `Infrastructure/DependencyInjection` directory
5. Add unit and integration tests for the new provider
6. Update the documentation to include the new provider

## Architecture Guidelines

* Follow Clean Architecture principles
* Keep the domain layer free of infrastructure concerns
* Use dependency injection for all external dependencies
* Ensure proper separation of concerns
* Write code that is testable
* Document architectural decisions in ADRs

## Additional Resources

* [Clean Architecture in .NET](https://docs.microsoft.com/en-us/dotnet/architecture/modern-web-apps-azure/common-web-application-architectures#clean-architecture)
* [Domain-Driven Design](https://docs.microsoft.com/en-us/dotnet/architecture/microservices/microservice-ddd-cqrs-patterns/ddd-oriented-microservice)
* [ASP.NET Core Documentation](https://docs.microsoft.com/en-us/aspnet/core/?view=aspnetcore-6.0)
* [Firebase Cloud Messaging Documentation](https://firebase.google.com/docs/cloud-messaging)
* [SendGrid API Documentation](https://docs.sendgrid.com/api-reference/how-to-use-the-sendgrid-v3-api/authentication)
* [Twilio API Documentation](https://www.twilio.com/docs/api)

## Questions?

If you have any questions, please feel free to create an issue with the label "question" or reach out to the maintainers directly.

Thank you for your contributions!
