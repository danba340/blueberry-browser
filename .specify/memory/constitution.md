<!--
Sync Impact Report:
Version change: initial → 1.0.0
Added principles: 
- Code Quality & Type Safety
- Verification & Debugging First  
- User Experience Consistency
- Performance Requirements
- End-to-End Validation
Added sections:
- Development Standards
- Quality Assurance
Templates requiring updates:
✅ Updated plan-template.md (Constitution Check section alignment)
✅ Updated spec-template.md (testability requirements alignment)  
✅ Updated tasks-template.md (verification and E2E testing integration)
Follow-up TODOs: None
-->

# Blueberry Browser Constitution

## Core Principles

### I. Code Quality & Type Safety (NON-NEGOTIABLE)
All code MUST be strongly typed with comprehensive type definitions; TypeScript strict mode enabled across frontend and backend; No implicit 'any' types permitted without explicit justification; All functions, variables, and interfaces must have clear type signatures; Type definitions must be documented with JSDoc comments explaining purpose and constraints.

**Rationale**: Type safety prevents runtime errors, improves code maintainability, and enables better tooling support for the Electron-based browser application.

### II. Verification & Debugging First  
Before implementing any feature, agent MUST research and verify existing code patterns, variable types, function signatures, and component interfaces; All dependencies and imports must be validated against actual codebase structure; Debug and investigate any unclear code relationships before making changes; Use IDE tools and type checking to verify code correctness during development.

**Rationale**: Prevents integration issues and ensures new code works harmoniously with existing browser architecture spanning main process, renderer, and preload contexts.

### III. User Experience Consistency
All UI components MUST follow established design patterns from existing codebase; Consistent styling using Tailwind CSS classes as per project configuration; Dark mode support required for all new components; Responsive design principles applied to all interfaces; User interactions must provide appropriate feedback and loading states.

**Rationale**: Maintains professional browser experience and ensures feature additions feel native to the existing application.

### IV. Performance Requirements
Frontend components must render within 100ms for common operations; Memory usage must be monitored for potential leaks in long-running processes; Bundle sizes must be optimized with appropriate code splitting; Background processes in main thread must not block UI responsiveness; Network requests must implement proper caching and error handling.

**Rationale**: Browser applications require exceptional performance to compete with established browsers and provide smooth user experience.

### V. End-to-End Validation
All user-facing features MUST include end-to-end tests that simulate real user interactions; Test automation should cover critical user journeys from browser startup to feature completion; Integration between Electron main process, renderers, and preload scripts must be validated; Cross-process communication (IPC) must be tested for reliability and error handling.

**Rationale**: Ensures complete feature functionality across the complex Electron architecture and prevents regressions in critical browser operations.

## Development Standards

**TypeScript Configuration**: Strict mode enforced with noImplicitAny, noImplicitReturns, and strictNullChecks enabled; ESLint configuration must be maintained and followed; Prettier formatting applied consistently across all files.

**Code Organization**: Feature-based organization with clear separation between main process (`src/main/`), renderer processes (`src/renderer/`), and preload scripts (`src/preload/`); Shared utilities in common directories; Components grouped by functionality with clear interface boundaries.

**Documentation Requirements**: All public APIs documented with TypeScript JSDoc; README files required for complex features; Inline comments for non-obvious business logic; Architecture decisions documented in appropriate specification files.

## Quality Assurance

**Verification Process**: Code changes must include verification of impacted variable types, function signatures, and component interfaces; Integration points between processes must be tested; Performance impact must be measured for significant changes.

**Testing Strategy**: End-to-end tests using appropriate automation framework; Unit tests for complex business logic; Integration tests for IPC communication; Manual testing checklist for UI/UX changes.

**Code Review Standards**: All code must pass type checking and linting; Performance implications must be considered; Security implications for Electron context isolation must be reviewed; Test coverage must be maintained or improved.

## Governance

This constitution supersedes all other development practices; All implementation plans and technical decisions must demonstrate compliance with these principles; Violations require explicit justification and mitigation plan; Complexity must be justified against user value and maintainability.

All code changes must verify alignment with type safety, verification practices, UX consistency, performance standards, and end-to-end validation requirements; Use project README and specification files for runtime development guidance and feature-specific requirements.

**Version**: 1.0.0 | **Ratified**: 2025-09-24 | **Last Amended**: 2025-09-24