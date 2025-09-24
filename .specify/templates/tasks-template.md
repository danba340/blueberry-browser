# Tasks: [FEATURE NAME]

**Input**: Design documents from `/specs/[###-feature-name]/`
**Prerequisites**: plan.md (required), research.md, data-model.md, contracts/

## Execution Flow (main)
```
1. Load plan.md from feature directory
   → If not found: ERROR "No implementation plan found"
   → Extract: tech stack, libraries, structure
2. Load optional design documents:
   → data-model.md: Extract entities → model tasks
   → contracts/: Each file → contract test task
   → research.md: Extract decisions → setup tasks
3. Generate tasks by category:
   → Setup: project init, dependencies, linting
   → Tests: contract tests, integration tests
   → Core: models, services, CLI commands
   → Integration: DB, middleware, logging
   → Polish: unit tests, performance, docs
4. Apply task rules:
   → Different files = mark [P] for parallel
   → Same file = sequential (no [P])
   → Tests before implementation (TDD)
5. Number tasks sequentially (T001, T002...)
6. Generate dependency graph
7. Create parallel execution examples
8. Validate task completeness:
   → All contracts have tests?
   → All entities have models?
   → All endpoints implemented?
9. Return: SUCCESS (tasks ready for execution)
```

## Format: `[ID] [P?] Description`
- **[P]**: Can run in parallel (different files, no dependencies)
- Include exact file paths in descriptions

## Path Conventions
- **Single project**: `src/`, `tests/` at repository root
- **Web app**: `backend/src/`, `frontend/src/`
- **Mobile**: `api/src/`, `ios/src/` or `android/src/`
- Paths shown below assume single project - adjust based on plan.md structure

## Phase 3.1: Setup
- [ ] T001 Create project structure per implementation plan
- [ ] T002 Initialize [language] project with [framework] dependencies
- [ ] T003 [P] Configure linting and formatting tools

## Phase 3.2: Verification & Testing ⚠️ MUST COMPLETE BEFORE 3.3
**CRITICAL: Research existing code and write tests that MUST FAIL before ANY implementation**
- [ ] T004 [P] Research and verify existing TypeScript interfaces and component patterns
- [ ] T005 [P] Validate dependency imports and module structure in codebase  
- [ ] T006 [P] Contract test POST /api/users in tests/contract/test_users_post.py
- [ ] T007 [P] Contract test GET /api/users/{id} in tests/contract/test_users_get.py
- [ ] T008 [P] Integration test user registration in tests/integration/test_registration.py
- [ ] T009 [P] Integration test auth flow in tests/integration/test_auth.py
- [ ] T010 [P] End-to-end test simulating complete user journey from browser startup
- [ ] T011 [P] E2E test for Electron IPC communication between processes

## Phase 3.3: Core Implementation (ONLY after verification and tests are failing)
- [ ] T012 [P] User model in src/models/user.py with strict TypeScript interfaces
- [ ] T013 [P] UserService CRUD in src/services/user_service.py with type safety
- [ ] T014 [P] CLI --create-user in src/cli/user_commands.py
- [ ] T015 POST /api/users endpoint with comprehensive error handling
- [ ] T016 GET /api/users/{id} endpoint with proper validation
- [ ] T017 Input validation with TypeScript strict mode enforcement
- [ ] T018 Error handling, logging, and performance monitoring

## Phase 3.4: Integration & Performance
- [ ] T019 Connect UserService to DB with optimized queries
- [ ] T020 Auth middleware with security best practices
- [ ] T021 Request/response logging with performance metrics
- [ ] T022 CORS and security headers
- [ ] T023 Memory usage monitoring and optimization
- [ ] T024 Bundle size analysis and code splitting

## Phase 3.5: Validation & Polish
- [ ] T025 [P] Unit tests for validation in tests/unit/test_validation.py
- [ ] T026 Performance tests ensuring <100ms frontend render times
- [ ] T027 [P] Cross-process communication validation tests
- [ ] T028 [P] Dark mode compatibility verification
- [ ] T029 [P] Update docs/api.md with TypeScript interfaces
- [ ] T030 Code quality review and duplication removal
- [ ] T031 Final E2E test suite execution and validation

## Dependencies
- Verification (T004-T005) before all tests and implementation
- Tests (T006-T011) before implementation (T012-T018)
- T012 blocks T013, T019
- T020 blocks T022
- Core implementation before integration (T019-T024)
- Integration before validation and polish (T025-T031)

## Parallel Example
```
# Launch T004-T007 together:
Task: "Contract test POST /api/users in tests/contract/test_users_post.py"
Task: "Contract test GET /api/users/{id} in tests/contract/test_users_get.py"
Task: "Integration test registration in tests/integration/test_registration.py"
Task: "Integration test auth in tests/integration/test_auth.py"
```

## Notes
- [P] tasks = different files, no dependencies
- Verify tests fail before implementing
- Commit after each task
- Avoid: vague tasks, same file conflicts

## Task Generation Rules
*Applied during main() execution*

1. **From Contracts**:
   - Each contract file → contract test task [P]
   - Each endpoint → implementation task
   
2. **From Data Model**:
   - Each entity → model creation task [P]
   - Relationships → service layer tasks
   
3. **From User Stories**:
   - Each story → integration test [P]
   - Quickstart scenarios → validation tasks

4. **Ordering**:
   - Setup → Tests → Models → Services → Endpoints → Polish
   - Dependencies block parallel execution

## Validation Checklist
*GATE: Checked by main() before returning*

- [ ] All contracts have corresponding tests
- [ ] All entities have model tasks
- [ ] All tests come before implementation
- [ ] Parallel tasks truly independent
- [ ] Each task specifies exact file path
- [ ] No task modifies same file as another [P] task