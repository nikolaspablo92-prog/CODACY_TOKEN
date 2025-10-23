# GitHub Copilot Instructions

## Project Overview
This is a template repository used in the "[Storing your secrets safely](https://docs.github.com/en/get-started/learning-to-code/storing-your-secrets-safely)" exercise on GitHub Docs. The repository demonstrates best practices for managing secrets in GitHub Actions workflows.

## Purpose
The primary purpose of this repository is to serve as an educational template that teaches developers how to:
- Safely store and use secrets in GitHub Actions
- Configure secrets at the repository level
- Use secrets in workflow files without exposing them
- Implement secure CI/CD practices

## Technology Stack
- **Languages**: C++, C#/.NET
- **Build Systems**: CMake (with Ninja generator), .NET SDK 8.0.x
- **CI/CD**: GitHub Actions
- **Code Analysis**: Codacy (for code quality and coverage analysis)
- **Testing**: .NET test framework with XPlat Code Coverage
- **Tools**: Docker, clang-tidy, reportgenerator

## Important Files and Directories
- `.github/workflows/`: Contains GitHub Actions workflow definitions
  - `ci-build.yml`: Main CI/CD pipeline for building and testing
  - `codacy.yml`: Codacy coverage reporting workflow
  - `comment.yml`: Simple workflow demonstrating secret usage in issue comments
- `README.md`: Repository documentation

## Workflows Structure

### CI Build Workflow (`ci-build.yml`)
- Runs on Windows and Ubuntu
- Uses CMake with Ninja for C++ builds
- Builds .NET projects in Release configuration
- Runs unit and integration tests with coverage
- Generates coverage reports using reportgenerator
- Performs Codacy analysis via Docker

### Codacy Coverage Workflow (`codacy.yml`)
- Runs on push to main branch and pull requests
- Reports code coverage to Codacy

### Comment Workflow (`comment.yml`)
- Demonstrates secret usage by commenting on issues
- Uses `CODACY_TOKEN` secret for authentication

## Secrets Management
This repository requires the following secrets to be configured:
- `CODACY_TOKEN`: Used for Codacy analysis and as a demonstration of secret management in workflows

**Important**: Never hardcode secrets in workflow files. Always use GitHub Secrets and reference them via `${{ secrets.SECRET_NAME }}`.

## Build and Test Instructions
Since this is a template repository, there may not be actual source code present. The workflows reference:
- C++ code built with CMake
- .NET projects at `src/AI.Agent.Core/AI.Agent.Core.csproj`
- Unit tests at `tests/UnitTests/AI.Agent.Core.Tests.csproj`
- Integration tests at `tests/IntegrationTests/AI.Agent.Core.Integration.csproj`

## Coding Standards and Preferences
- Use consistent YAML formatting in workflow files
- Follow GitHub Actions best practices for workflow configuration
- Maintain clear job names and step descriptions
- Use environment variables for configuration values
- Enable parallel execution where possible (`CMAKE_BUILD_PARALLEL_LEVEL: 4`)
- Use matrix strategies for cross-platform builds

## Best Practices for This Repository
1. **Secrets**: Always use GitHub Secrets for sensitive data
2. **Workflows**: Keep workflow files clean and well-documented
3. **Permissions**: Specify minimal required permissions for each job
4. **Caching**: Use `actions/cache` to speed up builds
5. **Error Handling**: Use `|| true` for non-critical steps that may fail
6. **Cross-platform**: Test changes on both Windows and Linux when modifying CI workflows

## When Making Changes
- For workflow modifications: Test changes thoroughly as they affect CI/CD pipeline
- For documentation updates: Ensure clarity for educational purposes
- For adding new workflows: Follow the existing pattern and include appropriate error handling
- When adding dependencies: Update both CMakeLists.txt and .csproj files as needed

## Security Considerations
This repository focuses on secrets management education. When making changes:
- Never commit actual secrets or tokens
- Always reference secrets through GitHub Secrets mechanism
- Review workflow files to ensure no secrets are logged or exposed
- Follow principle of least privilege for workflow permissions
