# Git Workflow Standards for Unified Knowledge Management System

## 🌿 Branch Strategy

### Main Branches
- `main`: Production-ready code, protected
- `develop`: Integration branch for features, protected

### Feature Branches
- Naming: `feature/short-description`
- Branch from: `develop`
- Merge to: `develop` via PR

### Bugfix Branches
- Naming: `bugfix/issue-number-description`
- Branch from: `develop`
- Merge to: `develop` via PR

### Hotfix Branches
- Naming: `hotfix/issue-number-description`
- Branch from: `main`
- Merge to: `main` AND `develop` via PR

## 📝 Commit Strategy

We use **Conventional Commits** for all code changes:

```
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]
```

### Types
- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation changes
- `style`: Formatting changes
- `refactor`: Code change that neither fixes a bug nor adds a feature
- `perf`: Performance improvements
- `test`: Adding or correcting tests
- `build`: Changes to build system or dependencies
- `ci`: Changes to CI configuration
- `chore`: Other changes that don't modify src or test files