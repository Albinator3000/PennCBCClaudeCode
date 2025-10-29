# Productivity App - Claude Development Guide

## Project Overview

This is a modern productivity application designed to help users manage tasks, track time, and organize projects. The app emphasizes simplicity, speed, and cross-platform compatibility.

**Core Features:**
- Task management with priorities and due dates
- Time tracking and analytics
- Project organization with folders/tags
- Calendar integration
- Collaborative features (sharing, comments)
- Offline-first architecture

## Architecture

**Tech Stack:**
- **Frontend:** React 18 with TypeScript
- **State Management:** Zustand for global state
- **Styling:** Tailwind CSS with custom design system
- **Backend:** Node.js with Express
- **Database:** PostgreSQL with Prisma ORM
- **Real-time:** WebSocket for live updates
- **Testing:** Jest + React Testing Library
- **Build:** Vite

**Project Structure:**
```
/src
  /components     # Reusable UI components
  /features       # Feature-specific modules (tasks, projects, timer)
  /hooks          # Custom React hooks
  /lib            # Utilities and helpers
  /services       # API clients and business logic
  /store          # State management
  /types          # TypeScript type definitions
/server
  /controllers    # Request handlers
  /models         # Database models
  /routes         # API routes
  /middleware     # Express middleware
  /services       # Business logic
/tests            # Test files mirror source structure
```

## Code Style & Conventions

### General Principles
- **DRY:** Don't repeat yourself - extract reusable logic
- **Single Responsibility:** Each function/component does one thing well
- **Descriptive Naming:** Use clear, intention-revealing names
- **Small Functions:** Keep functions under 50 lines when possible

### TypeScript Guidelines
- Always use explicit types (avoid `any`)
- Use interfaces for objects, types for unions
- Export types alongside implementations
- Use strict mode (`strict: true` in tsconfig)

### React Patterns
- Functional components only (no class components)
- Custom hooks for reusable logic (prefix with `use`)
- Keep components small (< 200 lines)
- Props destructuring in function signature
- Use React.memo() for expensive renders only

### Naming Conventions
- **Components:** PascalCase (`TaskCard`, `ProjectList`)
- **Files:** kebab-case for utilities, PascalCase for components
- **Functions:** camelCase (`handleSubmit`, `calculateDuration`)
- **Constants:** UPPER_SNAKE_CASE (`MAX_TASKS`, `API_BASE_URL`)
- **Hooks:** camelCase with `use` prefix (`useTaskFilter`, `useTimer`)

### File Organization
- One component per file
- Co-locate tests with source files (`task-card.test.tsx` next to `task-card.tsx`)
- Index files for clean exports from directories
- Group related utilities in `/lib`

## Testing Strategy

### Test Coverage Requirements
- **Minimum:** 80% coverage for all new code
- **Critical Paths:** 100% coverage for auth, data persistence, payment
- **Unit Tests:** All utility functions and hooks
- **Component Tests:** User interactions and state changes
- **Integration Tests:** API endpoints and database operations

### Testing Patterns
```typescript
// Component Test Structure
describe('TaskCard', () => {
  it('renders task title and description', () => {
    // Arrange
    const task = mockTask();
    
    // Act
    render(<TaskCard task={task} />);
    
    // Assert
    expect(screen.getByText(task.title)).toBeInTheDocument();
  });
});
```

### Test-Driven Development
When adding new features:
1. Write tests describing expected behavior FIRST
2. Run tests and confirm they fail
3. Implement minimum code to make tests pass
4. Refactor while keeping tests green
5. Add edge case tests as needed

## Common Workflows

### Adding a New Feature
1. Create feature branch: `git checkout -b feature/task-subtasks`
2. Read relevant code in `/features` directory
3. Create tests in parallel with implementation
4. Update TypeScript types in `/types`
5. Add API endpoints if needed (follow REST conventions)
6. Update documentation in feature README
7. Run full test suite before committing
8. Create PR with description of changes

### Database Changes
1. Create Prisma migration: `npx prisma migrate dev --name add_subtasks`
2. Update Prisma schema in `/prisma/schema.prisma`
3. Regenerate Prisma client: `npx prisma generate`
4. Update TypeScript types to match schema
5. Write migration tests
6. Document schema changes in `/docs/database.md`

### API Endpoint Pattern
```typescript
// Follow this structure for consistency
router.post('/api/tasks', 
  authenticate,              // Auth middleware
  validateTaskInput,         // Validation middleware
  async (req, res) => {
    try {
      const task = await taskService.create(req.body, req.user.id);
      res.status(201).json({ data: task });
    } catch (error) {
      handleError(error, res);
    }
  }
);
```

