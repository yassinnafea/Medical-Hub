# Contributing to Medical Hub

Thank you for your interest in contributing to Medical Hub! We welcome contributions from the community to help us build a better medical management system for Egypt.

## Code of Conduct

- Be respectful and inclusive
- Provide constructive feedback
- Focus on the work, not the person
- Help others succeed

## Getting Started

### Prerequisites
- Node.js 16+
- PostgreSQL 13+
- Docker (optional)
- Git

### Setup Development Environment

1. **Fork the repository**
   ```bash
   git clone https://github.com/YOUR_USERNAME/Medical-Hub.git
   cd Medical-Hub
   ```

2. **Create a development branch**
   ```bash
   git checkout -b feature/your-feature-name
   ```

3. **Install dependencies**
   ```bash
   npm install
   ```

4. **Setup environment**
   ```bash
   cp .env.example .env
   # Edit .env with your local settings
   ```

5. **Start development**
   ```bash
   npm run dev
   ```

## Development Workflow

### Making Changes

1. **Create a feature branch**
   ```bash
   git checkout -b feature/descriptive-name
   # or
   git checkout -b fix/descriptive-name
   ```

2. **Make your changes**
   - Follow the coding standards (see below)
   - Write clear, descriptive commit messages
   - Make small, focused commits

3. **Test your changes**
   ```bash
   npm test
   npm run lint
   ```

4. **Push to your fork**
   ```bash
   git push origin feature/descriptive-name
   ```

5. **Create a Pull Request**
   - Provide a clear description
   - Reference related issues
   - Include screenshots for UI changes

## Coding Standards

### TypeScript
- Use strict mode
- Define types explicitly
- Use interfaces for object shapes
- Avoid `any` type

### React Components
```typescript
interface ComponentProps {
  title: string;
  onClose?: () => void;
}

export const MyComponent: React.FC<ComponentProps> = ({ title, onClose }) => {
  return <div>{title}</div>;
};
```

### Naming Conventions
- Files: `PascalCase.tsx` for components, `camelCase.ts` for utilities
- Functions: `camelCase`
- Constants: `UPPER_SNAKE_CASE`
- Components: `PascalCase`

### Commit Messages
```
type(scope): brief description

Detailed explanation if needed.
Fixes #123
```

Types: `feat`, `fix`, `docs`, `style`, `refactor`, `test`, `chore`

### Code Comments
```typescript
// Use clear, meaningful comments
// Explain WHY, not WHAT

/**
 * Calculate patient age from date of birth
 * @param dateOfBirth - Patient's date of birth
 * @returns Age in years
 */
function calculateAge(dateOfBirth: Date): number {
  // Implementation
}
```

## Testing

### Unit Tests
```bash
npm run test
```

### Test Coverage
- Aim for >80% coverage
- Test critical paths
- Test error cases

### Example Test
```typescript
describe('calculateAge', () => {
  it('should calculate age correctly', () => {
    const dob = new Date('1990-01-01');
    expect(calculateAge(dob)).toBeGreaterThan(30);
  });
});
```

## Pull Request Process

1. **Before submitting:**
   - Ensure code passes linting: `npm run lint`
   - Ensure tests pass: `npm run test`
   - Update documentation if needed
   - Rebase on latest main

2. **PR Description should include:**
   - What changes were made
   - Why the changes were made
   - Related issues (e.g., Fixes #123)
   - Testing performed
   - Screenshots for UI changes

3. **PR Title format:**
   ```
   feat(patients): add patient filtering by specialization
   fix(appointments): resolve scheduling conflict bug
   docs(api): update authentication endpoint documentation
   ```

4. **Reviewers will:**
   - Review code quality
   - Check for security issues
   - Verify functionality
   - Request changes if needed

## Documentation

### Code Documentation
- Add JSDoc comments to functions
- Document complex logic
- Include examples for utilities

### Markdown Documentation
- Use clear, concise language
- Include code examples
- Use headers for organization
- Link to related documents

### Example Documentation
```markdown
## Patient Management

### Creating a Patient

To create a new patient record:

\`\`\`typescript
const patient = await createPatient({
  firstName: 'Ahmed',
  lastName: 'Ali',
  email: 'ahmed@example.com',
  // ... other fields
});
\`\`\`
```

## Issue Guidelines

### Reporting Bugs
Include:
- Description of the bug
- Steps to reproduce
- Expected behavior
- Actual behavior
- Environment (OS, browser, etc.)
- Screenshots if applicable

### Feature Requests
Include:
- Clear description
- Use case/motivation
- Possible implementation
- Related issues

## Review Process

1. **Automated Checks**
   - Linting
   - Testing
   - Build validation

2. **Code Review**
   - At least one maintainer review
   - Community feedback
   - Discussion if needed

3. **Approval & Merge**
   - All checks passing
   - Approval from maintainer
   - Squash and merge

## Style Guide

### Formatting
- 2 spaces for indentation
- Max line length: 100 characters
- Use single quotes for strings
- Trailing comma in objects/arrays

### React Patterns
```typescript
// Good: Functional component with hooks
const PatientList: React.FC = () => {
  const [patients, setPatients] = useState<Patient[]>([]);
  
  useEffect(() => {
    fetchPatients();
  }, []);
  
  return <div>{patients.map(p => <Patient key={p.id} {...p} />)}</div>;
};

// Avoid: Class components, complex prop drilling
```

### Express Patterns
```typescript
// Good: Async/await with error handling
router.get('/:id', async (req, res, next) => {
  try {
    const patient = await Patient.findById(req.params.id);
    res.json(patient);
  } catch (error) {
    next(error);
  }
});
```

## Performance Guidelines

- Use React.memo for expensive components
- Implement code splitting
- Optimize database queries
- Cache where appropriate
- Use lazy loading for routes

## Security Guidelines

- Never commit sensitive data
- Validate all inputs
- Use parameterized queries
- Sanitize user input
- Keep dependencies updated
- Use environment variables for secrets

## Resources

- [TypeScript Documentation](https://www.typescriptlang.org/docs/)
- [React Documentation](https://react.dev/)
- [Express Documentation](https://expressjs.com/)
- [PostgreSQL Documentation](https://www.postgresql.org/docs/)

## Getting Help

- Check existing issues and discussions
- Ask in GitHub Discussions
- Contact maintainers
- Review documentation

## Recognition

Contributors will be recognized in:
- README contributors section
- Changelog
- Release notes

Thank you for contributing to Medical Hub! 🏥✨