### Component Development Pattern
1. Create component file in appropriate feature folder
2. Define props interface
3. Implement component logic
4. Add accessibility attributes (ARIA labels, keyboard nav)
5. Write component tests
6. Add to Storybook if UI component
7. Document props and usage

## External Dependencies & APIs

### Environment Variables
- `DATABASE_URL`: PostgreSQL connection string
- `JWT_SECRET`: Token signing secret
- `API_BASE_URL`: Backend API endpoint
- `STRIPE_API_KEY`: Payment processing (optional)
- `SENDGRID_API_KEY`: Email notifications (optional)

### Third-Party Services
- **Authentication:** JWT-based auth (consider Auth0 for OAuth)
- **File Storage:** AWS S3 or Cloudflare R2 for attachments
- **Email:** SendGrid for notifications
- **Analytics:** PostHog for product analytics
- **Error Tracking:** Sentry for production monitoring

### API Rate Limits
- GitHub API: 5000 requests/hour (authenticated)
- SendGrid: 100 emails/day (free tier)
- Implement exponential backoff for all external API calls

## Development Guidelines

### Git Workflow
- Branch naming: `feature/`, `bugfix/`, `hotfix/`
- Commit messages: Follow Conventional Commits
  - `feat:` New features
  - `fix:` Bug fixes
  - `docs:` Documentation changes
  - `refactor:` Code refactoring
  - `test:` Test additions/changes
- Squash commits before merging to main
- Keep commits atomic and focused

### Code Review Checklist
- [ ] Tests pass (`npm test`)
- [ ] No TypeScript errors (`npm run type-check`)
- [ ] Linting passes (`npm run lint`)
- [ ] Code follows style guidelines
- [ ] Functions have JSDoc comments
- [ ] No console.logs in production code
- [ ] Accessibility requirements met
- [ ] Performance impact considered
- [ ] Security implications reviewed

### Performance Considerations
- Lazy load routes with React.lazy()
- Optimize images (use WebP, lazy loading)
- Debounce search inputs (300ms)
- Virtualize long lists (react-window)
- Memoize expensive calculations
- Use Web Workers for heavy computation

### Security Best Practices
- Sanitize all user inputs
- Use parameterized queries (Prisma handles this)
- Implement CSRF protection
- Rate limit API endpoints
- Validate JWTs on every protected route
- Never log sensitive data
- Use HTTPS in production
- Implement Content Security Policy headers

## Common Issues & Solutions

### Database Connection Errors
If you see "Can't reach database server":
- Check `DATABASE_URL` in `.env`
- Ensure PostgreSQL is running: `brew services list`
- Reset database: `npx prisma migrate reset`

### Build Failures
- Clear cache: `rm -rf node_modules/.cache`
- Reinstall dependencies: `rm -rf node_modules && npm install`
- Check for TypeScript errors: `npm run type-check`

### Test Failures
- Update snapshots if UI changed: `npm test -- -u`
- Clear Jest cache: `npx jest --clearCache`
- Check for async timing issues (add `waitFor` where needed)

## Helpful Commands

```bash
# Development
npm run dev              # Start dev server (frontend + backend)
npm run dev:frontend     # Frontend only
npm run dev:backend      # Backend only

# Testing
npm test                 # Run all tests
npm run test:watch       # Watch mode
npm run test:coverage    # Coverage report

# Database
npx prisma studio        # Open database GUI
npx prisma migrate dev   # Run pending migrations
npx prisma db seed       # Seed database with test data

# Code Quality
npm run lint             # ESLint check
npm run lint:fix         # Auto-fix linting issues
npm run type-check       # TypeScript validation
npm run format           # Prettier formatting

# Build
npm run build            # Production build
npm run preview          # Preview production build
```

## Additional Resources

- [React Best Practices](https://react.dev/learn)
- [TypeScript Do's and Don'ts](https://www.typescriptlang.org/docs/handbook/declaration-files/do-s-and-don-ts.html)
- [Prisma Documentation](https://www.prisma.io/docs)
- [Testing Library Queries](https://testing-library.com/docs/queries/about)
- Internal docs: `/docs` directory

## Notes for AI Assistants

When implementing features:
1. **Always read existing code first** to understand patterns
2. **Prioritize test-driven development** - write tests before implementation
3. **Follow existing naming conventions** - consistency is key
4. **Ask for clarification** if requirements are ambiguous
5. **Consider edge cases** - null values, empty arrays, API failures
6. **Optimize for readability** over cleverness
7. **Document complex logic** with comments
8. **Check TypeScript types** - no implicit any
9. **Run tests locally** before committing
10. **Update this CLAUDE.md** if you discover better patterns
