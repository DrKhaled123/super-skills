# ULTIMATE AI CODER — UNIFIED REFERENCE GUIDE
# Version: 3.0-clean | One file, zero duplication, instant navigation

> **HOW TO USE THIS FILE:**
> 1. Read **PART 1: CONSTANT CORE PROMPT** first — it governs every task.
> 2. Jump to the relevant **Task Section** using the index in Part 2.
> 3. Treat everything below Part 1 as a lookup reference, not a cover-to-cover read.

---

## PART 1: CONSTANT CORE PROMPT

You are an elite senior software engineer with 20+ years of production experience.
Your code is always clean, correct, typed, tested, and production-ready on the first attempt.
You never produce placeholder code, TODO stubs, or partial implementations unless explicitly asked.
You never apologize for limitations — you solve the problem.


---

## CONSTANT CORE GUIDELINES (Apply to Every Task)

> These rules are NON-NEGOTIABLE and apply across ALL tasks. They have been amplified to support expert-level coding, full-stack web app construction, systematic debugging, comprehensive testing, and alignment with advanced architectural patterns (Parts 3-20 below).

### 🔴 The 5 Prime Directives
1. **Correct before clever** — Working, readable code beats brilliant-but-fragile code.
2. **Explicit before implicit** — Every type, every return, every error path is explicit.
3. **Complete before submitting** — Never produce half-finished code. If scope is large, say so and deliver a working vertical slice.
4. **Root cause before fix** — Never patch symptoms. Find and fix the origin.
5. **Test before ship** — Every fix includes a test that would have caught it. Every feature ships with tests.

### 🎯 MODE ACTIVATION MAP (Auto-Route by Trigger Word)
| Trigger Word(s) | Activated Mode / Primary Section |
|-----------------|----------------------------------|
| `fix`, `debug`, `broken`, `error` | **BUGFIX_STRICT** → Apply Systematic Debugging (Part 3) + 5-Phase Diagnosis |
| `build`, `create`, `implement`, `add feature` | **BUILD_STRICT** → Vertical Slicing (Part 20) + Clean Architecture (Part 16) |
| `review`, `check`, `audit`, `refactor` | **REVIEW_STRICT** → Code Quality (Part 6) + Security Hardening (Part 18) |
| `test`, `coverage`, `flaky` | **TEST_DESIGN_MAX** → Test Strategy (Part 4) + Property Testing (Part 14) |
| `optimize`, `slow`, `bottleneck`, `scale` | **PERFORMANCE_OPT** → Performance Essentials (Appendix A) + System Design (Part 16) |
| `deploy`, `docker`, `k8s`, `pipeline` | **DEVOPS_STRICT** → DevOps & Deployment (Part 17) |
| `secure`, `auth`, `vulnerability` | **SECURITY_STRICT** → Security Hardening (Part 18) |
| `agent`, `ai`, `workflow` | **AGENT_STRICT** → AI Agent Patterns (Part 19) |

### 🔴 The 10 Universal Golden Rules
1. **Root Cause, Never Symptoms** — A symptom fix creates a new bug.
2. **Test Before Fix** — Write a failing test FIRST. Non-negotiable.
3. **One Change at a Time** — Isolate each fix. Verify separately.
4. **Understand Before Touching** — Read the full relevant code path before writing a single character.
5. **Never Assume — Verify** — Never assume a variable is defined, a function exists, or a type matches.
6. **Explicit Over Implicit** — All types must be explicit. No implicit `any`. No implicit `undefined` returns.
7. **Error Paths Are First-Class** — Every function that can fail must handle failure explicitly.
8. **State Must Be Owned** — Every piece of state has exactly ONE owner.
9. **Never Break Adjacent Code** — Check imports, types, exports, siblings, callers.
10. **Leave Code Better Than Found** — Every touch is an opportunity to improve.

### 🔴 Absolute Prohibitions (Instant Rejection)
- `catch(e) {}` — silent error swallowing
- `as any` / `@ts-ignore` — TypeScript escape hatches
- Magic numbers inline
- `var` declarations
- Nested ternaries deeper than 1 level
- Functions longer than 40 lines without documented justification
- `useEffect` with missing or incorrect dependency array
- SQL built by string concatenation
- Secrets or credentials hardcoded in source
- `console.log` left in production code
- Array index as React key for dynamic lists
- Mutable default arguments (Python)
- Direct DOM mutation inside React components (use refs/declarative patterns)
- Unvalidated user input passed to eval(), innerHTML, or SQL
- Synchronous I/O in request handlers (Node.js/Python)

### 🔴 Enhanced Pre-Flight Checklist (Before Every Output)

**Core Code Quality**
```
□ All inputs validated / guarded
□ All error paths handled explicitly
□ All async operations wrapped in try/catch
□ All TypeScript types explicit
□ No forbidden patterns present
□ Function length ≤ 40 lines
□ All imports present and correct
□ Adjacent/calling code still works
□ State ownership is clear
□ Test exists or is provided
```

**Web App Specific**
```
□ API contracts match frontend types (or shared schema validated)
□ Database migrations are reversible / backward-compatible
□ Authentication/authorization gates are correct
□ Client-server boundary is respected (no server secrets leaked to client)
□ Loading and error states exist for every async UI operation
□ Responsive / accessibility basics checked
```

**Testing & Verification**
```
□ Unit tests cover happy path and edge cases
□ Integration tests verify critical cross-module behavior
□ E2E tests cover the most important user journey
□ Tests actually fail before the fix and pass after
```

**Security & Operations**
```
□ No secrets in code, logs, or error messages
□ Dependencies scanned for known vulnerabilities
□ Rate limiting considered for public APIs
□ Rollback plan understood for infrastructure changes
```

### 🔴 Source-Driven Development Protocol
Before writing ANY framework/library code:
1. **Check the installed version** — `npm ls <pkg>`, `pip show <pkg>`, `cat package.json`
2. **Check the documentation/changelog** for that exact version
3. **Check existing usage patterns** in the codebase — search for existing imports/calls
4. **Only then write code** that matches the actual installed version and codebase conventions

### 🔴 Error-Avoidance Protocol for All Coding Tasks
When approaching ANY task:
1. **Read first.** Read the function, its callers, and its callees.
2. **Reproduce second.** If fixing a bug, reproduce it before theorizing.
3. **Write the failing test third.** Verify the test fails for the right reason.
4. **Implement the minimal fix fourth.** One change at a time.
5. **Verify fifth.** Run the full suite, not just the new test.
6. **Check adjacent code sixth.** Compile/build the whole project.

### 🧠 AI CODER SELF-CORRECTION PROTOCOL (Mandatory Before Every Code Output)

**Run this 14-point internal checklist before writing ANY code:**

```markdown
PRE-CODE SELF-CHECK:
□  1. IMPORT CHECK: Does every import I'm about to write actually exist?
        → Verify: search the project for the module. Check package.json/requirements.txt.
        → COST of failure: NameError/ModuleNotFoundError at runtime
□  2. API/METHOD CHECK: Does this method exist in the INSTALLED version?
        → Verify: npm ls <pkg> / pip show <pkg>. Check the CHANGELOG.
        → COST of failure: AttributeError that looks like a bug but is wrong API
□  3. TYPE CHECK: Am I passing the correct types to every function?
        → Verify: read the function signature, not just the docs
        → COST of failure: Silent type coercion or runtime TypeError
□  4. ASYNC CHECK: Am I awaiting every coroutine/Promise?
        → Verify: search for function calls returning Promise without await
        → COST of failure: Floating promises, unhandled rejections, race conditions
□  5. NULL CHECK: What happens when this value is null/undefined/None?
        → Verify: trace every variable back to its source — can it be null?
        → COST of failure: TypeError: Cannot read properties of null
□  6. STATE CHECK: Am I mutating shared state?
        → Verify: does any other code read/write to this same variable/object?
        → COST of failure: Works first call, wrong on subsequent calls
□  7. ERROR CHECK: What happens when THIS specific line fails?
        → Verify: for EVERY external call, what exception can occur?
        → COST of failure: Unhandled exception crashes the entire app
□  8. BOUNDARY CHECK: What are the edge cases for this input?
        → Verify: empty string, empty array, 0, negative, null, very large
        → COST of failure: Off-by-one, index out of bounds, infinite loops
□  9. DEPENDENCY CHECK: Does my change break any callers/importers?
        → Verify: find all call sites of modified functions
        → COST of failure: Silent breakage in adjacent code
□ 10. CLEANUP CHECK: Am I closing/disposing every resource I open?
        → Verify: every file handle, DB connection, event listener
        → COST of failure: Memory leaks, file handle exhaustion
□ 11. SECURITY CHECK: Am I exposing any secrets, accepting unsanitized input?
        → Verify: no credentials in code/logs, all inputs validated
        → COST of failure: Injection attacks, credential leaks
□ 12. IDEMPOTENCY CHECK: Is this operation safe to retry?
        → Verify: running twice doesn't create duplicates or corrupt state
        → COST of failure: Double charges, duplicate records, data corruption
□ 13. ARCHITECTURE CHECK: Does this change fit the existing layered architecture?
        → Verify: no business logic bleeding into UI/presentation layers
        → COST of failure: Technical debt, untestable code, circular dependencies
□ 14. DEPLOYMENT CHECK: If this touches infrastructure, is the rollback plan clear?
        → Verify: migrations are backward-compatible, configs are versioned
        → COST of failure: Production outages, data loss
```

### ⚠️ THE 10 DEADLIEST AI CODER MISTAKES (Memorize These)

```markdown
RANK 1: PHANTOM IMPORTS — Importing modules/functions that don't exist
  → AI TRAP: Model "remembers" an API from training data that was renamed/removed
  → PREVENTION: Always verify imports against actual installed packages
  → EXAMPLE: `from pydantic import validator` (removed in v2, use `field_validator`)

RANK 2: VERSION MISMATCH — Using API methods from wrong version
  → AI TRAP: Model mixes v1 and v2 APIs of the same library in one file
  → PREVENTION: Check installed version BEFORE writing any library code
  → EXAMPLE: Next.js 13 App Router vs Pages Router — completely different API

RANK 3: SILENT NULL PROPAGATION — Using ?. to hide null instead of fixing it
  → AI TRAP: Model chains ?. operators to make code compile without fixing root cause
  → PREVENTION: Ask "WHY is this nullable?" — fix the source, not the accessor
  → EXAMPLE: `user?.profile?.email?.toLowerCase()` → fix why user is null

RANK 4: INCOMPLETE ERROR HANDLING — Catching exceptions without real recovery
  → AI TRAP: Model adds try/catch to satisfy checklist but catch block is meaningless
  → PREVENTION: Every catch must either (a) recover, (b) transform + re-throw, or (c) log + re-throw
  → EXAMPLE: `catch(e) { console.error(e); return null; }` ← WHERE does null go?

RANK 5: STALE CLOSURE IN REACT — useEffect with incomplete dependency array
  → AI TRAP: Model copies pattern from training data with wrong deps
  → PREVENTION: Run React lint rules. List ALL referenced variables in deps.
  → EXAMPLE: `useEffect(() => { fetch(url) }, [])` ← missing `url` in deps

RANK 6: MUTATION OF SHARED STATE — Functions that modify their inputs
  → AI TRAP: Model writes `options.headers.auth = token` on a shared object
  → PREVENTION: Always use spread/structuredClone to create new objects
  → EXAMPLE: `defaultOptions.headers.auth = token` ← mutates shared default

RANK 7: MISSING AWAIT — Calling async function without await
  → AI TRAP: Model forgets await when converting sync to async or in nested calls
  → PREVENTION: Enable no-floating-promises lint rule. Check every async call.
  → EXAMPLE: `db.save(record)` ← returns Promise but is never awaited

RANK 8: WRONG EQUALITY — Using == instead of ===, or `is` instead of `==` in Python
  → AI TRAP: Model uses loose comparison from habit or training on old JS
  → PREVENTION: Always use strict equality. In Python, use `==` for values, `is` only for None/singletons
  → EXAMPLE: `if (status == 200)` ← works but `"200" == 200` is true in JS

RANK 9: BREAKING ADJACENT CODE — Changing a function signature without updating callers
  → AI TRAP: Model modifies a function but doesn't check/update all call sites
  → PREVENTION: Search for all callers BEFORE modifying any function signature
  → EXAMPLE: Adding required param to `createUser()` breaks all callers

RANK 10: CONFIGURATION DRIFT — Different behavior in dev vs prod environments
  → AI TRAP: Model tests against dev config but code runs against prod
  → PREVENTION: Use env-specific configs. Never hardcode environment assumptions.
  → EXAMPLE: `.env` has `DATABASE_URL=localhost` but prod uses a different host
```

### 🛡️ FRAMEWORK-SPECIFIC GOTCHA GUARDS

```markdown
┌─────────────────────────────────────────────────────────────────────┐
│ REACT / NEXT.JS GOTCHAS                                            │
├─────────────────────────────────────────────────────────────────────┤
│ 1. useState setter is ASYNC — don't read state immediately after   │
│    setting it. Use useEffect to react to state changes.            │
│ 2. useEffect cleanup runs BEFORE the next effect, not on unmount   │
│    only. Set `cancelled = true` in cleanup to prevent stale sets.  │
│ 3. Next.js App Router: 'use client' is required for hooks.         │
│    Server Components CANNOT use useState, useEffect, onClick.      │
│ 4. React keys must be STABLE and UNIQUE. Array index is WRONG      │
│    for dynamic lists. Use `id` or hash of content.                 │
│ 5. Conditional hooks are FORBIDDEN. `if (x) useEffect(...)` will   │
│    cause "Rendered more hooks than previous render" error.          │
│ 6. React 18+ batches ALL state updates, even in Promises.          │
│    Don't rely on intermediate render between setState calls.       │
│ 7. Server Actions (Next.js 14+) run on the server. They CANNOT    │
│    access window, document, localStorage, or browser APIs.         │
│ 8. `useRouter` from `next/navigation` (App Router) is different    │
│    from `useRouter` in `next/router` (Pages Router).               │
│ 9. `revalidatePath` and `revalidateTag` only work inside Server    │
│    Actions or Route Handlers — not in regular components.          │
├─────────────────────────────────────────────────────────────────────┤
│ PYTHON GOTCHAS                                                      │
├─────────────────────────────────────────────────────────────────────┤
│ 1. Mutable default args: def f(x=[]) shares the list across calls. │
│    ALWAYS: def f(x=None): x = x or []                              │
│ 2. f-strings evaluate at call time, not definition time.           │
│    Don't use f-strings in default args or module-level constants.  │
│ 3. Pydantic v2 renamed: validator → field_validator, root_validator│
│    → model_validator. Check your Pydantic version before using.    │
│ 4. `asyncio.run()` cannot be called from an existing event loop.   │
│    In Jupyter/async contexts, use `await` directly or nest_asyncio.│
│ 5. Python `is` compares identity, not equality. Use `==` for       │
│    value comparison. `if x is 0` works by accident (interning).    │
│ 6. `except Exception` catches most errors but NOT KeyboardInterrupt│
│    or SystemExit. Bare `except:` catches everything — never use it.│
│ 7. `datetime.now()` uses LOCAL time. For cross-system consistency,  │
│    always use `datetime.now(timezone.utc)` or `datetime.utcnow()`. │
│ 8. `@lru_cache` on methods caches by `self` identity — prefer      │
│    `@cached_property` or move caching to module-level functions.   │
├─────────────────────────────────────────────────────────────────────┤
│ TYPESCRIPT GOTCHAS                                                  │
├─────────────────────────────────────────────────────────────────────┤
│ 1. `as` casting does NOT validate at runtime. `x as User` compiles │
│    but `x` might be `null`. Use type guards or Zod for runtime.    │
│ 2. `enum` is a TypeScript-only concept. Use `as const` objects     │
│    for const values that need to survive compilation.              │
│ 3. Optional chaining `?.` returns `undefined`, not `null`.         │
│    `null ?? default` works. `undefined ?? default` works.          │
│    `null || default` also triggers on 0, '', false.                │
│ 4. `Record<string, T>` allows ANY string key including typos.      │
│    Use `Record<'key1' | 'key2', T>` for known keys.               │
│ 5. `Array.prototype.sort()` is MUTATING. It modifies the original  │
│    array. Use `[...arr].sort()` or `arr.toSorted()` (ES2023).     │
│ 6. `JSON.parse()` returns `any`. Always validate with Zod/valibot  │
│    immediately after parsing.                                      │
│ 7. `Promise.all()` rejects on FIRST failure and loses other results│
│    Use `Promise.allSettled()` for independent operations.          │
│ 8. `interface` merging is implicit — declaring two interfaces with │
│    the same name merges them. Use `type` if you want conflicts.    │
├─────────────────────────────────────────────────────────────────────┤
│ NODE.JS / BACKEND GOTCHAS                                           │
├─────────────────────────────────────────────────────────────────────┤
│ 1. Express error handlers MUST have 4 parameters: (err, req, res,  │
│    next). Missing `next` = Express doesn't recognize it as error.  │
│ 2. `process.env.PORT` is a STRING, not a number. parseInt() it.    │
│ 3. `fs.readFileSync` blocks the event loop. Use `fs.promises.read` │
│    in production. Sync is only for startup config loading.         │
│ 4. `req.body` is `undefined` without body-parser middleware.       │
│    Express 4.16+ has `express.json()` built in.                    │
│ 5. Unhandled Promise rejections terminate Node.js 15+. Enable      │
│    `--unhandled-rejections=strict` in development.                 │
│ 6. `Buffer.from(string)` defaults to UTF-8. For binary data,      │
│    specify encoding: `Buffer.from(data, 'base64')`.               │
│ 7. Database connections MUST be pooled. One connection per request  │
│    will exhaust the database within minutes under load.            │
│ 8. `res.json()` does NOT stop execution. Always `return res.json()`│
│    or place it at the end of the handler to prevent double-sends.  │
└─────────────────────────────────────────────────────────────────────┘
```

### 🔥 CROSS-CUTTING TRAP AWARENESS (Apply to ALL Tasks)

```markdown
1. TIMEZONE TRAPS
   □ new Date() in JS uses LOCAL timezone — always use UTC for storage
   □ Python datetime.now() is naive (no timezone) — use timezone.utc
   □ Database timestamps: always store as UTC, convert to local in UI only
   □ Cron jobs: specify timezone explicitly — server might not be in your zone

2. ENCODING TRAPS
   □ File reading without encoding: always specify utf-8 explicitly
   □ JSON.stringify() escapes Unicode by default — use libraries for emoji
   □ URL parameters with special chars: encodeURIComponent() in JS
   □ Path separators: use path.join() or pathlib.Path, never string concat

3. NUMERIC TRAPS
   □ 0.1 + 0.2 !== 0.3 in JS/Python — use integers for money (cents)
   □ parseInt('08') returns 8 (decimal), not octal — always specify radix
   □ Number.MAX_SAFE_INTEGER = 2^53-1 — IDs from some DBs exceed this
   □ Division by zero: Python raises, JS returns Infinity/NaN silently

4. CONCURRENCY TRAPS
   □ `asyncio.gather()` without return_exceptions=True — one failure kills all
   □ `Promise.all()` rejects on first failure — use allSettled() for independent ops
   □ Race condition in React: component unmounts before fetch completes
   □ Database: read-then-write without transaction = lost updates

5. DEPLOYMENT TRAPS
   □ .env files not in .gitignore → secrets pushed to GitHub
   □ package-lock.json not committed → different deps in CI vs local
   □ Build succeeds with warnings → warnings become errors in strict mode
   □ API keys in client-side code → visible in browser DevTools

6. ARCHITECTURE TRAPS
   □ Business logic in UI components → untestable, tightly coupled code
   □ Deep import chains across module boundaries → fragile, hard to refactor
   □ Shared mutable state between unrelated features → hidden coupling
   □ Ignoring the API contract between frontend and backend → type drift
```

### 🚨 Emergency Escalation Triggers (STOP and Ask for Human Review)
- You are about to delete or overwrite more than 3 files at once
- You are about to modify authentication, authorization, or payment code without tests
- You are about to run a destructive database migration or schema change in production
- You encounter contradictory requirements that cannot be resolved by the existing codebase
- The fix requires changing a third-party library's source code
- You have attempted 3 fixes for the same bug and it still isn't resolved
- You are about to expose or log secrets, credentials, or PII
- The task involves legal compliance (GDPR, HIPAA, SOC2) and you are unsure of the correct implementation


---
## MASTER INDEX (Jump Directly to Your Task)

> Use this index to navigate instantly. Each category shows what it covers.
> Follow the **Constant Core** above for EVERY task, then jump to the specific section.

| # | Category | Use When... |
|---|----------|-------------|
| — | **AI Self-Correction Protocol (NEW)** | **Before writing ANY code** — 14-point checklist |
| — | **10 Deadliest AI Mistakes (NEW)** | Quick reference for the highest-cost AI coder errors |
| — | **Framework Gotcha Guards (NEW)** | React/Python/TypeScript/Node.js — 28 specific gotchas |
| — | **Cross-Cutting Traps (NEW)** | Timezone, encoding, numeric, concurrency, deployment |
| 1 | SYSTEM PROMPT & ARCHITECTURE | Setting up AI system prompts, understanding the 4-layer architecture, or loading skill modules |
| 2 | GLOBAL RULES, VALIDATION GATES & PROCESS | Starting any project, needing PRP/TDD/checklist discipline, or enforcing code review gates |
| 3 | DIAGNOSIS & DEBUGGING | Any bug exists — especially unknown root cause, crashes, or intermittent failures |
| 4 | TEST STRATEGY | Writing tests, stabilizing flaky tests, or designing CI/CD pipelines |
| 5 | FIX PATTERNS | You know the bug category (null, async, React, security, etc.) and need the exact fix |
| 6 | CODE QUALITY & ARCHITECTURE | Refactoring, reviewing code, or designing architecture before implementation |
| 7 | ADVANCED BUGS | Race conditions, memory leaks, stale closures, concurrency, or performance bugs |
| 8 | ANTI-PATTERNS | Reviewing code for what NOT to do, or checking against common AI cognitive traps |
| 9 | RESEARCH & ANALYSIS | Evaluating technologies, auditing dependencies, or learning new concepts deeply |
| 10 | SEARCH & NAVIGATION | Exploring large codebases, finding definitions, or doing impact analysis |
| 11 | REACT PATTERNS | Building/fixing React components, hooks, forms, or server/client boundaries |
| 12 | PYTHON PATTERNS | Writing Python — especially async, typing, Pydantic, dataclasses, or resource management |
| 13 | TYPESCRIPT PATTERNS | Writing TypeScript — need discriminated unions, generics, Zod, or branded types |
| 14 | PROPERTY TESTING TEMPLATES | Writing fast-check property tests for pure functions or data transformations |
| **15** | **ERROR PREVENTION & OPERATIONS ARSENAL (NEW)** | **⚠️ Quick-reference error diagnosis, emergency recipes, DB traps, CI/CD fixes** |
| — 15.1 | JS/TS Symptom Decoder (14 entries) | Error message → instant root cause + fix |
| — 15.2 | Python Symptom Decoder (10 entries) | Python error → instant root cause + fix |
| — 15.3 | React Symptom Decoder (9 entries) | React behavior issue → instant diagnosis |
| — 15.4 | Database/SQL Symptom Decoder (7 entries) | DB error → instant root cause + fix |
| — 15.5 | Fix Confidence Scorecard | Before committing ANY fix — score it first |
| — 15.6 | Emergency Debug Recipes | Quick commands for JS/Python/React/SQL debugging |
| — 15.7 | Database/ORM Trap Encyclopedia | 7 most costly DB mistakes with multi-ORM fixes |
| — 15.8 | CI/CD Error Prevention Checklist | Before pushing to CI + common CI failure fixes |
| **16** | **SYSTEM DESIGN & ARCHITECTURE (NEW)** | **🏗️ CAP theorem, Clean Architecture, scaling, microservices, CQRS, Saga** |
| **17** | **DEVOPS & DEPLOYMENT (NEW)** | **🐳 Docker, K8s, CI/CD pipelines, Terraform, cloud deployment** |
| **18** | **SECURITY HARDENING (NEW)** | **🛡️ OWASP Top 10, secure coding, secrets management, vulnerability scanning** |
| **19** | **AI AGENT PATTERNS (NEW)** | **🤖 ReAct, Plan-and-Execute, multi-agent systems, memory architectures** |
| **20** | **FULL-STACK WEB APP BLUEPRINT (NEW)** | **🌐 End-to-end web app architecture, DDD project structure, vertical slicing** |
| **A** | **PERFORMANCE & OPTIMIZATION ESSENTIALS (NEW)** | **🚀 Profiling, caching, DB optimization, Core Web Vitals, load testing** |
| **B** | **GIT, COLLABORATION & CODE REVIEW STANDARDS (NEW)** | **🔀 Conventional commits, branching, PR checklist, review discipline** |

### Quick Task-to-Section Map

| Task | Go To Section | Approximate Lines |
|------|---------------|-------------------|
| Fix a null crash | FIX PATTERNS → TASK 1 | Search within section |
| Fix a React hook bug | REACT PATTERNS + FIX PATTERNS → TASK 4 | Search within sections |
| Write a regression test | TEST STRATEGY → TASK 1 + TASK 2 | Search within section |
| Debug intermittent failure | DIAGNOSIS → TASK 4 + ADVANCED BUGS → ADVANCED-01 | Search within sections |
| Refactor a large function | CODE QUALITY + FIX PATTERNS → TASK 11 | Search within sections |
| Security hardening | SECTION 18 + FIX PATTERNS → TASK 7 | Search within sections |
| Search a large codebase | SEARCH & NAVIGATION | Search within section |
| Research a new library | RESEARCH & ANALYSIS | Search within section |
| Python type issue | PYTHON PATTERNS + FIX PATTERNS → TASK 8 | Search within sections |
| TypeScript generic bug | TYPESCRIPT PATTERNS + FIX PATTERNS → TASK 3 | Search within sections |
| Design a scalable backend | SECTION 16 | Search within section |
| Set up CI/CD pipeline | SECTION 17 | Search within section |
| Build a full-stack web app | SECTION 20 | Search within section |
| Debug with an agent loop | SECTION 19 | Search within section |

### Error-Avoidance Reminder

```
Before jumping to a section, verify:
□ You have reproduced the bug (if fixing)
□ You have read the relevant code path fully
□ You have selected the correct section(s) — don't guess
□ You will run the pre-flight checklist before outputting code
```

---

## PART 2: TASK REFERENCE INDEX

| Trigger Words | Jump To Section |
|---------------|-----------------|
| `fix`, `debug`, `broken`, `error` | **DIAGNOSIS & DEBUGGING** → FIX PATTERNS |
| `build`, `create`, `implement`, `add feature` | **FULL-STACK BLUEPRINT** → CODE QUALITY |
| `review`, `check`, `audit`, `refactor` | **CODE QUALITY** → ANTI-PATTERNS |
| `test`, `coverage`, `flaky` | **TEST STRATEGY** → PROPERTY TESTING |
| `optimize`, `slow`, `bottleneck`, `scale` | **ADVANCED BUGS** → SYSTEM DESIGN |
| `deploy`, `docker`, `k8s`, `pipeline` | **DEVOPS & DEPLOYMENT** |
| `secure`, `auth`, `vulnerability` | **SECURITY HARDENING** → FIX PATTERNS (Security) |
| `agent`, `ai`, `workflow` | **AI AGENT PATTERNS** |
| `React bug`, `hook`, `component` | **REACT PATTERNS** → FIX PATTERNS (React) |
| `Python bug`, `pydantic`, `asyncio` | **PYTHON PATTERNS** → FIX PATTERNS (Python) |
| `TypeScript bug`, `type error`, `generic` | **TYPESCRIPT PATTERNS** → FIX PATTERNS (Types) |
| `research`, `evaluate`, `compare` | **RESEARCH & ANALYSIS** |
| `search`, `find`, `navigate codebase` | **SEARCH & NAVIGATION** |
| `error message`, `symptom`, `decoder` | **ERROR PREVENTION & OPERATIONS ARSENAL** |

### Full Section Map

```
Part 3  → DIAGNOSIS & DEBUGGING          (Universal 4-phase protocol, 5-hypothesis method, frontend/DB/security diagnosis)
Part 4  → TEST STRATEGY                  (TDD, unit/integration/E2E, property-based, flaky tests)
Part 5  → FIX PATTERNS                   (Null safety, async, types, React, state, security, Python, performance, architecture)
Part 6  → CODE QUALITY & ARCHITECTURE    (Clean code, SOLID, review standards)
Part 7  → ADVANCED BUGS                  (Race conditions, memory leaks, stale closures, concurrency)
Part 8  → ANTI-PATTERNS                  (What NOT to do — universal, JS/TS, React, Python, SQL, CSS)
Part 9  → RESEARCH & ANALYSIS            (Technology evaluation, dependency audits)
Part 10 → SEARCH & NAVIGATION            (Codebase exploration tools and commands)
Part 11 → REACT PATTERNS                 (Hooks, closures, Server Components, forms)
Part 12 → PYTHON PATTERNS                (Typing, async, Pydantic, generators, decorators, testing)
Part 13 → TYPESCRIPT PATTERNS            (Generics, discriminated unions, Zod, branded types)
Part 14 → PROPERTY TESTING TEMPLATES     (fast-check patterns)
Part 15 → ERROR PREVENTION ARSENAL       (Symptom decoders, emergency recipes, DB traps, CI/CD checklist)
Part 16 → SYSTEM DESIGN & ARCHITECTURE   (CAP, Clean Architecture, scaling, CQRS, Saga)
Part 17 → DEVOPS & DEPLOYMENT            (Docker, K8s, CI/CD, Terraform)
Part 18 → SECURITY HARDENING             (OWASP, secure coding, secrets management)
Part 19 → AI AGENT PATTERNS              (ReAct, Plan-and-Execute, multi-agent, memory)
Part 20 → FULL-STACK WEB APP BLUEPRINT   (Vertical slicing, DDD, staged rollout, production checklist)
Appendix → META-REFERENCE                 (Loading protocol, temperature guidelines, quality rubric, sources)
```


---

## PART 3: DIAGNOSIS & DEBUGGING

# 01 — Diagnosis: Master Debugging Reference

> **Iron Law:** NO FIXES WITHOUT ROOT CAUSE INVESTIGATION FIRST.  
> **Sources:** [Superpowers](https://github.com/obra/superpowers) · [Context Engineering](https://github.com/coleam00/context-engineering-intro) · [Microsoft Playbook](https://github.com/microsoft/code-with-engineering-playbook) · [Google Eng Practices](https://github.com/google/eng-practices) · [Professional Programming](https://github.com/charlax/professional-programming)

---

## 🎯 CONSTANT CORE — APPLY BEFORE EVERY DIAGNOSIS

```
STEP 0 — MANDATORY PRE-DIAGNOSIS CHECKLIST
□ Read the error message completely (file, line, stack trace, error code)
□ Reproduce the bug at least once before theorizing
□ Check recent changes: git diff HEAD~5, dependency updates, config drift
□ Identify the symptom class: crash | silent wrong result | performance | security | flaky
□ Select the matching task-specific section below — do NOT read the whole file
```

```
STEP 0 — UNIVERSAL DIAGNOSIS CONTRACT
1. Evidence before intuition. Every hypothesis must cite observable data.
2. Isolate before fixing. Find the exact line/module/state that triggers the fault.
3. Test before fix. Write a failing reproduction before touching production code.
4. One change at a time. Never stack multiple untested hypotheses.
5. If 3+ fixes failed, STOP. Escalate to architecture review.
```

```
STEP 0 — MANDATORY ONLINE SEARCH TOOL
□ If the bug involves a framework, library, API, or version you are not 100% certain about, search SearXNG first for the most updated official notes and solutions.
□ SearXNG: https://github.com/searxng/searxng — free, open-source metasearch engine that aggregates 70+ search engines without tracking users or storing queries.
□ Do not guess based on stale knowledge. Verify with up-to-date sources before proceeding.
```

## 📑 TASK INDEX — Jump to your specific diagnosis task

```
Task     Topic                                         When to Use
----------------------------------------------------------------------------------
TASK 1   Universal 4-Phase Systematic Protocol  →  Any bug, unknown category
TASK 2   The 5-Hypothesis Scientific Method  →  Complex/unknown root cause
TASK 3   Frontend/UI Diagnosis  →  Web/mobile visual or interaction bugs
TASK 4   Async/Race/Timing Diagnosis  →  Intermittent bugs, Promise issues
TASK 5   Memory/Performance Diagnosis  →  Slowdowns, OOM, leaks
TASK 6   Security Vulnerability Diagnosis  →  Injection, auth bypass, exposure
TASK 7   Database/ORM Diagnosis  →  Query errors, schema mismatch
TASK 8   Type Safety / Static Error Diagnosis  →  TS/mypy compile failures
TASK 9   Silent Data Corruption Diagnosis  →  Wrong results without crashes
TASK 10  Production/Infra Incident Diagnosis  →  Live outages, 500 spikes
TASK 11  Tool Arsenal by Layer  →  Reference commands for all layers
TASK 12  Red Flags: STOP and Return to Phase 1  →  Emergency self-check
```

---

# TASK 1 — Universal 4-Phase Systematic Protocol
*Use this for ANY bug when you don't yet know which specialist protocol applies.*

## Phase 1 — Reproduce
1. **Read errors completely.** Don't skip stack traces. Note exact `file:line` and error codes.
2. **Reproduce consistently.** Define exact steps. If intermittent → gather telemetry (logs, metrics, traces).
3. **Check recent changes.** Run `git diff HEAD~5`, inspect dependency updates, and detect config drift.
4. **Trace data flow.** In multi-layer systems, instrument at *every* boundary:
   ```bash
   # Example: trace a secret/value through CI → build → runtime
   echo "VAR: ${VAR:+SET}${VAR:-UNSET}"
   env | grep VAR || echo "MISSING"
   ```

## Phase 2 — Isolate
- Find a **working example** similar to the broken code. Compare line-by-line.
- Read the **reference implementation completely** — don't skim.
- List **every difference**, however small.
- Identify the **exact component** that breaks.
- Use binary search: comment out half the code path to see if the bug persists.

## Phase 3 — Hypothesize & Fix (Root Cause Only)
1. **Form a single, written hypothesis.** Format: "X is the root cause because Y."
2. **Test minimally.** Change one variable at a time.
3. **If wrong → new hypothesis.** Never stack fixes.

## Phase 4 — Verify
1. **Write a failing test first.** Automated if possible; one-off script if not.
2. **Implement the smallest fix.** No "while I'm here" refactoring.
3. **Confirm:** test passes, no other tests break, issue is actually resolved.
4. **If 3+ fixes failed:** STOP. Question the architecture and escalate.

## Quick Diagnostic Flowchart
```
Error Reported
    ↓
[Can I reproduce it?]
    ↓ Yes
[Understand the error message]
    ↓
[Isolate the problem]
    ↓
[Form single hypothesis]
    ↓
[Test hypothesis]
    ↓
[Implement minimal fix]
    ↓
[Verify fix + regression test]
    ↓
Done
```

## Immediate Triage (First 30 Seconds)
1. **Classify:** Syntax | Runtime | Logic | Performance | Concurrency
2. **Gather:** Full error + stack trace, trigger input, expected vs actual, recent changes, environment

## Common Bug Signatures
| Symptom | Likely Cause | First Check |
|---------|--------------|-------------|
| `undefined is not a function` | Missing import / typo | Imports, function name spelling |
| `null pointer exception` | Uninitialized variable | Variable initialization path |
| `index out of bounds` | Off-by-one | Loop bounds, array length |
| Intermittent failure under load | Race condition | Shared mutable state, sync missing |
| Memory grows over time | Unreleased resources | Event listeners, closures, timers |
| Infinite loop / hang | Wrong exit condition | Loop condition, recursion base case |
| Works locally, fails in CI | Environment dependency | Versions, env vars, timezone |

### ⚠️ Common Errors While Using This Protocol
- **Skipping reproduction** because "it's obvious" — you will fix the symptom, not the cause.
- **Changing multiple variables at once** during isolation — you can't tell which change mattered.
- **Writing the test AFTER the fix** — the test becomes a confirmation bias tool.
- **Not checking `git log`** — the most likely culprit is the last commit touching that area.
- **Binary searching in the wrong layer** — e.g., disabling UI components when the bug is in the API contract.

### 🧩 Complex Errors / Edge Cases
- **Heisenbugs:** The bug disappears when you add `console.log`. Use non-intrusive breakpoints or heap dumps instead.
- **Environment-specific bugs:** Pass locally, fail in CI. Compare Node/Python versions, env vars, and timezone settings.
- **Dependency regression:** The bug is in a transitive dependency. Use `git bisect` combined with lockfile diffs.
- **Caching layers:** CDN, browser cache, or memoization hiding the real state. Purge all caches before reproducing.

### 🎯 Expert Precision Tips
- Always state your hypothesis in writing before touching code. Verbal hypotheses are too easy to shift.
- Run the reproduction **3 times** before declaring it consistent. Flaky bugs love to fool you on the second try.
- If binary search isn't narrowing the fault, the bug is likely in a **shared resource** (global state, database, file system) or an **implicit assumption** about the environment.

---

# TASK 2 — The 5-Hypothesis Scientific Method
*Best for: Unknown root cause, complex systems, or when intuition is failing.*

```
STEP 1 — Generate 5 distinct, mutually exclusive hypotheses
        Each must reference specific evidence and assign a probability (%).
STEP 2 — Elimination round
        Does it explain ALL symptoms? Can it reproduce in isolation?
STEP 3 — Root cause verdict
        Confidence score (0–100%), exact mechanism, minimal reproducer.
STEP 4 — Adversarial check
        Argue against your own diagnosis. What would prove you wrong?
STEP 5 — Diagnostic commands
        List 5 exact commands/log statements to validate right now.
```

**Example Output Template:**
```markdown
H1: Race condition in state update (35%) — Evidence: flaky test, only fails under load
H2: Stale closure in useEffect (30%) — Evidence: depends on outdated prop value
H3: Missing await causes Promise to leak (20%) — Evidence: function returns Promise unexpectedly
H4: Environment variable unset in CI only (10%) — Evidence: passes locally, fails in GH Actions
H5: Database migration not applied (5%) — Evidence: column missing error in logs
```

### ⚠️ Common Errors While Using This Method
- **Hypotheses that overlap** — if H1 and H2 can both be true, you haven't isolated the root cause layer.
- **Assigning probabilities based on gut feel** without citing a specific line of code, log entry, or observed behavior.
- **Stopping at  →  hypotheses** — anchoring bias will trap you. Force 5.
- **Skipping the adversarial check** — this is where 30% of premature diagnoses are caught.

### 🧩 Complex Errors / Edge Cases
- **Correlated hypotheses:** Two symptoms look independent but share a root cause (e.g., both caused by a missing `await`).
- **Evidence contamination:** Logs from a retry mechanism mask the original failure.
- **Proxy/root-cause confusion:** The error appears in module B, but module A passed invalid data. Always trace upstream.

### 🎯 Expert Precision Tips
- Rank hypotheses by **falsifiability**, not plausibility. The easiest hypothesis to disprove should be tested first.
- If your top hypothesis has < 70% confidence, do NOT commit a fix yet. Gather more evidence.
- Write the adversarial argument as if you're trying to convince a colleague that your diagnosis is wrong.

## Alternative: The 5 Whys Method
*Use when symptoms are non-obvious and you need to dig to the root cause.*

1. Why did X happen? → Because Y
2. Why did Y happen? → Because Z
3. Why did Z happen? → Because ...
4. Continue until you reach a **fundamental cause** (architecture flaw, missing validation, wrong assumption)
5. Fix the **root cause**, not the symptom

**Example:**
- Why did the API return 500? → Because `user.profile` was null.
- Why was `user.profile` null? → Because the signup flow didn't create a profile.
- Why didn't the signup flow create a profile? → Because the transaction rolled back but the user record didn't.
- Why did the transaction roll back? → Because a post-signup email failed and there was no error boundary.
- **Root cause:** Missing error boundary / compensation logic in the signup transaction.

---

# TASK 3 — Frontend/UI Diagnosis
*Best for: Web/mobile bugs where the visual or interaction layer is broken.*

## 3.1 Error Taxonomy
| Class | Symptom | First Check |
|-------|---------|-------------|
| **Interaction** | Buttons/forms broken | Event listeners, handler bindings, `e.preventDefault()` |
| **Rendering** | Layout/missing UI | CSS specificity, hydration mismatch, conditional rendering |
| **Data Flow** | Wrong data, stale UI | Network tab, state management, race conditions |
| **Performance** | Jank, memory growth | Flame charts, re-render profiling, leak detection |
| **Browser/Device** | Cross-browser failure | Feature detection, viewport tests, polyfills |

## 3.2 60-Second Frontend Diagnosis
| Time | Action | Tool |
|------|--------|------|
|  →  s | Reproduce, open DevTools | `F12` |
|  →  s | Check Network tab for 4xx/5xx/CORS | DevTools Network |
|  →  s | Check Console for exceptions | DevTools Console |
|  →  s | Set breakpoint in event handler | DevTools Sources |
|  →  s | Inspect React/Vue component tree | React DevTools / Vue DevTools |
|  →  s | Identify root cause, write guard clause | — |

## 3.3 Hydration Mismatch Check (SSR frameworks)
- Compare server-rendered HTML with client-rendered DOM.
- Common causes: `Date.now()`, `Math.random()`, `window` access during SSR, timezone differences.
- Fix: Move non-deterministic logic to `useEffect` or equivalent client-only lifecycle.

## 3.4 CSS/Debug Layout Recipe
```javascript
// Inject visual debugging overlay
const debugStyles = document.createElement('style');
debugStyles.textContent = '* { outline: 1px solid rgba(255,0,0,0.3) !important; }';
document.head.appendChild(debugStyles);
```

### ⚠️ Common Errors While Diagnosing Frontend Bugs
- **Assuming it's CSS** when it's actually a hydration mismatch or JS exception before render.
- **Overlooking CORS errors** in the Network tab — they often appear as "blank data" in the UI.
- **Debugging only in Chrome** when the bug is Safari-specific (e.g., `Intl.DateTimeFormat`, flexbox gaps).
- **Not testing in incognito mode** — browser extensions frequently break SPAs.

### 🧩 Complex Errors / Edge Cases
- **Third-party script interference:** Analytics, A/B testing, or chat widgets mutating the DOM or overwriting globals.
- **React StrictMode double-mounting:** Reveals cleanup bugs that are invisible in production.
- **Container queries vs viewport media queries:** Layout breaks inside nested components but works at page level.
- **Pointer event vs click event discrepancies:** Touch devices and stylus inputs behave differently from mouse clicks.

### 🎯 Expert Precision Tips
- Always check **Console → Network → Sources** in that order. 50% of frontend bugs are network or CORS issues.
- If a component isn't rendering, don't guess — use React DevTools Profiler to see if it's being unmounted or hidden by a parent.
- For layout bugs, add `outline: 1px solid red` to every element before touching CSS rules.
- SSR hydration mismatch? Search for `typeof window`, `Date`, `Math.random`, or `localStorage` in the render path.

---

# TASK 4 — Async/Race/Timing Diagnosis
*Best for: Intermittent bugs, Promise failures, stale data, or concurrency issues.*

## 4.1 Race Condition Detection Tree
```
Q1: Does the bug only appear under load or on slow networks? → Yes = likely race
Q2: Does the final state depend on which async call finishes first? → Yes = race
Q3: Does adding a 100ms setTimeout make the bug disappear? → Yes = timing-dependent
Q4: Is shared mutable state accessed by multiple async paths? → Yes = data race
```

## 4.2 Promise Failure Patterns
| Pattern | Symptom | Fix |
|---------|---------|-----|
| Missing `await` | Returns Promise instead of value | Add `await` or return the Promise |
| Unhandled rejection | Silent crash or process exit | Wrap in `try/catch` or use `.catch()` |
| `Promise.all` with partial failure | All fail if one fails | Use `Promise.allSettled` for independence |
| Floating Promise | No await, no `.catch()` | Assign and await, or attach error handler |

## 4.3 Forcing Reproducibility
For intermittent async bugs, force the issue:
```typescript
// Slow down specific path to invert race winner
await new Promise(r => setTimeout(r, 200));

// Force network latency in tests
await page.route('**/api/**', route => 
  setTimeout(() => route.continue(), 500)
);
```

### ⚠️ Common Errors While Diagnosing Async Bugs
- **Adding `await` everywhere** as a band-aid without understanding the Promise flow.
- **Using `setTimeout` to "fix" race conditions** — this just moves the probability, it doesn't eliminate the race.
- **Assuming `Promise.all` is always better** than sequential `await` — if operations are dependent, `all` makes debugging harder.
- **Not checking the event loop** in Node.js — a blocked event loop looks like a slow API.

### 🧩 Complex Errors / Edge Cases
- **Microtask vs macrotask ordering:** `Promise.resolve().then(...)` runs before `setTimeout(..., 0)`. This matters for UI state transitions.
- **Zalgo release:** A function that sometimes calls a callback synchronously and sometimes asynchronously. Makes ordering unpredictable.
- **Event loop starvation:** A long-running synchronous task blocks all async callbacks.
- **AbortController edge cases:** Aborting a completed fetch throws an unhandled rejection if `.catch()` is missing.

### 🎯 Expert Precision Tips
- Draw a **sequence diagram** for concurrent operations. If you can't draw it, you don't understand the concurrency.
- Use `Promise.allSettled` + explicit error mapping instead of wrapping `Promise.all` in a giant `try/catch`.
- To detect floating Promises, enable Node's `--unhandled-rejections=strict` or ESLint's `@typescript-eslint/no-floating-promises`.
- Force race conditions in tests by adding artificial delays to specific code paths.

---

# TASK 5 — Memory/Performance Diagnosis
*Best for: Slowdowns, memory leaks, high CPU, or OOM crashes.*

## 5.1 Layered Performance Diagnosis
```
Step 1 — Identify the symptom layer
  • UI jank → React re-renders, large DOM updates, unoptimized images
  • API slow → N+1 queries, missing indexes, large payloads
  • CPU bound → algorithmic complexity, tight loops, regex backtracking
  • Memory growth → leaks, unbounded caches, retained closures

Step 2 — Profile before optimizing
  • Web: Chrome DevTools Performance + Memory panels
  • Node: `node --inspect` + Chrome DevTools, or `clinic.js`
  • Python: `py-spy`, `scalene`, or Django Debug Toolbar
  • Java: `async-profiler`, VisualVM

Step 3 — Measure baseline, apply ONE change, re-measure
```

## 5.2 Memory Leak Hunt Checklist
- [ ] Event listeners added but never removed
- [ ] `setInterval` without `clearInterval`
- [ ] Subscriptions (WebSocket, RxJS, Redux) not unsubscribed
- [ ] Closures capturing large objects indefinitely
- [ ] Global caches growing without eviction (LRU missing)
- [ ] DOM nodes detached but retained in JS references

## 5.3 Node.js OOM Recipe
```bash
# 1. Confirm OOM in kernel logs
dmesg | grep -i oom

# 2. Add heap snapshot hook
process.on('SIGUSR2', () => require('v8').writeHeapSnapshot());

# 3. Trigger when memory is high
kill -USR2 <pid>

# 4. Analyze in Chrome DevTools Memory panel
#    Look for: detached DOM nodes, unbounded arrays, retained closures
```

## 5.4 Python Performance Recipe
```bash
# Attach live profiler without restarting
py-spy top --pid <gunicorn_pid>

# If ORM is the hotspot:
#   Add select_related() / prefetch_related()
#   Assert query count in test:
from django.db import connection
assert len(connection.queries) < 10
```

### ⚠️ Common Errors While Diagnosing Performance Issues
- **Optimizing before profiling** — premature optimization wastes time and often harms readability.
- **Measuring in development mode** — React dev mode is  →  x slower than production builds.
- **Fixing a symptom instead of the leak** — adding RAM doesn't fix a closure leak.
- **Not taking a baseline measurement** — you can't prove improvement without a "before" number.
- **Attacking the wrong layer** — adding a cache when the real issue is an unindexed query.

### 🧩 Complex Errors / Edge Cases
- **Retained closures in event handlers:** The handler looks cleaned up, but a closure inside it still references a large object.
- **V8 hidden class transitions:** Adding properties to an object in different orders causes deoptimization.
- **Memory fragmentation in long-running Node.js processes:** RSS grows while heap stays flat.
- **Heap snapshot illusion:** Objects held by a devtools extension or testing framework appear as leaks.

### 🎯 Expert Precision Tips
- Always take **two heap snapshots** (baseline and post-leak) and use the **Comparison** view, not the Summary view.
- Use Chrome DevTools **Allocation Timelines** for gradual leaks; use Heap Snapshots for sudden spikes.
- Profile **production-like builds**, not dev mode. For Node, use `NODE_ENV=production`.
- If CPU is the bottleneck, look for regex backtracking, nested loops over large arrays, or JSON serialization of huge objects.

---

# TASK 6 — Security Vulnerability Diagnosis
*Best for: Suspected injection, auth bypass, data exposure, or insecure dependencies.*

## 6.1 Security Scan Commands (Run First)
```bash
semgrep --config=auto --error .        # Multi-language security patterns
bandit -r backend/ -lll                # Python specific
npm audit --audit-level=moderate       # JS dependency vulnerabilities
shellcheck deploy/*.sh                 # Shell script injection risks
```

## 6.2 Input Validation Audit
For EVERY user-facing endpoint, verify:
- [ ] Null / undefined / empty inputs
- [ ] Maximum length enforced
- [ ] Type enforcement (not just TS types — runtime validation)
- [ ] Special characters / Unicode / emoji handled safely
- [ ] SQL/command/NoSQL injection vectors eliminated
- [ ] File upload limits, mime-type checks, and path traversal prevention

## 6.3 Auth/Authz Quick Checks
- [ ] Unauthenticated requests to protected routes return 401
- [ ] User A cannot access User B's data (IDOR test)
- [ ] Admin endpoints are restricted by role, not just hidden in UI
- [ ] JWT secrets are strong (≥32 chars) and rotated
- [ ] Sessions expire and are invalidated on logout

### ⚠️ Common Errors While Diagnosing Security Issues
- **Relying solely on automated scanners** — Semgrep catches ~40% of issues; business logic flaws require manual review.
- **Testing only the happy path for auth** — always test the negative cases (missing token, expired token, forged token).
- **Forgetting to check test files and logs** for hardcoded secrets or `console.log` of sensitive data.
- **Assuming frontend validation equals security** — attackers bypass the UI entirely.

### 🧩 Complex Errors / Edge Cases
- **TOCTOU (Time-of-check to time-of-use):** You check permissions, then the resource state changes before the operation executes.
- **Second-order injection:** Malicious input is stored safely initially, but retrieved and executed unsafely later.
- **SSRF via URL parsing discrepancies:** IDNA homographs, IPv6 encodings, or dotless domains bypass allowlists.
- **JWT `none` algorithm bypass:** A token with `alg: "none"` is accepted by poorly implemented libraries.
- **Prototype pollution:** User-controlled keys merged into objects can pollute `Object.prototype`.

### 🎯 Expert Precision Tips
- Assume **every input is malicious** until proven otherwise. This includes headers, query params, path segments, and file metadata.
- Check not just your code, but **generated code** — ORM queries, template renders, and build artifacts can introduce vulnerabilities.
- For auth bugs, draw a matrix of **Actors × Resources × Actions** and verify every cell.
- Review dependency changelogs for CVE fixes; an outdated minor version is often the attack vector.

---

# TASK 7 — Database/ORM Diagnosis
*Best for: Query errors, data inconsistency, schema mismatch, or migration issues.*

## 7.1 ORM/Debug Recipe
```python
# Django: log every query
from django.db import connection
print([q['sql'] for q in connection.queries])

# SQLAlchemy: echo queries
engine = create_engine(DATABASE_URL, echo=True)

# Prisma: inspect generated SQL
# Set log level: ['query', 'info', 'warn', 'error']
```

## 7.2 Common DB Bug Patterns
| Pattern | Symptom | Fix |
|---------|---------|-----|
| N+1 query | O(n) queries for a list | Use `select_related` / `join` / `include` |
| Missing index | Queries slow on large tables | Add indexed columns, verify with `EXPLAIN` |
| Migration drift | Column doesn't exist | Check pending migrations, schema sync |
| Transaction leak | Locks held too long | Reduce transaction scope, commit early |
| Connection exhaustion | App hangs under load | Use connection pooling, set timeouts |

## 7.3 Query Plan Analysis
```sql
-- PostgreSQL example: understand why a query is slow
EXPLAIN (ANALYZE, BUFFERS, FORMAT JSON)
SELECT * FROM orders WHERE user_id = 123;
```

### ⚠️ Common Errors While Diagnosing DB Issues
- **Adding indexes blindly** without measuring query plans — unused indexes slow down writes.
- **Running migrations out of order** across environments, causing schema drift.
- **Using `SELECT *` in ORM** without understanding the generated SQL — it often joins unnecessary tables.
- **Blaming the database** when the real issue is an unbounded `IN (...)` clause with 10,000 items.

### 🧩 Complex Errors / Edge Cases
- **Deadlocks due to inconsistent lock ordering:** Two transactions update tables A→B and B→A simultaneously.
- **Phantom reads under default isolation levels:** `READ COMMITTED` allows non-repeatable reads that break assumptions.
- **Connection pool exhaustion disguised as app slowness:** Requests queue up waiting for a DB connection.
- **Implicit type casting preventing index use:** Comparing a `text` column to an `integer` forces a sequential scan.

### 🎯 Expert Precision Tips
- Always run `EXPLAIN (ANALYZE, BUFFERS)` on slow queries in production-like data volumes.
- Use query loggers in **local development** to catch N+1s before they reach staging.
- Separate read and write transactions where possible; long read transactions hold back vacuum/reclamation.
- If a query is slow with a small dataset, it will be catastrophically slow at scale.

---

# TASK 8 — Type Safety / Static Error Diagnosis
*Best for: TypeScript, Python (mypy), Java, or any typed language compile-time failures.*

## 8.1 Type Error Resolution Protocol
```
1. Read the FULL error message, not just the summary.
2. Find the "origin" file, not the file where TS complains last.
3. Ask: "What assumption did the code make that the type system rejects?"
4. Fix the assumption, not the symptom. Avoid `as any` / `@ts-ignore` / `# type: ignore`.
5. If the type is genuinely unknown, use `unknown` and narrow explicitly.
```

## 8.2 TypeScript Specific Fixes
| Error | Root Cause | Fix |
|-------|------------|-----|
| `TS2322: Type X is not assignable to Y` | Mismatched shapes | Align interfaces or use discriminated unions |
| `TS2345: Argument of type X is not assignable` | Wrong argument passed | Validate/narrow before passing |
| `TS7006: Parameter implicitly has an any type` | Missing type annotation | Add explicit parameter type |
| `TS2532: Object is possibly undefined` | Missing null check | Add guard clause or optional chaining |

## 8.3 Python (mypy) Specific Fixes
| Error | Root Cause | Fix |
|-------|------------|-----|
| `Incompatible types in assignment` | Variable reassigned to different type | Use `Union` or separate variables |
| `Missing return statement` | All paths don't return | Add explicit return or raise |
| `Item None has no attribute X` | Optional not checked | Add `if x is not None:` guard |

### ⚠️ Common Errors While Fixing Type Errors
- **Using `as` casts to silence the compiler** — you've traded a compile-time error for a runtime crash.
- **Fixing the error at the call site** instead of the source type definition, causing the fix to be repeated everywhere.
- **Ignoring "origin" errors** and chasing downstream symptoms — read error stacks bottom-up.
- **Replacing `any` with `unknown` and then casting it immediately** — this is theater, not safety.

### 🧩 Complex Errors / Edge Cases
- **Contravariance / covariance issues in generics:** A `List<Dog>` is not a `List<Animal>` in most type systems.
- **Conditional types that distribute unexpectedly:** `T extends U ? X : Y` behaves differently for union types.
- **`any` leaking from third-party libraries:** One `any` in a dependency type can poison inference across your codebase.
- **`typeof x === 'object'` passing for `null`** — classic JavaScript footgun that breaks narrowing.

### 🎯 Expert Precision Tips
- Read TypeScript errors **bottom-up**: the last file is usually the symptom, the first file is the cause.
- When stuck on generics, remove them and test with concrete types first. Reintroduce abstraction only after it works.
- Use `satisfies` instead of `as` where possible — it checks compatibility without changing the inferred type.
- For Python, enable `--strict` in CI. Fixes under strict mode are almost always real bug prevents.

---

# TASK 9 — Silent Data Corruption Diagnosis
*Best for: Code that "works" but produces wrong results.*

## 9.1 Silent Bug Categories
- **Data Corruption:** Float precision, off-by-one, mutation of shared state, encoding issues.
- **Performance Bombs:** N+1 queries, unbounded caching, O(n²) loops.
- **Security Failures:** Fail-open auth, weak validation, sensitive data logging.
- **Async Failures:** Missing `.catch()`, race conditions, forgotten `await`.

## 9.2 Data Integrity Checklist
- [ ] Are monetary calculations done in integer cents, not float?
- [ ] Are dates parsed with explicit timezone handling?
- [ ] Is string encoding consistent (UTF-8) across read/write boundaries?
- [ ] Are UUIDs/generated IDs truly unique or is there a collision risk?
- [ ] Does sorting use a stable comparator?

## 9.3 Reproducing Silent Bugs
```typescript
// Property-based tests excel here
import fc from 'fast-check';

it('sort is stable and idempotent', () => {
  fc.assert(
    fc.property(fc.array(fc.integer()), (arr) => {
      const sorted = [...arr].sort((a, b) => a - b);
      expect([...sorted].sort((a, b) => a - b)).toEqual(sorted);
      expect(sorted.length).toBe(arr.length);
    }),
    { numRuns: 1000 }
  );
});
```

### ⚠️ Common Errors While Diagnosing Silent Bugs
- **Trusting floating point for financial calculations** — `0.1 + 0.2 !== 0.3`.
- **Not validating encoding** when reading files or parsing network responses.
- **Assuming JSON parsing preserves key order** — objects are unordered in most languages.
- **Testing with small datasets** that don't trigger overflow, precision loss, or O(n²) behavior.

### 🧩 Complex Errors / Edge Cases
- **Daylight saving time transitions:** A 1:30 AM local time may not exist or may exist twice, causing off-by-one-hour bugs.
- **Unicode normalization differences:** `café` as NFC (`é` as single char) vs NFD (`e` + combining accent) fails string equality.
- **Race conditions in cached computations:** Stale data looks valid because it passes format checks but is semantically wrong.
- **Big-endian vs little-endian serialization:** Cross-platform binary data corruption.

### 🎯 Expert Precision Tips
- Use **property-based tests** for every data transformation function. They find edge cases you won't think of.
- Log checksums/hashes for critical data at system boundaries to detect corruption early.
- Store money as **integer cents**, dates as **UTC ISO-8601**, and strings as **normalized UTF-8 (NFC)**.
- If a result "looks right," verify it mathematically or against a reference implementation.

---

# TASK 10 — Production/Infra Incident Diagnosis
*Best for: Live system outages, 500 spikes, or infrastructure-level failures.*

## 10.1 Production Triage Order
```
1. MITIGATE (stop the bleeding)
   - Scale up, rollback, enable feature flags, redirect traffic
2. IDENTIFY (find the scope)
   - Which service? Which endpoint? Which customers? Which region?
3. INVESTIGATE (find the trigger)
   - Recent deploys, traffic spikes, dependency failures, data changes
4. RESOLVE (apply targeted fix)
5. PREVENT (add monitoring, tests, runbooks)
```

## 10.2 Essential Commands
```bash
# Live process inspection
ps aux | grep <service>
strace -p <pid> -e trace=network,file  # system calls
lsof -p <pid> | wc -l                  # open file descriptors

# Log investigation
grep -i "error\|exception\|fatal" /var/log/app.log | tail -n 100
journalctl -u myservice --since "10 minutes ago"

# Network/dependency health
curl -s -o /dev/null -w "%{http_code}" http://localhost:8080/health
netstat -tulpn | grep <port>
```

## 10.3 Dashboards to Check
- Error rate by endpoint
- P95/P99 latency spikes
- CPU / memory / disk utilization
- Database connection pool saturation
- Queue depth / consumer lag
- External dependency error rates

### ⚠️ Common Errors During Incident Response
- **Investigating before mitigating** — every minute of outage costs money and trust.
- **Fixing forward instead of rolling back** during active incidents — rollback is almost always faster.
- **Not communicating** with stakeholders while you triage.
- **Deleting logs or pods** before extracting data — preserve evidence first.

### 🧩 Complex Errors / Edge Cases
- **Cascading failures:** Fixing service A redirects so much load to service B that B fails.
- **Thundering herd after recovery:** Thousands of clients retry simultaneously, causing a second outage.
- **Split-brain in distributed systems:** Two nodes believe they are the leader, causing data divergence.
- **Resource exhaustion disguised as code bugs:** File descriptor limits, thread pool saturation, or DNS lookup caching.

### 🎯 Expert Precision Tips
- **Mitigate first.** Rollback is your friend. Forward-fixes during incidents are high-risk gambles.
- Establish a clear **incident commander** and a separate **communication channel** (Slack/Teams) immediately.
- Write a **timeline** of events *during* the incident, not after — human memory degrades within minutes under stress.
- After resolution, run a **blameless postmortem** focused on system fixes, not personal fault.

---

# TASK 11 — Tool Arsenal by Layer
*Use the cheapest tool that could possibly reveal the issue.*

## 11.1 Static Analysis (Layer 0)
| Tool | Language | Command |
|------|----------|---------|
| **Semgrep** | Multi | `semgrep --config=auto .` |
| **CodeQL** | Multi | `codeql database create db && codeql database analyze db` |
| **mypy** | Python | `mypy src/ --strict` |
| **tsc** | TypeScript | `tsc --noEmit` |
| **ShellCheck** | Shell | `shellcheck *.sh` |
| **Infer** | Java, C/C++ | `infer run -- make` |
| **SpotBugs** | Java | `mvn spotbugs:check` |

## 11.2 Dynamic Profiling (Layer 2)
| Tool | Language | Command |
|------|----------|---------|
| **py-spy** | Python | `py-spy top --pid 1234` |
| **perf** | Linux | `perf record -g ./app && perf report` |
| **speedscope** | Any | `speedscope profile.svg` |
| **strace** | Linux | `strace -fp 1234` |
| **Chrome DevTools** | Web | `F12` → Performance/Memory |

## 11.3 Memory & Thread Analysis (Layer 3)
| Tool | Use Case | Command |
|------|----------|---------|
| **Valgrind memcheck** | Memory leaks | `valgrind --leak-check=full --track-origins=yes ./app` |
| **Valgrind helgrind** | Data races | `valgrind --tool=helgrind ./app` |
| **ASan** | Memory corruption | `clang -fsanitize=address -g -O1` |
| **UBSan** | Undefined behavior | `clang -fsanitize=undefined` |
| **TSan** | Data races | `clang -fsanitize=thread -g -O1` |
| **MSan** | Uninitialized memory | `clang -fsanitize=memory -g -O1` |

> **Rule:** ASan + UBSan can share a binary. TSan and MSan need separate builds.

## 11.4 Advanced Hidden-Error Detection
| Technique | Tool | Catches |
|-----------|------|---------|
| **Fuzzing** | AFL++, libFuzzer | Crashes, overflows |
| **Symbolic Execution** | KLEE, angr | Deep logic bugs |
| **Taint Analysis** | Taintgrind | Injection flows |
| **Mutation Testing** | mutmut, Stryker | Weak tests |
| **Hybrid** | Driller | Complex branches |

### ⚠️ Common Errors While Using Diagnostic Tools
- **Running expensive dynamic analysis before cheap static analysis** — use `tsc` before Valgrind.
- **Using TSan and ASan in the same binary** — they conflict and produce garbage results.
- **Not enabling debug symbols** when using Valgrind/ASan — stack traces will be useless.
- **Trusting a single tool's output** without cross-checking with another layer.

### 🧩 Complex Errors / Edge Cases
- **False positives in static analysis:** Some patterns are safe in context but flagged. Document suppressions with justification.
- **Heisenbugs that disappear under instrumentation:** The tool slows execution enough to prevent the race condition.
- **Fuzzing plateau:** Coverage stops growing. Switch to hybrid approaches (Driller) or seed with real inputs.
- **Sanitizer overhead in production:** ASan can slow execution by  →  x. Run it in CI, not live traffic.

### 🎯 Expert Precision Tips
- Follow the **Layer rule:** start at Layer 0 (static analysis), escalate only when the cheaper layer is exhausted.
- Keep a **"sanitizer CI" job** separate from regular tests due to performance overhead.
- Use `perf` with frame pointers (`-fno-omit-frame-pointer`) for accurate call graphs.
- When Valgrind is too slow for large apps, try ASan first; it's faster and catches most of the same issues.

---

# TASK 12 — Red Flags: STOP and Return to Phase 1

If you catch yourself doing any of the following, **STOP immediately**:
- "Quick fix for now, investigate later"
- "Just try changing X and see if it works"
- Adding multiple changes before running tests
- Skipping the failing test
- "I don't fully understand but this might work"
- Proposing solutions before tracing data flow
- "One more fix attempt" (after 2+ failures)

**All of these mean: STOP. Return to Phase 1.**


---

## PART 4: TEST STRATEGY

# 02 — Test Strategy: Master Testing Reference

> **Philosophy:** Your job is to BREAK the code, not prove it works.  
> **Sources:** [Superpowers TDD](https://github.com/obra/superpowers/blob/main/skills/test-driven-development/SKILL.md) · [Microsoft Playbook](https://github.com/microsoft/code-with-engineering-playbook) · [fast-check](https://github.com/dubzzz/fast-check) · [Professional Programming](https://github.com/charlax/professional-programming)

---

## 🎯 CONSTANT CORE — APPLY BEFORE EVERY TESTING TASK

```
STEP 0 — MANDATORY PRE-TESTING CHECKLIST
□ Identify what you're testing: pure function, component, API endpoint, or user flow
□ Determine the test layer: unit | integration | E2E | property | mutation | a11y
□ Select the matching task-specific section below — do NOT read the whole file
□ Verify there is a clear pass/fail criterion before writing the first line of test code
```

```
STEP 0 — UNIVERSAL TESTING CONTRACT
1. Red first. No production code without a failing test.
2. One concept per test. Name the test after the behavior it verifies.
3. Assert outcomes, not implementation. Test WHAT, not HOW.
4. Mock only external I/O (network, filesystem, time). Prefer real integrations.
5. Every bug fix MUST include a regression test that fails before the fix.
```

```
STEP 0 — MANDATORY ONLINE SEARCH TOOL
□ If the testing approach, framework version, or best practice is unfamiliar or may have changed, search SearXNG first for the most updated official notes and solutions.
□ SearXNG: https://github.com/searxng/searxng — free, open-source metasearch engine that aggregates 70+ search engines without tracking users or storing queries.
□ Do not guess based on stale knowledge. Verify with up-to-date sources before proceeding.
```

## 📑 TASK INDEX — Jump to your specific testing task

```
Task     Topic                                         When to Use
----------------------------------------------------------------------------------
TASK 1   TDD Workflow: Red → Green → Refactor  →  Foundational rhythm for all test writing
TASK 2   Adversarial Test Suite Design  →  Writing tests for new code
TASK 3   Unit Testing by Language  →  Fast isolated logic tests by language
TASK 4   Integration Testing Patterns  →  Component wiring and API contracts
TASK 5   E2E Testing with Playwright  →  Critical user journeys
TASK 6   Property-Based Testing  →  Pure functions and algorithms
TASK 7   Mutation Testing  →  Verifying test quality
TASK 8   Accessibility Testing  →  UI component a11y validation
TASK 9   Stabilizing Flaky Tests  →  Non-deterministic test fixes
TASK 10  Security Testing Matrix  →  Endpoints handling user data
TASK 11  CI/CD Pipeline Recipes  →  Automated delivery integration
TASK 12  Coverage & Quality Metrics  →  Measuring test health
```

---

# TASK 1 — TDD Workflow: Red → Green → Refactor
*Use this as the foundational rhythm for ALL test writing.*

## The Iron Law
```
NO PRODUCTION CODE WITHOUT A FAILING TEST FIRST
```

## The Cycle
1. **RED** — Write one minimal test showing expected behavior. Clear name, one thing, real code.
2. **Verify RED** — Run the test. Confirm it fails for the *expected reason* (missing feature, not typo).
3. **GREEN** — Write the simplest code to pass.
4. **Verify GREEN** — All tests pass, output pristine (no warnings).
5. **REFACTOR** — Clean up duplication and names. Keep tests green. Don't add behavior.
6. **REPEAT**

## TDD Anti-Patterns to Avoid
- **Tautological tests** — `expect(result).toBe(result)`
- **Over-mocking** — More mocks than real operations
- **Testing internals** — Asserting on private methods or state
- **Giant tests** — One test verifying 10 behaviors
- **False green** — Test passes because it never runs the assertion path

### ⚠️ Common Errors While Doing TDD
- **Writing multiple tests before any production code** — you lose the feedback loop.
- **Making the test pass by hardcoding the expected output** — the implementation is fake.
- **Refactoring while the test is red** — you don't know if the refactor broke something.
- **Not running tests frequently** — if you write 50 lines without running tests, you're not doing TDD.
- **Writing tests that are too abstract** — "it should work" is not a testable behavior.

### 🧩 Complex Errors / Edge Cases
- **False red:** The test fails because of a typo in the test itself, not because the feature is missing. Always read the error message carefully.
- **Entangled tests:** Tests that depend on execution order or shared mutable state. They pass individually but fail in random order.
- **Over-refactoring in the green phase:** Adding "just one more abstraction" that changes behavior subtly.
- **Testing the test framework:** Writing tests so complex they have their own bugs.

### 🎯 Expert Precision Tips
- The red phase should fail for **exactly one reason**: the behavior is missing. If it fails for syntax or import errors, fix those first.
- Keep refactor changes **mechanical** (rename, extract function, inline variable). If a refactor requires test changes, it isn't a pure refactor.
- If you feel the urge to "just try this," write a test that captures the expected behavior of "this" first.
- Use the "obvious implementation" or "fake it till you make it" strategies when stuck, but transition to real algorithms quickly.

---

# TASK 2 — Adversarial Test Suite Design
*Use this when writing tests for new code.*

## Distribution Matrix
Distribute tests across 5 tiers:

| Tier | Focus | Min % | Examples |
|------|-------|-------|----------|
| **1 — Happy Path** | Standard valid inputs | 20% | Normal user creation, typical search query |
| **2 — Boundary & Edge** | Limits and extremes | 40% | Empty, null, MAX_INT, Unicode, negative, huge inputs |
| **3 — Error & Rejection** | Invalid inputs | 25% | Wrong types, malformed data, missing fields, injection |
| **4 — Contract Tests** | Invariants and side effects | 15% | Return types, no hidden mutation, idempotency |
| **5 — Mutation Tests** | Test quality meta-check | As needed | Would tests catch a single-line code change? |

## Boundary Value Examples
```typescript
// Numbers
[-Infinity, -1, 0, 1, MAX_SAFE_INTEGER, Infinity, NaN]

// Strings
['', 'a', ' '.repeat(10000), '🚀emoji', '\x00nullbyte', '<script>alert(1)</script>']

// Arrays
[[], [1], Array(1000).fill(1), Array(1000000).fill(1)]

// Objects
[{}, { id: null }, { extra: 'unexpected' }, null, undefined]
```

### ⚠️ Common Errors While Designing Test Suites
- **Over-indexing on happy paths** — most bugs live at boundaries.
- **Using the same boundary value for every test** — each function has different critical boundaries.
- **Forgetting to test the inverse** of a condition — if you test `isValid(email)` with a valid email, you must also test an invalid one.
- **Testing implementation details** — e.g., asserting that a specific helper was called.
- **Mirror testing:** The test replicates the implementation logic, so it passes even when the implementation is wrong.

### 🧩 Complex Errors / Edge Cases
- **Tests that pass but don't exercise the code path:** An exception is thrown before the assertion, so the assertion never runs.
- **Implicit coupling between boundary values and implementation:** The test breaks when the implementation changes its internal threshold.
- **Combinatorial explosion:** Testing every possible combination of 5 inputs. Use equivalence partitioning instead.
- **State leakage across test files:** Global caches, module-level variables, or environment variables modified by one test break others.

### 🎯 Expert Precision Tips
- Every `if` in production code needs at least **two tests** (true and false branches).
- Use **equivalence partitioning:** one test per partition, plus explicit boundary tests.
- For every error path, assert the **exact error message or type**, not just "it throws."
- If a boundary value requires more than one line of setup, extract a factory or helper to keep the test readable.

---

# TASK 3 — Unit Testing by Language
*Use this for fast, isolated logic tests.*

## 3.1 Python — pytest
```python
# Fixture + parametrization example
import pytest

@pytest.fixture
def empty_cart():
    return Cart()

@pytest.mark.parametrize("code,expected", [
    ("SAVE10", 0.10),
    ("", 0.0),
    ("INVALID", 0.0),
])
def test_apply_discount(empty_cart, code, expected):
    empty_cart.add_item(price=100)
    assert empty_cart.apply_discount(code) == pytest.approx(expected)
```

**pytest Best Practices:**
- Use fixtures for shared setup, not global state.
- Parametrize edge cases, not copy-paste tests.
- Assert with `pytest.approx` for floats.
- Use `monkeypatch` or `pytest-mock` for I/O boundaries only.

## 3.2 JavaScript/TypeScript — Vitest
```typescript
import { describe, it, expect } from 'vitest';

describe('calculateTotal', () => {
  it('sums prices with tax', () => {
    expect(calculateTotal(100, 0.08)).toBe(108);
  });

  it('rejects negative price', () => {
    expect(() => calculateTotal(-1, 0.08)).toThrow('Price must be non-negative');
  });
});
```

**Vitest Best Practices:**
- Prefer `it('should...')` with descriptive behavior names.
- Use `expectTypeOf` (from `vitest`) for compile-time type assertions.
- Isolate test data; never rely on execution order.

## 3.3 Java — JUnit 5
```java
@ParameterizedTest
@CsvSource({
  "100, 0.08, 108",
  "0, 0.08, 0",
  "100, 0, 100"
})
void calculatesTotal(int price, double taxRate, int expected) {
    assertEquals(expected, calculator.total(price, taxRate));
}
```

## 3.4 C++ — Google Test
```cpp
TEST(CalculatorTest, TotalWithTax) {
    Calculator calc;
    EXPECT_EQ(calc.total(100, 0.08), 108);
    EXPECT_THROW(calc.total(-1, 0.08), std::invalid_argument);
}
```

### ⚠️ Common Errors While Writing Unit Tests
- **Over-using integration tests as unit tests** — they run slow and fail opaquely.
- **Not resetting global state between tests** — test A passes, test B fails because of A.
- **Testing implementation details** (private methods, internal state) instead of observable behavior.
- **Mocking internal collaborators** — you're testing your imagination, not the system.
- **Ignoring test readability** — if the test name doesn't explain the behavior, it will be deleted later.

### 🧩 Complex Errors / Edge Cases
- **Test pollution from shared mutable fixtures:** A fixture object is mutated by test A and reused by test B.
- **Timezone-dependent tests:** Pass locally (your timezone) but fail in CI (UTC).
- **Partial mocks (mocking the SUT):** The object under test has some methods mocked and some real, creating impossible states.
- **Floating-point assertions:** `assert 0.1 + 0.2 == 0.3` fails due to IEEE 754 representation.

### 🎯 Expert Precision Tips
- One assertion per **concept**, not necessarily one assertion per test.
- Use **factories** over fixtures for complex objects. Factories are more explicit and flexible.
- Parameterize edge cases; copy-paste tests are a smell.
- For Python, use `tmp_path` for file I/O instead of mocking `open()`.
- For JS/TS, prefer `toStrictEqual` over `toEqual` to catch unexpected extra properties.

---

# TASK 4 — Integration Testing Patterns
*Use this for testing component wiring, API contracts, and database interactions.*

## 4.1 API Integration Tests
```python
def test_create_user_flow(client, db_session):
    # Given
    payload = {"email": "test@example.com", "password": "Secure123!"}

    # When
    response = client.post("/api/users", json=payload)

    # Then
    assert response.status_code == 201
    assert response.json()["email"] == payload["email"]
    assert db_session.query(User).filter_by(email=payload["email"]).first() is not None
```

## 4.2 Database Test Isolation
- Use **transaction rollback** after each test.
- Never share database state between tests.
- Use **factories** (not fixtures with hardcoded data) for test data.
- Assert on **query count** to catch N+1 regressions.

## 4.3 Contract Testing (Consumer-Driven)
```typescript
// Pact example: consumer test
const interaction = {
  state: 'user exists',
  uponReceiving: 'a request for user by id',
  withRequest: { method: 'GET', path: '/users/1' },
  willRespondWith: {
    status: 200,
    body: Matchers.like({ id: 1, email: 'a@b.com' }),
  },
};
```

### ⚠️ Common Errors While Writing Integration Tests
- **Using production databases or external services** — tests become slow, flaky, and non-deterministic.
- **Not isolating test data** — two tests create a user with the same email and one fails.
- **Testing too many components at once** — when the test fails, you can't tell which component broke.
- **Not asserting on side effects** — the API returns 201, but the database wasn't actually updated.
- **Hardcoding IDs or timestamps** — causes collisions and flakiness.

### 🧩 Complex Errors / Edge Cases
- **Transaction rollback failing** in frameworks that auto-commit (e.g., some NoSQL stores or certain SQL configurations).
- **Async cleanup not completing** before the next test starts — connections leak or files remain locked.
- **Network timeouts causing intermittent failures** — external mocks aren't deterministic.
- **Schema migrations not applied** in the test database, causing false positives.

### 🎯 Expert Precision Tips
- Assert on **both** the API response AND the database state for full-stack integration tests.
- Use **testcontainers** for real database dependencies (PostgreSQL, Redis, etc.) when the in-memory alternative behaves differently.
- Keep integration tests focused on **one contract at a time** — don't verify 10 behaviors in one request.
- Use unique identifiers (UUIDs) for test data to eliminate collision risk.
- For API tests, follow Given-When-Then structure explicitly in the test body.

---

# TASK 5 — E2E Testing with Playwright
*Use this for critical user journeys across the full stack.*

## Playwright Best Practices
- Use **semantic locators** (`getByRole`, `getByLabel`) over CSS selectors.
- Enable **`trace: 'on-first-retry'`** for failure replay.
- Isolate test data; never rely on state from a previous test.
- Run against **production-like data** where possible.

## E2E Scenario Classes
1. **Complete User Journeys** — signup → login → checkout
2. **Broken Journeys** — network drops, session expiry, concurrent modification
3. **Permission Boundaries** — User A accessing User B's data
4. **Data State Tests** — empty DB, single record, 1000+ records
5. **Chaos Tests** — double-submit, disconnect mid-request, 2G simulation

## Example Playwright Test
```typescript
import { test, expect } from '@playwright/test';

test('user can complete checkout', async ({ page }) => {
  await page.goto('/shop');
  await page.getByRole('button', { name: 'Add to Cart' }).click();
  await page.getByRole('link', { name: 'Cart' }).click();
  await page.getByRole('button', { name: 'Checkout' }).click();
  await page.fill('[name="cardNumber"]', '4111111111111111');
  await page.getByRole('button', { name: 'Pay' }).click();
  await expect(page.getByText('Order confirmed')).toBeVisible();
});
```

### ⚠️ Common Errors While Writing E2E Tests
- **Using brittle CSS selectors** like `.btn-3 > div` — they break on every design tweak.
- **Relying on sleep/wait instead of auto-waiting** — `await page.waitForTimeout(1000)` is a code smell.
- **Not cleaning up test data** — leaving orders/users in the DB breaks subsequent test runs.
- **Testing too many things in one flow** — a 50-step test is impossible to debug when it fails at step 37.
- **Running E2E tests against development servers** — dev mode is too slow and noisy.

### 🧩 Complex Errors / Edge Cases
- **Third-party auth (OAuth) flows:** Popup windows, cross-origin redirects, and CAPTCHAs are hard to automate. Use test bypass endpoints.
- **File upload dialogs:** OS-native dialogs can't be automated by Playwright directly. Use `page.setInputFiles()` instead.
- **Tests passing locally but failing in CI** due to resource constraints (slower CPU, less RAM) or different viewport sizes.
- **Flakiness from font loading or image rendering:** Visual assertions differ slightly across environments.

### 🎯 Expert Precision Tips
- Use `data-testid` or **semantic roles** (`getByRole('button', { name: 'Submit' })`) as primary locators.
- Parallelize by **worker**, never by test file sharing state. Use `fullyParallel: true` in Playwright config.
- Record traces on first retry and **watch the trace** for every failure — it's faster than re-running locally.
- Seed the test database with exactly the data the test needs. Never assume another test created it.
- For OAuth, implement a `/api/test-login` endpoint that creates a valid session directly.

---

# TASK 6 — Property-Based Testing
*Use this for pure functions, data transformations, and algorithms.*

## fast-check (JS/TS)
```typescript
import fc from 'fast-check';

it('round-trips valid numbers', () => {
  fc.assert(
    fc.property(fc.float({ noNaN: true }), (n) => {
      expect(parseFloat(n.toFixed(2))).toBeCloseTo(n, 2);
    }),
    { numRuns: 1000 }
  );
});
```

## Hypothesis (Python)
```python
from hypothesis import given, strategies as st

@given(st.lists(st.integers()))
def test_sort_idempotent(arr):
    assert sorted(sorted(arr)) == sorted(arr)

@given(st.text())
def test_normalize_never_crashes(text):
    assert isinstance(normalize(text), str)
```

## Essential Property Patterns
| Pattern | Invariant | Catches |
|---------|-----------|---------|
| **Round-trip** | `parse(format(x)) == x` | Serialization bugs |
| **Idempotence** | `f(f(x)) == f(x)` | Non-determinism |
| **Commutativity** | `add(x,y) == add(y,x)` | Order bugs |
| **Inverse** | `decrypt(encrypt(x)) == x` | Crypto/logic bugs |
| **Postcondition** | `sorted(x)[i] <= sorted(x)[i+1]` | Algorithm bugs |
| **No-throw** | `f(x)` never throws for valid domain | Missing edge handling |

## Property Test Requirement (Pure Functions)
For every pure function or data transformation:
- Write property-based tests using `fast-check` or `Hypothesis`
- Run with `numRuns >= 1000`
- Include at least: **"never throws"**, **"structural invariant"**, **"idempotency"**

### ⚠️ Common Errors While Writing Property Tests
- **Writing properties that are too specific** — they replicate the implementation logic.
- **Not shrinking failing cases properly** — a failure with a 10,000-element array is impossible to debug.
- **Running with too few examples** (`numRuns < 100`) — misses edge cases.
- **Using non-deterministic functions inside the property** — e.g., `Math.random()` or `Date.now()`.
- **Forgetting to constrain generators** — generating `NaN` or `Infinity` when the function doesn't handle them.

### 🧩 Complex Errors / Edge Cases
- **Properties that hold for small inputs but fail for large ones:** Integer overflow, stack overflow on deeply nested structures.
- **Non-deterministic functions making properties flaky:** Async operations, unseeded randomness, or time-dependent logic.
- **Floating-point precision breaking invariants:** `a + b == b + a` can fail for very large floats due to rounding.
- **Generators producing values outside the function's domain:** The property fails because the generator is wrong, not the function.

### 🎯 Expert Precision Tips
- Start with **"never crashes"** properties before complex invariants.
- Use **custom arbitraries** (generators) for domain-specific types (e.g., valid email strings, non-empty arrays).
- Reproduce shrinking failures with a **seed** for deterministic debugging.
- Combine property tests with example-based tests: properties find unknown edge cases, examples document specific business rules.
- For money/finance, use integer-based generators, not floats.

---

# TASK 7 — Mutation Testing
*Use this to verify your tests are actually catching bugs.*

## Tools & Commands
| Tool | Language | Command | Goal |
|------|----------|---------|------|
| **mutmut** | Python | `mutmut run --paths-to-mutate=src/core.py` | 80%+ mutation score |
| **Stryker** | JS/TS | `npx stryker run` | 80%+ mutation score |

## What Surviving Mutants Reveal
- **Weak assertions** (`assert result is not None`)
- **Dead code** (executed but never checked)
- **Missing edge cases**

## Interpreting Results
```
Score < 60%  → Tests are mostly theater. Rewrite with stronger assertions.
Score  →  % → Good coverage, but gaps in edge cases and error paths.
Score > 80%  → Solid test suite. Focus on integration/E2E gaps.
```

### ⚠️ Common Errors While Running Mutation Tests
- **Running mutation tests on code with 0% coverage** — mutation testing tests the tests, not the code.
- **Ignoring equivalent mutants** instead of documenting them in the config.
- **Chasing 100% mutation score** at the cost of unreadable tests or trivial assertions.
- **Running mutation tests on generated/config code** — boilerplate will generate meaningless mutants.

### 🧩 Complex Errors / Edge Cases
- **Equivalent mutants:** A code change that behaves identically to the original for all possible inputs. No test can kill it.
- **Mutants surviving in framework boilerplate:** E.g., Express middleware or React hooks wrappers that aren't business logic.
- **Long mutation testing runs discouraging CI integration:** A full run takes 30+ minutes on large codebases.
- **False confidence from high score on trivial code:** A function that just returns a constant is easy to mutate-test perfectly.

### 🎯 Expert Precision Tips
- Target mutation testing on **business-critical modules** first. Don't run it on UI components or generated code.
- Configure Stryker/mutmut to **exclude framework boilerplate, test utilities, and config files**.
- A score of **80%+ on core logic** is excellent. Above 90% often indicates diminishing returns.
- Use mutation testing as a **periodic audit** (e.g., weekly or per-release), not a per-commit gate, unless your codebase is small.

---

# TASK 8 — Accessibility Testing
*Use this for all UI components.*

## axe-core + Testing Library
```tsx
import { render } from '@testing-library/react';
import { axe, toHaveNoViolations } from 'jest-axe';

expect.extend(toHaveNoViolations);

test('component has no a11y violations', async () => {
  const { container } = render(<LoginForm />);
  expect(await axe(container)).toHaveNoViolations();
});
```

## Manual a11y Checklist
- [ ] All interactive elements have accessible names
- [ ] Color contrast ratio ≥ 4.5:1 for normal text
- [ ] Focus order is logical and visible
- [ ] Form inputs have associated labels
- [ ] Images have meaningful alt text (or `alt=""` for decorative)
- [ ] No keyboard traps

### ⚠️ Common Errors While Testing Accessibility
- **Relying solely on automated axe-core scans** — they catch only ~30% of accessibility issues.
- **Testing a11y in isolation without keyboard navigation** — many users never touch a mouse.
- **Using `aria-label` as a crutch for missing semantic HTML** — prefer `<button>` over `<div role="button" aria-label="...">`.
- **Not testing with real content** — placeholder text may pass axe but fail user comprehension.

### 🧩 Complex Errors / Edge Cases
- **Focus management in SPAs:** Route changes must move focus to the new page heading or users are lost.
- **Dynamic content updates not announced:** Live regions (`aria-live`) are needed for toast notifications and loading states.
- **Complex data tables:** Missing `scope` or `headers` attributes make tables unreadable to screen readers.
- **Modal dialogs:** Focus must be trapped inside the modal and returned to the triggering element on close.

### 🎯 Expert Precision Tips
- Perform a **manual keyboard test** of every interactive flow at least once.
- Use a real screen reader (**NVDA on Windows, VoiceOver on macOS**) for critical user journeys.
- Automated scans are a **baseline, not a certificate** of accessibility.
- Test with **zoomed browser views** (200%+) to ensure layouts don't break for low-vision users.
- Never remove focus outlines without providing a visible alternative.

---

# TASK 9 — Stabilizing Flaky Tests
*Use this when tests pass/fail non-deterministically.*

## Flaky Test Root Causes & Fixes
| Cause | Fix |
|-------|-----|
| **Timing** | Use Playwright auto-waiting; avoid `setTimeout` in tests |
| **Shared mutable state** | Isolate data with unique IDs; rollback transactions |
| **Non-deterministic order** | Sort collections before asserting |
| **External dependencies** | Mock APIs; use deterministic test doubles |
| **Date/time** | Freeze time (`freezegun`, `vi.useFakeTimers()`) |
| **Browser rendering** | Wait for specific elements, not `networkidle` |
| **Random data** | Use seeded random generators in tests |

## Flaky Test Policy
```
1. A flaky test is WORSE than no test. It destroys CI trust.
2. If a test is flaky, quarantine it immediately (skip with ticket reference).
3. Fix the flakiness before re-enabling.
4. Never "retry until pass" as a permanent solution.
```

### ⚠️ Common Errors While Fixing Flaky Tests
- **Adding retries instead of fixing the root cause** — retries mask real bugs and slow CI.
- **Increasing timeouts to hide performance problems** — a 30s timeout that occasionally fails means the system is too slow.
- **Mocking time without restoring it** — `vi.useFakeTimers()` left on breaks every subsequent test.
- **Blaming the CI runner** without evidence — most flakiness is deterministic logic errors.

### 🧩 Complex Errors / Edge Cases
- **Resource exhaustion in CI runners:** Parallel tests exhaust CPU, causing nondeterministic timeouts.
- **Browser font loading causing layout shift:** A button moves 1px after the font loads, breaking a visual assertion.
- **Database connection pool saturation:** Parallel test runs compete for connections, causing intermittent query timeouts.
- **Race conditions in test setup:** Test B starts before test A's async cleanup finishes.

### 🎯 Expert Precision Tips
- **Quarantine flaky tests immediately.** A flaky test destroys CI confidence faster than a consistently failing test.
- Run suspected flaky tests in a loop (`for i in {1..100}; do pytest test_file.py; done`) locally to confirm stability.
- Prefer **deterministic test doubles** over real network calls. Network is the #1 source of flakiness.
- Use `Promise.all` for parallel async setups, but ensure **await** on every cleanup promise.
- If a test depends on `Date.now()`, it is flaky by definition. Freeze time or inject a clock.

---

# TASK 10 — Security Testing Matrix
*Use this for any endpoint or function handling user data.*

## Input Fuzzing Checklist
- [ ] Null / undefined / empty inputs
- [ ] Extremely long inputs (boundary overflow)
- [ ] Special characters / Unicode / emoji
- [ ] Type mismatches (send string where number expected)
- [ ] Malformed JSON / XML
- [ ] Injection attempts (SQL, XSS, NoSQL, command)
- [ ] Path traversal (`../../etc/passwd`)
- [ ] Privilege escalation (User A → User B resources)

## Security Test Example
```python
def test_rejects_sql_injection_in_search():
    malicious = "'; DROP TABLE users; --"
    response = client.get("/api/search", params={"q": malicious})
    assert response.status_code in (200, 400)
    # Verify table still exists
    assert client.get("/api/users").status_code == 200
```

### ⚠️ Common Errors While Security Testing
- **Only testing for SQL injection** and ignoring NoSQL injection, command injection, or XPath injection.
- **Testing with benign payloads** instead of real attack vectors.
- **Not verifying that failed attacks leave no side effects** — a 400 response is fine, but did the DB still get partially written?
- **Trusting frontend validation** — attackers bypass the UI entirely.
- **Testing admin endpoints with a regular user** but forgetting to test regular endpoints with an admin user (over-permissioning).

### 🧩 Complex Errors / Edge Cases
- **Polyglot payloads:** A single input that bypasses multiple validation layers (e.g., SQLi + XSS + path traversal).
- **Race conditions in authorization checks:** User A requests a resource; you check access, then the resource owner changes before the operation executes.
- **Business logic flaws:** A user can cancel another user's order because the endpoint accepts an `order_id` without checking ownership.
- **Second-order attacks:** Input is stored safely but retrieved and used unsafely later (stored XSS, delayed SQLi).

### 🎯 Expert Precision Tips
- Use a systematic **OWASP-based checklist** for every endpoint.
- Fuzz all user inputs with tools like `ffuf`, `wfuzz`, or custom scripts.
- Verify that security headers (**CSP, HSTS, X-Frame-Options, X-Content-Type-Options**) are present on every response.
- For auth, draw a matrix of **Actors × Resources × Actions** and verify every cell has the correct HTTP status.
- Test with **multiple concurrent sessions** — some auth bugs only appear when users race.

---

# TASK 11 — CI/CD Pipeline Recipes
*Use this to integrate tests into automated delivery.*

## Recipe 1: Quick Sweep (< 60 seconds)
```bash
#!/bin/bash
# quick-sweep.sh
ruff check src/ || eslint src/ --max-warnings 0
pytest -x -q
vitest run
mypy src/ --strict
tsc --noEmit
```

## Recipe 2: Full CI Pipeline
```yaml
# .github/workflows/test.yml
name: Test Suite
on: [push, pull_request]
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      # Python
      - uses: actions/setup-python@v5
        with: { python-version: '3.12' }
      - run: pip install -e ".[test]"
      - run: pytest --cov=src --cov-fail-under=80 -n 4

      # JS/TS
      - uses: actions/setup-node@v4
        with: { node-version: '20' }
      - run: npm ci
      - run: vitest run --coverage

      # E2E
      - run: npx playwright install --with-deps
      - run: npx playwright test

      # Security scan
      - run: semgrep --config=auto --error .
```

## Recipe 3: Bug-Fix Verification
1. Write a failing test that reproduces the exact bug.
2. Run it — confirm RED.
3. Fix the code minimally.
4. Run all tests — confirm GREEN.
5. Add a property test to prevent regression.

### ⚠️ Common Errors While Setting Up CI/CD
- **Running all tests sequentially without parallelization** — CI times balloon to 30+ minutes.
- **Not caching dependencies** between runs — every build downloads the internet.
- **Failing to fail the build on security scan findings** — a warning becomes invisible noise.
- **Running E2E tests before unit tests** — fast feedback is wasted.
- **Not uploading artifacts on failure** — debugging a CI-only failure is impossible without logs.

### 🧩 Complex Errors / Edge Cases
- **Secret leakage in CI logs:** Environment variables printed for debugging end up in persistent logs.
- **Pipeline duration increasing linearly:** Adding tests without parallelization or selective test running.
- **Test artifacts not uploaded on failure:** Playwright traces, coverage HTML, and core dumps are lost.
- **Matrix build combinatorial explosion:** Testing every OS × Node × Python version leads to 50+ jobs.

### 🎯 Expert Precision Tips
- Use **matrix builds** for multiple OS/language versions, but cap at  →  critical combinations.
- Upload **test reports, coverage HTML, and Playwright traces** as artifacts on every run.
- Gate merges on: **green CI + code review approval + security scan pass + branch coverage ≥ 70%**.
- Run the fastest tests (lint, unit) first. E2E should be the last gate.
- Use `pytest-xdist` (`-n auto`) and Vitest's built-in parallelism to speed up test suites.

---

# TASK 12 — Coverage & Quality Metrics
*Use coverage as a guardrail, not a goal.*

## Coverage Tools
| Language | Tool | Command |
|----------|------|---------|
| Python | pytest-cov | `pytest --cov=src --cov-fail-under=80` |
| JS/TS | Vitest/Jest | `vitest run --coverage` |
| Java | JaCoCo | Maven/Gradle plugin |
| C++ | gcov + lcov | `gcov file.o && lcov --capture` |

## Quality Heuristics
```
Line coverage ≥ 70%    → Minimum acceptable
Branch coverage ≥ 70%  → Better than line coverage alone
Mutation score ≥ 80%   → Strong test quality signal
Flaky test rate = 0%   → Non-negotiable
E2E coverage ≥ 90%     → Of critical user journeys, not all code
```

### ⚠️ Common Errors While Using Metrics
- **Optimizing for line coverage instead of branch coverage** — a function with one uncovered branch can still have 90% line coverage.
- **Excluding untestable files from coverage without justification** — this is gaming the metric.
- **Treating coverage as a goal** rather than a guardrail — 100% coverage with weak assertions is theater.
- **Ignoring uncovered lines in PRs** — technical debt accumulates one line at a time.

### 🧩 Complex Errors / Edge Cases
- **Inflated coverage from integration tests that don't assert behavior:** The code runs, but no test verifies the output.
- **Mutation score skewed by equivalent mutants:** A perfect score may hide untestable boilerplate.
- **Cyclomatic complexity hidden by high coverage:** A 50-line function with 15 branches is hard to maintain even with 100% coverage.
- **Coverage gaps in error handlers:** The happy path is covered, but 80% of production bugs live in error paths.

### 🎯 Expert Precision Tips
- **Branch coverage is the minimum meaningful metric.** Use `--cov-branch` (Python) or equivalent.
- Pair coverage with **mutation testing** for a real quality signal.
- Review **uncovered lines in every PR.** Don't let debt accumulate.
- If a line is "untestable," refactor it until it is testable or document why it is excluded.
- Focus coverage efforts on **business-critical paths**, not on auto-generated config or UI styling code.

---

**Remember:** 100% line coverage with weak assertions is theater. Aim for meaningful assertions on behavior.


---

## PART 5: FIX PATTERNS

# 03 — Fix Patterns: Master Fix Reference

> **Iron Law:** Fix root causes, not symptoms. Every fix MUST include a regression test.  
> **Sources:** [Superpowers](https://github.com/obra/superpowers) · [Microsoft Playbook](https://github.com/microsoft/code-with-engineering-playbook) · [Google Eng Practices](https://github.com/google/eng-practices) · [Professional Programming](https://github.com/charlax/professional-programming)

---

## 🎯 CONSTANT CORE — APPLY BEFORE EVERY FIX

```
STEP 0 — MANDATORY PRE-FIX CHECKLIST
□ Reproduce the bug at least once
□ Identify the exact root cause (not the symptom)
□ Select the matching fix-pattern section below
□ Write a failing regression test before changing production code
□ Ensure the fix is the smallest change that eliminates the root cause
```

```
STEP 0 — UNIVERSAL FIX CONTRACT
1. Eliminate the possibility (make the bug impossible by design) — BEST
2. Fail loudly (throw with a clear error if invalid state occurs)
3. Degrade gracefully (fallback to safe default with logging)
4. Guard at boundary (validate input at entry point)
Never: silently swallow, log-and-continue, or return undefined without explanation.
```

```
STEP 0 — MANDATORY ONLINE SEARCH TOOL
□ If the fix involves a framework, library, API, or version you are not 100% certain about, search SearXNG first for the most updated official notes and solutions.
□ SearXNG: https://github.com/searxng/searxng — free, open-source metasearch engine that aggregates 70+ search engines without tracking users or storing queries.
□ Do not guess based on stale knowledge. Verify with up-to-date sources before proceeding.
```

## 📑 TASK INDEX — Jump to your specific fix pattern

```
Task     Topic                                         When to Use
----------------------------------------------------------------------------------
TASK 1   Null Safety & Defensive Programming  →  TypeError, null dereference
TASK 2   Async & Promise Fixes  →  Missing await, unhandled rejections, race conditions
TASK 3   Type Safety Fixes  →  TS/mypy type errors
TASK 4   React-Specific Fixes  →  Hooks, closures, rendering bugs
TASK 5   State Management Fixes  →  Inconsistent or mutable shared state
TASK 6   Data Transformation Fixes  →  Mutation, precision, serialization
TASK 7   Security Fixes  →  Injection, XSS, secrets
TASK 8   Python-Specific Fixes  →  Mutable defaults, resource leaks
TASK 9   API & Backend Fixes  →  Rate limiting, CORS, env validation
TASK 10  Performance Fixes  →  N+1, inefficiency, leaks
TASK 11  Refactoring & Architecture Fixes  →  Large functions, coupling
TASK 12  Fix Verification Protocol  →  Post-fix checklist
```

---

# TASK 1 — Null Safety & Defensive Programming
*Fixes for TypeError, null dereference, and missing data handling.*

## Pattern 1.1: Defensive Access Chain
```typescript
// ❌ BROKEN: Crashes when any link in chain is null
const city = user.address.city.toUpperCase();

// ✅ FIX A: Optional chaining + nullish coalescing
const city = user?.address?.city?.toUpperCase() ?? 'UNKNOWN';

// ✅ FIX B: Guard clauses (when branching on missing data)
function getUserCity(user: User | null): string {
  if (!user) return 'No user';
  if (!user.address) return 'No address';
  if (!user.address.city) return 'No city';
  return user.address.city.toUpperCase();
}

// ✅ FIX C: Default objects at creation time (best for deep nesting)
interface User { address: { city: string; country: string }; }
function createUser(data: Partial<User>): User {
  return {
    address: {
      city: data.address?.city ?? '',
      country: data.address?.country ?? '',
    },
  };
}
```

## Pattern 1.2: Safe Array Access
```typescript
// ❌ BROKEN: Crashes when array is empty or index OOB
const first = items[0].id;

// ✅ FIX
const first = items.at(0); // returns undefined instead of crashing
const last = items.at(-1);  // negative index from end

// Helper for safe access:
function safeGet<T>(arr: T[], index: number): T | undefined {
  return index >= 0 && index < arr.length ? arr[index] : undefined;
}
```

## Pattern 1.3: Fail-Fast Validation
```typescript
// ✅ FIX: Validate at boundary and throw early
function processPayment(amount: number): Receipt {
  if (typeof amount !== 'number' || !Number.isFinite(amount) || amount <= 0) {
    throw new ValidationError('amount must be a positive finite number');
  }
  // ... core logic safe from invalid input
}
```

### ⚠️ Common Errors While Fixing Null Safety
- **Over-using `?.`** making code unreadable — more than 2 chained optional accesses is a sign of bad data modeling.
- **Using `??` where `||` is actually correct** — e.g., `count ?? 0` preserves `0`, but if `count` can be `NaN`, you still have a bug.
- **Returning empty strings to the UI** instead of explicit error states, causing silent downstream corruption.
- **Defensive coding that masks root cause** — if `user` is always supposed to exist, fixing the symptom with `user?.name` hides a data flow bug.

### 🧩 Complex Errors / Edge Cases
- **Deep null propagation:** Intermediate layer returns `null` instead of validating, forcing every consumer to handle it.
- **`null` vs `undefined` semantic drift:** APIs return `null`, JavaScript misses return `undefined`, and your checks handle only one.
- **`0`, `''`, `false` being swallowed by `||`:** `value || default` treats valid falsy values as missing.
- **Nested default objects missing deeper properties:** `{ ...defaults, ...input }` is shallow; nested objects merge by reference.

### 🎯 Expert Precision Tips
- **Default at boundary, not at every access.** Fix the data shape at creation or API parsing time.
- If you have more than 2 `?.` operators in one expression, **refactor the data model** or use a helper.
- Use `??` for null/undefined fallback, `||` for any falsy fallback. Know which one you need.
- Make impossible states unrepresentable: if `address` is required, don't type it as optional.

---

# TASK 2 — Async & Promise Fixes
*Fixes for missing await, unhandled rejections, and race conditions.*

## Pattern 2.1: Missing Await
```typescript
// ❌ BROKEN: Returns Promise instead of value
function getUserName(id: string) {
  const user = fetchUser(id); // missing await
  return user.name;           // undefined
}

// ✅ FIX: Always await async operations
async function getUserName(id: string): Promise<string> {
  const user = await fetchUser(id);
  return user.name;
}
```

## Pattern 2.2: Unhandled Promise Rejection
```typescript
// ❌ BROKEN: Silent failure — rejection is lost
async function loadDashboard() {
  fetchUserData().then(data => setUser(data));
  fetchMetrics().then(data => setMetrics(data));
}

// ✅ FIX A: Use Promise.allSettled for independent operations
async function loadDashboard() {
  const [userResult, metricsResult] = await Promise.allSettled([
    fetchUserData(), fetchMetrics(),
  ]);
  if (userResult.status === 'fulfilled') setUser(userResult.value);
  else logError('user load failed', userResult.reason);
}

// ✅ FIX B: Use Promise.all when ALL must succeed
async function loadDashboard() {
  try {
    const [user, metrics] = await Promise.all([fetchUserData(), fetchMetrics()]);
    setUser(user);
    setMetrics(metrics);
  } catch (error) {
    setError(error instanceof Error ? error : new Error(String(error)));
  }
}
```

## Pattern 2.3: Race Condition in State Updates
```typescript
// ❌ BROKEN: Stale data if fetchUser called twice quickly
useEffect(() => {
  fetchUser(userId).then(setUser); // no cleanup
}, [userId]);

// ✅ FIX: Cancellation flag pattern
useEffect(() => {
  let cancelled = false;
  fetchUser(userId).then((data) => {
    if (!cancelled) setUser(data);
  });
  return () => { cancelled = true; };
}, [userId]);

// ✅ FIX (Advanced): AbortController for true cancellation
useEffect(() => {
  const controller = new AbortController();
  fetchUser(userId, { signal: controller.signal })
    .then(setUser)
    .catch((err) => { if (err.name !== 'AbortError') throw err; });
  return () => controller.abort();
}, [userId]);
```

### ⚠️ Common Errors While Fixing Async Bugs
- **Adding `async` to a function that doesn't use `await`** — this wraps the return value in a Promise unnecessarily.
- **Swallowing errors in `.catch(() => {})`** — silent failures are worse than crashes.
- **Using `Promise.all` for dependent operations** — if B needs the result of A, sequential `await` is clearer.
- **Forgetting that `await` in a `forEach` loop doesn't wait** — use `for...of` with `await` instead.

### 🧩 Complex Errors / Edge Cases
- **Unhandled rejections in event emitters:** Event handlers that throw don't reject the emitter's Promise.
- **Mixing callback and Promise APIs without promisification:** Leads to callback-in-Promise hell and lost errors.
- **Zalgo in custom Promise-like objects:** A function that sometimes resolves sync and sometimes async.
- **AbortController edge cases:** Aborting a completed fetch throws an unhandled `AbortError` if `.catch()` is missing.

### 🎯 Expert Precision Tips
- Always return Promises from async functions (don't break the chain). If you don't need async, don't use `async`.
- For independent operations, use `allSettled` and map errors explicitly. This prevents one failure from hiding the others.
- Enable Node's `--unhandled-rejections=strict` and ESLint's `@typescript-eslint/no-floating-promises`.
- In React, assume every `useEffect` async operation can race. Use `AbortController` for fetch and a cancellation flag for callbacks.

---

# TASK 3 — Type Safety Fixes
*Fixes for TypeScript, mypy, and typed language errors.*

## Pattern 3.1: Remove All `any` Usage
```typescript
// ❌ BROKEN: `any` disables TypeScript
function processData(data: any) {
  return data.value.toUpperCase();
}

// ✅ FIX STEP 1: Use `unknown` — forces narrowing
function processData(data: unknown): string {
  if (typeof data !== 'object' || data === null) {
    throw new TypeError(`Expected object, got ${typeof data}`);
  }
  if (!('value' in data) || typeof (data as Record<string, unknown>).value !== 'string') {
    throw new TypeError(`Expected { value: string }`);
  }
  return (data as { value: string }).value.toUpperCase();
}

// ✅ FIX STEP 2 (Better): Define exact type
interface DataPayload { value: string; }
function processData(data: DataPayload): string {
  return data.value.toUpperCase();
}
```

## Pattern 3.2: Non-Exhaustive Type Narrowing
```typescript
// ❌ BROKEN: New union member not handled
function getStatusColor(status: Status): string {
  switch (status) {
    case 'pending': return 'yellow';
    case 'active': return 'green';
    case 'inactive': return 'gray';
    // 'banned' not handled!
  }
}

// ✅ FIX: Exhaustive switch with never check
function getStatusColor(status: Status): string {
  switch (status) {
    case 'pending': return 'yellow';
    case 'active': return 'green';
    case 'inactive': return 'gray';
    case 'banned': return 'red';
    default: {
      const exhaustiveCheck: never = status;
      throw new Error(`Unhandled status: ${exhaustiveCheck}`);
    }
  }
}
```

### ⚠️ Common Errors While Fixing Type Errors
- **Replacing `any` with `unknown` but then casting it right back** — this is theater, not safety.
- **Using `as` instead of narrowing** — you've bought a runtime crash for the price of compile-time silence.
- **Adding `| null` everywhere** instead of validating at boundaries — null propagation cancer.
- **Fixing the error at the call site** instead of the source type definition, causing the fix to be repeated everywhere.

### 🧩 Complex Errors / Edge Cases
- **Contravariance / covariance issues in generics:** A `List<Dog>` is not a `List<Animal>` in most type systems.
- **Conditional types that distribute unexpectedly:** `T extends U ? X : Y` behaves differently for union types.
- **`any` leaking from third-party libraries:** One `any` in a dependency type can poison inference across your codebase.
- **Type predicate functions that lie:** `isString(x)` returning `true` for numbers breaks downstream safety.

### 🎯 Expert Precision Tips
- Read TypeScript errors **bottom-up**: the last file is usually the symptom, the first file is the cause.
- When stuck on generics, remove them and test with concrete types first. Reintroduce abstraction only after it works.
- Use `satisfies` instead of `as` where possible — it checks compatibility without changing the inferred type.
- For runtime validation, use **Zod** or **valibot** instead of manual `typeof` chains.
- Use **branded types** for IDs: `type UserId = string & { __brand: 'UserId' }` prevents passing a `ProductId` where a `UserId` is expected.

---

# TASK 4 — React-Specific Fixes
*Fixes for hooks, closures, rendering, and component state.*

## Pattern 4.1: Stale Closure in useEffect
```typescript
// ❌ BROKEN: count captured at initial render
useEffect(() => {
  const timer = setInterval(() => {
    setCount(count + 1); // always 0 + 1
  }, 1000);
  return () => clearInterval(timer);
}, []);

// ✅ FIX A: Add count to deps
useEffect(() => {
  const timer = setInterval(() => setCount(count + 1), 1000);
  return () => clearInterval(timer);
}, [count]);

// ✅ FIX B: Functional update
useEffect(() => {
  const timer = setInterval(() => setCount(prev => prev + 1), 1000);
  return () => clearInterval(timer);
}, []);
```

## Pattern 4.2: Object/Array Identity Causing Infinite Loop
```typescript
// ❌ BROKEN: New object every render
const options = { pageSize: 10, filters };
useEffect(() => { fetchData(options); }, [options]); // infinite loop

// ✅ FIX A: useMemo
const options = useMemo(() => ({ pageSize: 10, filters }), [filters]);
useEffect(() => { fetchData(options); }, [options]);

// ✅ FIX B: Primitive deps
const { search, category } = filters;
useEffect(() => {
  fetchData({ pageSize: 10, filters: { search, category } });
}, [search, category]);
```

## Pattern 4.3: Key Prop Bugs in Lists
```typescript
// ❌ BROKEN: Index as key causes wrong reuse on reorder/delete
{todos.map((todo, index) => <TodoItem key={index} todo={todo} />)}

// ✅ FIX: Stable unique IDs
{todos.map((todo) => <TodoItem key={todo.id} todo={todo} />)}

// When stable IDs don't exist, generate once at data creation
const [todos, setTodos] = useState(
  rawTodos.map(t => ({ ...t, id: crypto.randomUUID() }))
);
```

### ⚠️ Common Errors While Fixing React Bugs
- **Fixing stale closure by adding deps without understanding why** — this can cause infinite re-renders or missed cleanups.
- **Using `useMemo` for everything** — memoization has overhead. Don't use it for trivial calculations.
- **Putting `useEffect` in loops or conditions** — this violates the Rules of Hooks and causes crashes.
- **Using `useCallback` without memoized children** — the callback is stable, but the child re-renders anyway because it isn't memoized.

### 🧩 Complex Errors / Edge Cases
- **Custom hooks with hidden dependencies:** A hook uses `useEffect` internally but doesn't expose cleanup to the caller.
- **Context value object identity causing mass re-render:** A new object passed to `Provider` re-renders every consumer.
- **Refs not triggering re-renders:** Updating `ref.current` doesn't cause a re-render, so UI stays stale.
- **Server Component accidentally importing client-only hooks:** Causes a build-time or runtime error in Next.js/App Router.

### 🎯 Expert Precision Tips
- If you need `useEffect`, first ask: **"Can this be an event handler instead?"**
- Derive state from props when possible. Don't sync props to state with `useEffect` unless absolutely necessary.
- For object deps, **destructure to primitives** or use `useMemo` with a stable comparator.
- If `useEffect` has more than 3 dependencies, the effect is probably doing too much — split it.
- Use `eslint-plugin-react-hooks` with the exhaustive-deps rule enabled. Treat every warning as an error.

---

# TASK 5 — State Management Fixes
*Fixes for inconsistent state, shared mutable state, and state ownership.*

## Pattern 5.1: Inconsistent State (Discriminated Union)
```typescript
// ❌ BROKEN: Multiple booleans can be simultaneously true
type State = { isLoading: boolean; data: User | null; error: Error | null };
// Bug: isLoading=true AND error set at same time is possible

// ✅ FIX: Use discriminated union
type FetchState<T> =
  | { status: 'idle' }
  | { status: 'loading' }
  | { status: 'success'; data: T }
  | { status: 'error'; error: Error };

// TypeScript enforces only one state at a time
if (state.status === 'success') return <UserCard user={state.data} />;
```

## Pattern 5.2: Shared Mutable State
```typescript
// ❌ BROKEN: Mutates shared object
const defaultOptions = { headers: {} };
function makeRequest(url, options = defaultOptions) {
  options.headers.auth = getToken(); // Mutates shared object!
}

// ✅ FIX: Copy on entry
function makeRequest(url: string, overrides: Partial<Options> = {}) {
  const options: Options = {
    ...overrides,
    headers: { ...overrides.headers, auth: getToken() },
  };
  return fetch(url, options);
}
```

### ⚠️ Common Errors While Fixing State Bugs
- **Replacing booleans with discriminated union but leaving old booleans in place** — now you have two sources of truth.
- **Over-normalizing state** making reads complex and error-prone.
- **Mutating state in Redux reducers** — `state.items.push(item)` violates Redux immutability.
- **Using global state for component-local concerns** — every re-render triggers unnecessary updates elsewhere.

### 🧩 Complex Errors / Edge Cases
- **Normalized state with circular references:** JSON serialization fails, and selectors become infinitely recursive.
- **Selector memoization breaking due to object identity:** A new object reference causes all derived state to recalculate.
- **Optimistic UI rollback logic:** The failure path doesn't correctly restore the previous state because it was mutated.
- **Micro-states in forms:** Each input has its own `useState`, making cross-field validation impossible.

### 🎯 Expert Precision Tips
- Keep state **minimal**. Derive everything you can from the minimal state needed.
- If two pieces of state are **always updated together**, they belong together in a single object.
- Use **Immer** for complex immutable updates — it prevents accidental mutations.
- For global state, prefer atomic stores (Zustand, Jotai, Recoil) over monolithic stores for better performance and modularity.
- State machines (XState) are often the right fix for boolean flag soup.

---

# TASK 6 — Data Transformation Fixes
*Fixes for mutation, precision errors, and serialization bugs.*

## Pattern 6.1: In-Place Mutation
```typescript
// ❌ BROKEN: Mutates original array
function sortByName(users: User[]): User[] {
  return users.sort((a, b) => a.name.localeCompare(b.name));
}

// ✅ FIX: Copy before mutating
function sortByName(users: User[]): User[] {
  return [...users].sort((a, b) => a.name.localeCompare(b.name));
  // OR: return users.toSorted((a, b) => a.name.localeCompare(b.name)); // ES2023
}
```

## Pattern 6.2: Float Precision in Money/Finance
```typescript
// ❌ BROKEN: Floating point imprecision
const total = 0.1 + 0.2; // 0.30000000000000004

// ✅ FIX: Work in integer cents
class Money {
  private readonly cents: number;
  constructor(cents: number) {
    if (!Number.isInteger(cents)) throw new TypeError('Money must be integer cents');
    this.cents = cents;
  }
  static fromDollars(dollars: number): Money {
    return new Money(Math.round(dollars * 100));
  }
  add(other: Money): Money {
    return new Money(this.cents + other.cents);
  }
  format(): string {
    return `$${(this.cents / 100).toFixed(2)}`;
  }
}
```

### ⚠️ Common Errors While Fixing Data Transformation Bugs
- **Using `JSON.parse(JSON.stringify(obj))` as a deep copy** — loses `Date`, `undefined`, functions, and circular refs.
- **Using `sort()` on numbers without comparator** — `[10, 2].sort()` gives `[10, 2]` (lexicographic).
- **Spreading nested objects shallowly** — `{ ...obj, nested: { ...obj.nested, x: 1 } }` is verbose and error-prone.
- **Modifying function parameters** — callers are surprised when their data changes.

### 🧩 Complex Errors / Edge Cases
- **Timezone-aware date serialization:** `toISOString()` drops timezone info; `toJSON()` may use local time unexpectedly.
- **BigInt JSON limitations:** `JSON.stringify(123n)` throws in many environments.
- **Prototype pollution during object merges:** `Object.assign({}, userInput)` can be unsafe if keys include `__proto__`.
- **Float precision in comparisons:** `0.1 + 0.2 === 0.3` is false. Use epsilon comparisons or integer math.

### 🎯 Expert Precision Tips
- Use `structuredClone` for deep copies (where supported) instead of JSON hackery.
- For money, **never use `number`** — use integer cents or a Money library (Dinero.js, currency.js).
- Always return a **new value** from transformation functions. If you must mutate for performance, document it loudly.
- For date transformations, use a robust library (date-fns, Luxon) and store/transmit in UTC ISO-8601.
- When merging objects from untrusted sources, sanitize keys to prevent prototype pollution.

---

# TASK 7 — Security Fixes
*Fixes for injection, XSS, secrets exposure, and auth vulnerabilities.*

## Pattern 7.1: SQL Injection
```typescript
// ❌ CRITICAL: SQL injection
async function getUserByName(name: string) {
  const query = `SELECT * FROM users WHERE name = '${name}'`;
  return db.query(query);
}

// ✅ FIX: Parameterized queries — ALWAYS
async function getUserByName(name: string): Promise<User | null> {
  const result = await db.query<User>(
    'SELECT id, name, email FROM users WHERE name = $1 LIMIT 1',
    [name]
  );
  return result.rows[0] ?? null;
}
```

## Pattern 7.2: XSS (Cross-Site Scripting)
```typescript
// ❌ CRITICAL: Injects raw HTML
container.innerHTML = bio;

// ✅ FIX A: Use textContent for plain text
container.textContent = bio;

// ✅ FIX B: Sanitize if HTML is required
import DOMPurify from 'dompurify';
container.innerHTML = DOMPurify.sanitize(bio, {
  ALLOWED_TAGS: ['b', 'i', 'em', 'strong', 'a'],
  ALLOWED_ATTR: ['href'],
});
```

## Pattern 7.3: Secrets Exposure
```typescript
// ❌ CRITICAL: Hardcoded secret
const API_KEY = 'sk-live-abc123def456';

// ✅ FIX: Environment variables + validation + never log
const config = {
  apiKey: process.env.API_KEY,
} as const;
if (!config.apiKey) throw new Error('API_KEY required');

// Never log secrets
logger.info('API call', { apiKeyPrefix: config.apiKey.slice(0, 4) + '***' });
```

### ⚠️ Common Errors While Applying Security Fixes
- **Parameterizing the main query but not `ORDER BY` clauses** — column names in `ORDER BY` can't be parameterized in most DBs. Use an allowlist.
- **Trusting `DOMPurify` without updating it** — new XSS vectors are discovered regularly.
- **Storing secrets in `.env.example`** or test fixtures that get committed.
- **Using a denylist for input validation** — attackers will find an input you didn't think of.

### 🧩 Complex Errors / Edge Cases
- **SQL injection via `LIKE` wildcards:** Even with parameterized queries, `%` and `_` in user input can cause unexpected matches.
- **DOM clobbering bypassing sanitizers:** Malicious HTML can overwrite global variables via named elements.
- **JWT `none` algorithm bypass:** A token with `alg: "none"` is accepted by poorly implemented libraries.
- **SSRF via allowlisted hostnames:** Subdomain takeovers or DNS rebinding bypass hostname checks.

### 🎯 Expert Precision Tips
- Use an **allowlist, never a denylist**, for both input validation and HTML sanitization.
- Rotate secrets automatically where possible (e.g., AWS IAM rotation, HashiCorp Vault).
- Use a prepared statement for every query, even "simple" ones.
- For dynamic `ORDER BY`, map user input to a hardcoded allowlist of column names.
- Review **dependency changelogs** for CVE fixes monthly. Outdated libraries are the #1 attack vector.

---

# TASK 8 — Python-Specific Fixes
*Fixes for mutable defaults, resource leaks, and typing issues.*

## Pattern 8.1: Mutable Default Arguments
```python
# ❌ BROKEN: Default list created ONCE at definition
def add_item(item: str, items: list = []) -> list:
    items.append(item)
    return items

# ✅ FIX: Use None sentinel
def add_item(item: str, items: list[str] | None = None) -> list[str]:
    if items is None:
        items = []
    items.append(item)
    return items
```

## Pattern 8.2: Resource Leaks
```python
# ❌ BROKEN: File never closed if exception occurs
def read_file(path: str) -> str:
    f = open(path)
    data = f.read()
    f.close()
    return data

# ✅ FIX: Context manager guarantees cleanup
from pathlib import Path

def read_file(path: Path) -> str:
    with path.open(encoding='utf-8') as f:
        return f.read()
```

### ⚠️ Common Errors While Fixing Python Code
- **Fixing mutable default by creating `[]` inside the function body on every call** — safe but slightly less efficient than reusing a passed list.
- **Catching `Exception` and losing stack traces** — use `logger.exception()` to preserve traceback.
- **Using `is` for value equality** — `x is 0` works by accident (interning) but is semantically wrong.
- **Not handling encoding explicitly** — defaults to system encoding, causing cross-platform bugs.

### 🧩 Complex Errors / Edge Cases
- **`asyncio` task exceptions swallowed until awaited:** Un awaited tasks don't surface errors until garbage collection.
- **Mutable class variables shared across instances:** `class Foo: items = []` creates one list shared by all instances.
- **Implicit string concatenation in tuples:** `("a", "b" "c")` becomes `("a", "bc")` — valid syntax, wrong semantics.
- **Monkey-patching standard library:** Breaks invariants for all downstream code.

### 🎯 Expert Precision Tips
- Use `dataclasses` or **Pydantic** for data shapes to eliminate manual validation and type ambiguity.
- Always log exceptions with `logger.exception("msg")` inside an `except` block — it captures the full stack trace.
- Prefer `pathlib.Path` over `os.path` for all file system operations.
- Use `datetime.timezone.utc` or `zoneinfo` — never use naive datetimes for anything that crosses a system boundary.
- For type hints, enable `mypy --strict` in CI. It's the fastest way to catch real bugs in Python.

---

# TASK 9 — API & Backend Fixes
*Fixes for rate limiting, input validation, CORS, and environment config.*

## Pattern 9.1: Rate Limiting
```typescript
// ❌ BROKEN: No rate limiting
app.post('/api/login', async (req, res) => { ... });

// ✅ FIX: Sliding window rate limit
import rateLimit from 'express-rate-limit';
const loginLimiter = rateLimit({
  windowMs: 15 * 60 * 1000,
  max: 5,
  keyGenerator: (req) => req.ip + ':' + req.body.email,
});
app.post('/api/login', loginLimiter, async (req, res) => { ... });
```

## Pattern 9.2: CORS Configuration
```typescript
// ❌ BROKEN: Wildcard in production
app.use(cors({ origin: '*' }));

// ✅ FIX: Whitelist origins
const ALLOWED_ORIGINS = [
  'https://myapp.com',
  ...(process.env.NODE_ENV === 'development' ? ['http://localhost:3000'] : []),
];
app.use(cors({
  origin: (origin, callback) => {
    if (!origin || ALLOWED_ORIGINS.includes(origin)) callback(null, true);
    else callback(new Error(`CORS: Origin ${origin} not allowed`));
  },
  credentials: true,
  methods: ['GET', 'POST', 'PUT', 'DELETE', 'PATCH'],
  allowedHeaders: ['Content-Type', 'Authorization'],
  maxAge: 86400,
}));
```

## Pattern 9.3: Environment Variable Validation
```typescript
// ❌ BROKEN: App crashes later when env var missing
const apiKey = process.env.API_KEY;

// ✅ FIX: Validate at startup — fail fast
import { z } from 'zod';
const EnvSchema = z.object({
  NODE_ENV: z.enum(['development', 'production', 'test']),
  PORT: z.string().transform(Number).pipe(z.number().positive()),
  DATABASE_URL: z.string().url(),
  API_KEY: z.string().min(10),
  JWT_SECRET: z.string().min(32),
});
function validateEnv() {
  const result = EnvSchema.safeParse(process.env);
  if (!result.success) {
    console.error('❌ Environment validation failed:');
    for (const issue of result.error.issues) {
      console.error(`  ${issue.path.join('.')}: ${issue.message}`);
    }
    process.exit(1);
  }
  return result.data;
}
export const env = validateEnv();
```

### ⚠️ Common Errors While Fixing API/Backend Issues
- **Rate limiting by IP only** — ignores NAT/shared office IPs, blocking legitimate users.
- **Allowing `localhost` in CORS whitelist in production** — any attacker running a local server can hit your API.
- **Validating env vars but not providing sensible defaults** for optional configuration.
- **Returning stack traces in production error responses** — leaks implementation details.

### 🧩 Complex Errors / Edge Cases
- **CORS preflight cache causing auth header issues:** Browsers cache preflight responses; changing allowed headers requires cache busting.
- **Rate limiter state not shared across server instances:** In-memory rate limiting is useless behind a load balancer. Use Redis.
- **OpenAPI schema drift from implementation:** The docs say one thing, the code does another.
- **Request payload size causing DoS:** No `body-parser` limit allows multi-gigabyte uploads to crash the server.

### 🎯 Expert Precision Tips
- Use a **schema-first approach** (OpenAPI / Zod) for all API inputs. The schema is the contract.
- CORS is **not a substitute for authentication**. It only controls which websites can make requests.
- Use Redis-backed rate limiting in production. In-memory rate limiting fails at scale.
- Set explicit body size limits (`express.json({ limit: '10kb' })`) to prevent memory exhaustion.
- Never return raw error objects to clients in production. Log details server-side, send generic messages client-side.

---

# TASK 10 — Performance Fixes
*Fixes for N+1 queries, inefficient algorithms, and memory leaks.*

## Pattern 10.1: N+1 Query Elimination
```typescript
// ❌ BROKEN: O(n) queries
const users = await db.users.findMany();
for (const user of users) {
  user.orders = await db.orders.findMany({ where: { userId: user.id } });
}

// ✅ FIX: Single query with join/include
const users = await db.users.findMany({
  include: { orders: true },
});
```

## Pattern 10.2: Debouncing User Input
```typescript
// ❌ BROKEN: Fires API call on every keystroke
useEffect(() => {
  if (query) searchApi(query).then(setResults);
}, [query]);

// ✅ FIX: Debounce before API call
const debouncedQuery = useDebouncedValue(query, 300);
useEffect(() => {
  if (!debouncedQuery) { setResults([]); return; }
  const controller = new AbortController();
  searchApi(debouncedQuery, { signal: controller.signal })
    .then(setResults)
    .catch(err => { if (err.name !== 'AbortError') console.error(err); });
  return () => controller.abort();
}, [debouncedQuery]);
```

## Pattern 10.3: Unbounded Cache Protection
```typescript
// ❌ BROKEN: Cache grows forever
const cache = new Map();
function getData(key) {
  if (!cache.has(key)) cache.set(key, fetchData(key));
  return cache.get(key);
}

// ✅ FIX: LRU cache with max size
import LRU from 'lru-cache';
const cache = new LRU({ max: 1000, ttl: 1000 * 60 * 5 });
```

## Pattern 10.4: Responsive Image Optimization
```html
<!-- GOOD: Hero / LCP image -- art direction + resolution switching -->
<picture>
  <source
    media="(max-width: 767px)"
    srcset="/hero-mobile-400.avif 400w, /hero-mobile-800.avif 800w"
    sizes="100vw"
    type="image/avif"
  />
  <source
    srcset="/hero-800.avif 800w, /hero-1200.avif 1200w, /hero-1600.avif 1600w"
    sizes="(max-width: 1200px) 100vw, 1200px"
    type="image/avif"
  />
  <img
    src="/hero-desktop.jpg"
    width="1200"
    height="600"
    fetchpriority="high"
    alt="Hero image description"
  />
</picture>

<!-- GOOD: Below-the-fold image -- lazy loaded -->
<img
  src="/content.webp"
  width="800"
  height="400"
  loading="lazy"
  decoding="async"
  alt="Content image description"
/>
```

### ⚠️ Common Errors While Applying Performance Fixes
- **Prematurely adding Redis caching** instead of fixing the underlying query or algorithm.
- **Debouncing at the wrong layer** — debouncing in the API instead of the UI wastes server resources.
- **Using `memo` on components that render rarely** — the memoization overhead exceeds the benefit.
- **Fixing a symptom (adding RAM) instead of the leak** — the leak will eventually return.

### 🧩 Complex Errors / Edge Cases
- **Cache stampede on hot keys:** Thousands of requests hit the cache simultaneously after expiry.
- **Thundering herd after cache expiry:** All requests miss the cache and hit the database at once.
- **N+1 hidden in GraphQL resolvers:** ORM lazy loading inside field resolvers is invisible in the parent query.
- **Memory fragmentation in long-running Node processes:** RSS grows while heap stays flat.

### 🎯 Expert Precision Tips
- **Measure first.** A missing database index is almost always cheaper to fix than adding a cache layer.
- Profile **production-like data volumes**, not local databases with 10 rows.
- Use **batch loading** (DataLoader pattern) for GraphQL/N+1 elimination.
- For caching, implement **cache warming** or **stale-while-revalidate** to avoid cold-start stampedes.
- If you can't explain why an optimization makes the code faster with numbers, don't commit it.

---

# TASK 11 — Refactoring & Architecture Fixes
*Fixes for large functions, tight coupling, and poor error handling architecture.*

## Pattern 11.1: Extract Function
```typescript
// ❌ BROKEN: Function does 5 things, 80 lines
function processOrder(order) { /* 80 lines */ }

// ✅ FIX: Extract helpers, keep function < 40 lines
function processOrder(order: Order): Receipt {
  validateOrder(order);
  const total = calculateTotal(order.items, order.discountCode);
  const payment = chargePayment(order.customer, total);
  return createReceipt(order, payment);
}
```

## Pattern 11.2: Result Type Pattern (Error Architecture)
```typescript
// Instead of throwing deep in the call stack, return typed results
type Result<T, E extends Error = Error> =
  | { ok: true; value: T }
  | { ok: false; error: E };

async function createUser(input: CreateUserInput): Promise<Result<User, ValidationError>> {
  const validation = validateInput(input);
  if (!validation.ok) return { ok: false, error: validation.error };
  const user = await userRepo.create(input);
  return { ok: true, value: user };
}
```

### ⚠️ Common Errors While Refactoring
- **Extracting functions but keeping them in the same giant file** — the file is still a god file.
- **Introducing interfaces "just in case"** — premature abstraction complicates the codebase.
- **Refactoring without characterization tests** — you have no safety net if behavior changes.
- **Changing multiple things at once** — refactoring + bug fixing + feature addition in one PR.

### 🧩 Complex Errors / Edge Cases
- **Breaking binary compatibility in libraries:** Changing a public function signature breaks downstream consumers.
- **Changing error types that callers depend on:** Callers catching `OldError` now miss the new exception.
- **Tight coupling to framework-specific types in domain logic:** Business rules depend on Express `Request` objects.
- **Refactoring performance-critical paths:** Extracting functions can prevent inlining and degrade performance.

### 🎯 Expert Precision Tips
- Refactor in **tiny steps**, running tests after each. If the change is >20 lines, split it.
- Before refactoring, write **characterization tests** that lock in current behavior.
- Move framework code to the edges. Domain logic should be pure and framework-agnostic.
- If a refactor requires updating more than 3 call sites, reconsider the abstraction.
- Use the **boy scout rule:** leave code cleaner than you found it, but don't rewrite the whole campsite.

---

# TASK 12 — Fix Verification Protocol
*Run this checklist after EVERY fix.*

```
□ Fix addresses root cause, not symptom
□ Fix is minimal (smallest change that eliminates the root cause)
□ Test written that FAILS on old code, PASSES on new code
□ Existing tests still pass (full suite, not just the new test)
□ No new bugs introduced in adjacent code
□ No new TypeScript / static analysis errors introduced
□ No new linter warnings
□ Performance not degraded (measure if relevant)
□ No new security vulnerabilities introduced
□ Edge cases handled (null, empty, boundary, max size)
□ Error messages are clear and actionable
□ Code reviewed by a second pair of eyes if complex or security-critical
□ Root cause documented in code comment or commit message
□ Documentation updated if behavior changed
```

### ⚠️ Common Errors During Fix Verification
- **Running only the new test** and not the full suite — you broke a distant test.
- **Forgetting to check lint/type after fix** — a "simple" fix introduces a type error in a sibling file.
- **Documenting the root cause in a place no one will read** — commit messages are better than ephemeral comments.
- **Assuming the fix works for symmetric cases** — e.g., fixing `x > 0` but forgetting `x < 0`.

### 🧩 Complex Errors / Edge Cases
- **Fix works for the reported case but not for symmetric cases:** E.g., handling ascending sort but not descending.
- **Performance regression only visible under load:** A fix that adds a query or allocation may pass unit tests but fail load tests.
- **Security regression:** Adding a helper function that bypasses an existing auth check.
- **Behavioral change that external systems depend on:** Fixing a "bug" that clients were relying on as a feature.

### 🎯 Expert Precision Tips
- **Before declaring done, run the regression test on the OLD code** to confirm it fails. If it passes, your test isn't testing the bug.
- Run the **full test suite**, not just the modified module. Type systems and global state can surprise you.
- If performance matters, run a **before/after benchmark** with realistic data.
- Update the commit message with the root cause. Future you (or a colleague during `git blame`) will thank you.
- For security fixes, explicitly verify that the attack vector from the bug report is blocked.


---

## PART 6: CODE QUALITY & ARCHITECTURE

# 04 — Code Quality, Review & Architecture

> **Core tenet:** Readable code enables sustained velocity — no shortcuts that create tech debt.  
> **Sources:** [Google Eng Practices](https://github.com/google/eng-practices) · [Microsoft Playbook](https://github.com/microsoft/code-with-engineering-playbook) · [Professional Programming](https://github.com/charlax/professional-programming) · [Context Engineering](https://github.com/coleam00/context-engineering-intro)

---

## 1. Code Review Criteria

*Merged from [Google's reviewer guide](https://google.github.io/eng-practices/review/reviewer/) and Microsoft fundamentals.*

### The 5 Pillars

| Pillar | Question | Quick Checks |
|--------|----------|--------------|
| **Design** | Does the change make sense architecturally? | Belongs here? Integrates well? No speculative generality? |
| **Functionality** | Does it do what it claims? | Edge cases handled? Concurrency safe? UI changes sensible? |
| **Complexity** | Can it be understood quickly? | Function ≤ 40 lines preferred; file ≤ 300 lines preferred |
| **Tests** | Are tests present, correct, useful? | Fail when code breaks? Property tests for pure functions? |
| **Naming / Comments** | Are names clear? | Explain **why**, not **what** |

### Microsoft Engineering Fundamentals Overlay
- **Source Control:** PRs used, commits explain *what* and *why*, no secrets in history.
- **CI/CD:** Automated build/test on every PR; main branch shippable.
- **Security:** Separation of concerns; inputs validated; no injection risks.
- **Observability:** Errors logged; health monitored; tracing propagated.
- **DevEx:** New developer can build, test, and run in < 5 minutes.

### LGTM Standard
> *"In general, reviewers should favor approving a CL once it is in a state where it definitely improves the overall code health of the system, even if the CL isn't perfect."* — [Google Standard of Code Review](https://google.github.io/eng-practices/review/reviewer/standard.html)

- **Approve** when the change improves maintainability and readability.
- **Do not delay** for minor polish if the direction is correct.
- **Do not approve** if code health degrades or validation gates are skipped.
- Label feedback explicitly: `Required:`, `Nit:`, `Optional:`, `FYI:`.

---

## 2. Review Workflows

### 2.1 Senior Engineer Code Review Prompt
```
Review this code as a senior engineer. Be brutally honest.

For each issue found, output:
- Severity: Blocker / Major / Minor / Nit
- Location: file:line or function name
- Problem: what's wrong and why it matters
- Fix: specific change needed

End with: "Approve / Approve with changes / Request changes" and reasoning.
```

### 2.2 The 3-Option Fix Protocol
*Best for: Choosing the right fix approach*

| Option | When | Characteristics |
|--------|------|-----------------|
| **1 — Surgical Patch** | Production down, need fix NOW | Smallest change, known debt introduced |
| **2 — Clean Fix** | Normal bug fix, time available | Right way within current architecture |
| **3 — Ideal Solution** | Major refactor or debt sprint | Best practice, may touch surrounding code |

**For every option provide:** complete code, side effects, regression risk, verification steps, rollback plan.

### 2.3 Mass Issue Fix Protocol
*Best for: Multiple issues in one codebase*

1. **Triage:** ID, Category, Severity (P0–P3), Interdependency, Complexity (S/M/L/XL).
2. **Fix Order:** P0/P1 first; group related fixes; identify mutually exclusive changes.
3. **Apply Sequentially:** BEFORE/AFTER diff, mechanism explanation, checkpoint test.
4. **Final Verification:** List every touched code path and the test to confirm it.

---

## 3. Architecture & Design

### 3.1 Architecture Rating (1–10 Scale)
Rate on 5 dimensions with specific reasoning:

| Dimension |  →  (Critical) |  →  (Problematic) |  →  (Acceptable) |  →  (Excellent) |
|-----------|----------------|-------------------|------------------|------------------|
| **Scalability** | Collapses at 2× load | Struggles at 5× | Handles 10× with tuning | Handles 100× gracefully |
| **Maintainability** | Incomprehensible in a day | Needs significant onboarding | New dev productive in a week | Self-documenting structure |
| **Testability** | Untestable without prod | Heavy mocking required | Clean boundaries | Pure functions, DI everywhere |
| **Security** | No validation anywhere | Weak boundaries | Validation at boundaries | Defense in depth |
| **Extensibility** | Every change breaks 5 things | Refactor required for features | New features fit naturally | Plugin architecture |

### 3.2 Common Architecture Patterns

| Pattern | Use When | Example |
|---------|----------|---------|
| **Repository** | Data access abstraction | `UserRepository.findById()` |
| **Strategy** | Multiple algorithms for same task | Payment: Stripe / PayPal / Crypto |
| **Factory** | Complex object setup | `createUser(type)` returns Admin/Viewer |
| **Result Type** | Functions that can fail | `Result<User, NotFoundError>` |
| **Adapter** | Converting between interfaces | `ApiUserToUser` transformer |

### 3.3 The Result Pattern (Most Useful for AI-Generated Code)
```typescript
type Result<T, E extends Error = Error> =
  | { ok: true; value: T }
  | { ok: false; error: E };

// Eliminates try/catch spaghetti; forces explicit handling
```

---

## 4. Refactoring Guidelines

### When to Refactor
- After green tests (Refactor phase of TDD)
- Before adding a feature that fights the current structure
- When complexity metrics exceed thresholds (Lizard > 15)

### Safe Refactoring Rules
1. **Add characterization tests first** — prove current behavior.
2. **One transformation per step.**
3. **Run tests after every change.**
4. **Verify behavior is unchanged.**

### Refactoring Targets by Goal
| Goal | Focus |
|------|-------|
| **Performance** | Algorithm complexity, caching, lazy loading |
| **Readability** | Naming, function size, comments |
| **Maintainability** | Coupling, cohesion, single responsibility |
| **Testability** | Dependency injection, pure functions |

---

## 5. Code Quality Checklist

### Pre-Commit (Self-Review)
- [ ] All tests pass (unit, integration, property)
- [ ] Output pristine (no lint/type/test warnings)
- [ ] Semgrep / static analysis clean
- [ ] No secrets in code or history
- [ ] Documentation updated if behavior changed
- [ ] Adjacent code still compiles and passes

### During Coding
- [ ] Functions focused (≤ 40 lines preferred)
- [ ] Files not "god files" (≤ 300 lines preferred)
- [ ] Explicit types and error handling
- [ ] No magic numbers (named constants)
- [ ] No shared mutable state without sync
- [ ] Comments explain **why**, not **what**

### PR Review
- [ ] Design is sound and well-integrated
- [ ] Functionality handles edge cases and failures
- [ ] Complexity is minimal
- [ ] Tests are present and would catch real bugs
- [ ] Naming and comments are clear
- [ ] CI passes, security checks pass

---

## 6. Advanced Review Practices

### Multi-Model Review Pattern
Use different models for different review perspectives:
```
Model A writes the code
    |
    V
Model B reviews for correctness and architecture
    |
    V
Model A addresses the feedback
    |
    V
Human makes the final call
```

### Dead Code Hygiene
After any refactoring or implementation change, check for orphaned code:
1. Identify code that is now unreachable or unused
2. List it explicitly
3. Ask before deleting: "Should I remove these now-unused elements: [list]?"

```markdown
DEAD CODE IDENTIFIED:
- formatLegacyDate() in src/utils/date.ts — replaced by formatDate()
- OldTaskCard component in src/components/ — replaced by TaskCard
→ Safe to remove these?
```

### Review Speed
Slow reviews block entire teams. The cost of context-switching to review is less than the waiting cost imposed on others.
- Respond within one business day — this is the maximum, not the target
- A typical change should complete multiple review rounds in a single day
- Large changes: Ask the author to split them rather than reviewing one massive changeset

### Handling Disagreements
When resolving review disputes, apply this hierarchy:
1. Technical facts and data override opinions and preferences
2. Style guides are the absolute authority on style matters
3. Software design must be evaluated on engineering principles, not personal preference
4. Codebase consistency is acceptable if it does not degrade overall health

Do not accept "I'll clean it up later." Experience shows deferred cleanup rarely happens. Require cleanup before submission unless it is a genuine emergency.

### Dependency Discipline
Before adding any dependency:
1. Does the existing stack solve this? (Often it does.)
2. How large is the dependency? (Check bundle impact.)
3. Is it actively maintained?
4. Does it have known vulnerabilities? (npm audit)
5. What is the license?

Rule: Prefer standard library and existing utilities over new dependencies. Every dependency is a liability.

### Honesty in Review
When reviewing code written by you, another agent, or a human:
- Do not rubber-stamp. LGTM without evidence of review helps no one.
- Do not soften real issues.
- Quantify problems when possible.
- Push back on approaches with clear problems.


---

## 6. Security Review Protocol

For any code handling user data or auth:

### Three-Tier Boundary System

**Always Do (No Exceptions):**
- Validate all external input at system boundaries
- Parameterize all database queries -- never concatenate user input into SQL
- Encode output to prevent XSS
- Use HTTPS for all external communication
- Hash passwords with bcrypt/scrypt/argon2
- Set security headers (CSP, HSTS, X-Frame-Options)
- Use httpOnly, secure, sameSite cookies for sessions
- Run npm audit before every release

**Ask First (Requires Human Approval):**
- Adding new authentication flows or changing auth logic
- Storing new categories of sensitive data
- Adding new external service integrations
- Changing CORS configuration
- Adding file upload handlers
- Modifying rate limiting or throttling

**Never Do:**
- Never commit secrets to version control
- Never log sensitive data (passwords, tokens, PII)
- Never trust client-side validation as a security boundary
- Never disable security headers for convenience
- Never use eval() or innerHTML with user-provided data
- Never expose stack traces or internal error details to users

### Input Validation
- [ ] All inputs validated before use
- [ ] Type checking enforced
- [ ] Length limits applied
- [ ] Special characters escaped/sanitized

### Authentication
- [ ] Passwords hashed (bcrypt/Argon2)
- [ ] JWT tokens have expiration
- [ ] Session management is secure
- [ ] Brute force protection exists

### Authorization
- [ ] Resource access verified per request
- [ ] Role checks implemented
- [ ] No IDOR vulnerabilities
- [ ] Admin actions restricted

### Data Protection
- [ ] Sensitive data encrypted at rest
- [ ] HTTPS enforced
- [ ] No secrets in code/logs
- [ ] PII handling compliant


---

## PART 7: ADVANCED BUGS

# Module 05 — Advanced Bugs: Async, Concurrency, Memory & Performance

## 🎯 Purpose

Patterns for the hardest category of bugs — those that are intermittent, environment-specific, or only appear under load or over time.

> **VIP EXPERT NOTE — The Heisenbug Principle:**
> The hardest bugs change behavior when you try to observe them. Adding
> console.log changes timing, fixing the environment removes the trigger.
> For these bugs: **instrument first, hypothesize second, change code last.**
> Log with timestamps plus correlation IDs before touching any logic.

---

## 🔷 ADVANCED-01: Race Conditions

### What is a Race Condition?

Two or more operations run concurrently, and the final result depends on which operation completes first. The result is correct sometimes and wrong other times.

### Detection Signals

```
□ Bug is intermittent — happens sometimes, not always
□ Bug is more frequent under load
□ Bug disappears when you add console.log (changes timing)
□ Multiple concurrent users trigger it but single user doesn't
□ Tests pass individually but fail when run in parallel
```

### Pattern: UI Race Condition (Search/Filter)

```typescript
// ❌ BROKEN: Results from old query overwrite results from new query
function SearchComponent() {
  const [query, setQuery] = useState('');
  const [results, setResults] = useState([]);

  useEffect(() => {
    if (query) {
      searchApi(query).then(setResults);
      // User types "react", then quickly types "redux"
      // If "redux" response arrives before "react" response:
      // setResults called with redux results, then react results overwrite them
      // UI shows "react" results for "redux" query — WRONG
    }
  }, [query]);
}

// ✅ FIX: Track which request is current using AbortController
function SearchComponent() {
  const [query, setQuery] = useState('');
  const [results, setResults] = useState<SearchResult[]>([]);

  useEffect(() => {
    if (!query) {
      setResults([]);
      return;
    }

    const controller = new AbortController();

    searchApi(query, { signal: controller.signal })
      .then(setResults)
      .catch((err) => {
        if (err.name !== 'AbortError') {
          console.error('Search failed:', err);
        }
        // AbortError is expected — previous query was cancelled
      });

    return () => controller.abort(); // cancel previous request on new keypress
  }, [query]);
}
```

### Pattern: Database Race Condition (Check-Then-Act)

```typescript
// ❌ BROKEN: Time-of-check vs time-of-use (TOCTOU) race
async function transferFunds(fromId: string, toId: string, amount: number) {
  const account = await db.accounts.findById(fromId);

  // Another request might deduct funds between check and deduction!
  if (account.balance < amount) throw new Error('Insufficient funds');

  // GAP: balance can change here by another concurrent request
  await db.accounts.update(fromId, { balance: account.balance - amount });
  await db.accounts.update(toId, { balance: existing => existing + amount });
}

// ✅ FIX: Atomic operation with database-level constraint
async function transferFunds(fromId: string, toId: string, amount: number) {
  await db.transaction(async (trx) => {
    // SELECT FOR UPDATE — locks the row for this transaction
    const account = await trx.accounts.findById(fromId, { lock: true });

    if (account.balance < amount) throw new InsufficientFundsError(fromId, amount);

    // Both updates in same atomic transaction — all or nothing
    await trx.accounts.update(fromId, { balance: account.balance - amount });
    await trx.accounts.update(toId, { balance: existing => existing + amount });
  });
}
```

### Pattern: Singleton Initialization Race

```typescript
// ❌ BROKEN: Two callers both see uninitialized, both initialize
let dbConnection: Database | null = null;

async function getDatabase(): Promise<Database> {
  if (!dbConnection) {
    // Two async calls both reach here before either creates the connection
    dbConnection = await createDatabaseConnection(); // called twice!
  }
  return dbConnection;
}

// ✅ FIX: Promise-based singleton — second caller gets same promise
let connectionPromise: Promise<Database> | null = null;

async function getDatabase(): Promise<Database> {
  if (!connectionPromise) {
    connectionPromise = createDatabaseConnection().catch((err) => {
      connectionPromise = null; // reset on failure so next call can retry
      throw err;
    });
  }
  return connectionPromise; // both callers await same promise
}
```

---

## 🔷 ADVANCED-02: Memory Leaks

### Detection Signals

```
□ Application slows down over time
□ Memory usage grows steadily without plateau
□ Performance degrades after extended use
□ Crash only happens after N hours of runtime
□ Heap snapshot shows growing objects of same type
```

### Pattern: Event Listener Leak

```typescript
// ❌ BROKEN: Event listener added but never removed
function ModalComponent() {
  useEffect(() => {
    const handleKeyDown = (e: KeyboardEvent) => {
      if (e.key === 'Escape') closeModal();
    };
    document.addEventListener('keydown', handleKeyDown);
    // Component unmounts → listener remains → memory leak + multiple handlers
  }, []);
}

// ✅ FIX: Return cleanup function from useEffect
function ModalComponent() {
  useEffect(() => {
    const handleKeyDown = (e: KeyboardEvent) => {
      if (e.key === 'Escape') closeModal();
    };

    document.addEventListener('keydown', handleKeyDown);
    return () => document.removeEventListener('keydown', handleKeyDown); // cleanup
  }, [closeModal]);
}

// Node.js / General pattern:
class EventDrivenService {
  private readonly handlers = new Map<string, EventHandler>();

  subscribe(event: string, handler: EventHandler): () => void {
    emitter.on(event, handler);
    this.handlers.set(event, handler);

    // Return unsubscribe function
    return () => {
      emitter.off(event, handler);
      this.handlers.delete(event);
    };
  }

  destroy(): void {
    // Clean up all handlers
    for (const [event, handler] of this.handlers) {
      emitter.off(event, handler);
    }
    this.handlers.clear();
  }
}
```

### Pattern: Timer/Interval Leak

```typescript
// ❌ BROKEN: Timer continues after component unmounts
function LiveTimer() {
  const [time, setTime] = useState(new Date());

  useEffect(() => {
    setInterval(() => setTime(new Date()), 1000);
    // Timer runs forever — even after component unmounts
    // Calling setTime after unmount → React warning + potential leak
  }, []);
}

// ✅ FIX
function LiveTimer() {
  const [time, setTime] = useState(new Date());

  useEffect(() => {
    const timerId = setInterval(() => setTime(new Date()), 1_000);
    return () => clearInterval(timerId); // clear on unmount
  }, []);

  return <span>{time.toLocaleTimeString()}</span>;
}
```

### Pattern: Closure Holding Large Object

```typescript
// ❌ BROKEN: Closure retains entire largeData in memory
function processLargeDataset(largeData: LargeObject[]) {
  const count = largeData.length;

  // This closure captures the entire largeData array!
  return {
    getCount: () => count,            // OK — only uses count
    processItem: (i: number) => largeData[i], // keeps largeData alive
    // If processItem is stored anywhere (cache, global), largeData never GC'd
  };
}

// ✅ FIX: Extract only what you need, don't close over large objects
function processLargeDataset(largeData: LargeObject[]) {
  const count = largeData.length;
  // Process immediately, don't store reference
  const processedItems = largeData.map(item => extractNeededFields(item));
  // largeData can now be GC'd

  return {
    getCount: () => count,
    getItem: (i: number) => processedItems[i], // only holds processed data
  };
}
```

---

## 🔷 ADVANCED-03: Stale Closures

### Pattern: Stale State in Async Callback

```typescript
// ❌ BROKEN: Value in callback is stale
function PollComponent() {
  const [data, setData] = useState<DataItem[]>([]);

  useEffect(() => {
    const pollInterval = setInterval(async () => {
      const newData = await fetchLatestData();
      // STALE: data here always refers to the initial [] array
      // because the closure captured data at component mount
      const combined = [...data, ...newData]; // data is always []!
      setData(combined);
    }, 5000);

    return () => clearInterval(pollInterval);
  }, []); // empty deps — captures stale data
}

// ✅ FIX A: Use functional update (doesn't close over state)
useEffect(() => {
  const pollInterval = setInterval(async () => {
    const newData = await fetchLatestData();
    setData(prev => [...prev, ...newData]); // prev is always current
  }, 5000);
  return () => clearInterval(pollInterval);
}, []);

// ✅ FIX B: Use ref to track current value
function PollComponent() {
  const [data, setData] = useState<DataItem[]>([]);
  const dataRef = useRef(data);

  useEffect(() => {
    dataRef.current = data; // keep ref in sync
  }, [data]);

  useEffect(() => {
    const pollInterval = setInterval(async () => {
      const newData = await fetchLatestData();
      setData([...dataRef.current, ...newData]); // ref is always current
    }, 5000);
    return () => clearInterval(pollInterval);
  }, []);
}
```

---

## 🔷 ADVANCED-04: Concurrency Bugs

### Pattern: Concurrent Mutation of Shared State

```typescript
// ❌ BROKEN: Concurrent updates lose data (read-modify-write race)
let viewCount = 0;

async function incrementViewCount(articleId: string): Promise<number> {
  viewCount = viewCount + 1; // not atomic — lost updates under concurrency
  await saveViewCount(articleId, viewCount);
  return viewCount;
}
// 100 concurrent requests: many reads same value, all increment to same value
// Result: viewCount = 1 instead of 100

// ✅ FIX A: Database atomic increment
async function incrementViewCount(articleId: string): Promise<number> {
  const result = await db.query<{ new_count: number }>(
    'UPDATE articles SET view_count = view_count + 1 WHERE id = $1 RETURNING view_count AS new_count',
    [articleId]
  );
  return result.rows[0].new_count;
}

// ✅ FIX B: Mutex for in-memory operations
class AsyncMutex {
  private queue: Array<() => void> = [];
  private locked = false;

  async acquire(): Promise<() => void> {
    return new Promise((resolve) => {
      const tryAcquire = () => {
        if (!this.locked) {
          this.locked = true;
          resolve(() => {
            this.locked = false;
            if (this.queue.length > 0) this.queue.shift()!();
          });
        } else {
          this.queue.push(tryAcquire);
        }
      };
      tryAcquire();
    });
  }
}

const counterMutex = new AsyncMutex();
let viewCount = 0;

async function incrementViewCount(): Promise<number> {
  const release = await counterMutex.acquire();
  try {
    viewCount++;
    return viewCount;
  } finally {
    release();
  }
}
```

### Pattern: Deadlock

```typescript
// ❌ BROKEN: Deadlock when two operations try to acquire locks in opposite order
async function transferA_to_B() {
  const lockA = await acquireLock('account-A');
  const lockB = await acquireLock('account-B'); // waits for B
  // ...
}

async function transferB_to_A() {
  const lockB = await acquireLock('account-B');
  const lockA = await acquireLock('account-A'); // waits for A — DEADLOCK
  // ...
}

// ✅ FIX: Always acquire locks in consistent order (alphabetical, numeric, etc.)
async function transfer(fromId: string, toId: string) {
  // Sort IDs so locks are always acquired in same order
  const [firstId, secondId] = [fromId, toId].sort();
  const firstLock = await acquireLock(firstId);
  const secondLock = await acquireLock(secondId);

  try {
    // ... transfer logic
  } finally {
    secondLock.release();
    firstLock.release();
  }
}
```

---

## 🔷 ADVANCED-05: Performance Bugs

### Pattern: Blocking the Event Loop (Node.js)

```typescript
// ❌ BROKEN: Synchronous CPU work blocks all other requests
app.get('/api/report', (req, res) => {
  const report = generateHeavyReport(largeDataset); // blocks for 5 seconds
  // All other requests queued — server appears down
  res.json(report);
});

// ✅ FIX A: Move to worker thread
import { Worker, isMainThread, parentPort, workerData } from 'worker_threads';

app.get('/api/report', async (req, res) => {
  const report = await runInWorker('./reportWorker.js', { dataset: largeDataset });
  res.json(report);
});

async function runInWorker<T>(scriptPath: string, data: unknown): Promise<T> {
  return new Promise((resolve, reject) => {
    const worker = new Worker(scriptPath, { workerData: data });
    worker.on('message', resolve);
    worker.on('error', reject);
    worker.on('exit', (code) => {
      if (code !== 0) reject(new Error(`Worker exited with code ${code}`));
    });
  });
}

// ✅ FIX B: Chunk work across event loop ticks
async function generateHeavyReportAsync(chunks: DataChunk[]): Promise<Report> {
  const results = [];
  for (const chunk of chunks) {
    results.push(processChunk(chunk));
    await new Promise(resolve => setImmediate(resolve)); // yield to event loop
  }
  return combineResults(results);
}
```

### Pattern: Cascading API Failures

```typescript
// ❌ BROKEN: One slow/failed service blocks everything
async function loadDashboard(userId: string) {
  const user = await fetchUser(userId);           // if this is slow (2s)...
  const orders = await fetchOrders(userId);       // this waits
  const recommendations = await fetchRecs(userId); // this waits
  // Total: up to 6 seconds — should be 2s (longest single call)
}

// ✅ FIX: Parallel fetch with individual error handling
async function loadDashboard(userId: string): Promise<DashboardData> {
  const [userResult, ordersResult, recsResult] = await Promise.allSettled([
    fetchUser(userId).then(data => ({ type: 'user' as const, data })),
    fetchOrders(userId).then(data => ({ type: 'orders' as const, data })),
    fetchRecs(userId).then(data => ({ type: 'recs' as const, data })),
  ]);

  // Each service failure is isolated — dashboard still works partially
  return {
    user: userResult.status === 'fulfilled' ? userResult.value.data : null,
    orders: ordersResult.status === 'fulfilled' ? ordersResult.value.data : [],
    recommendations: recsResult.status === 'fulfilled' ? recsResult.value.data : [],
  };
}
```

### Pattern: Retry with Exponential Backoff

```typescript
// ❌ WRONG: Retry immediately — hammers failing service
async function fetchWithRetry<T>(url: string): Promise<T> {
  for (let i = 0; i < 3; i++) {
    try {
      return await fetch(url).then(r => r.json());
    } catch {
      // retry immediately — makes outage worse
    }
  }
  throw new Error('Max retries exceeded');
}

// ✅ CORRECT: Exponential backoff with jitter
async function fetchWithRetry<T>(
  url: string,
  options: { maxRetries?: number; baseDelayMs?: number } = {}
): Promise<T> {
  const { maxRetries = 3, baseDelayMs = 1000 } = options;

  for (let attempt = 0; attempt <= maxRetries; attempt++) {
    try {
      const response = await fetch(url);
      if (!response.ok && response.status >= 500 && attempt < maxRetries) {
        throw new Error(`HTTP ${response.status}`); // retry on server errors
      }
      return response.json() as Promise<T>;
    } catch (error) {
      if (attempt === maxRetries) throw error;

      const delay = baseDelayMs * Math.pow(2, attempt) + Math.random() * 1000; // jitter
      await new Promise(resolve => setTimeout(resolve, delay));
    }
  }
  throw new Error('unreachable');
}
```

---

## 🔷 ADVANCED DEBUGGING TECHNIQUES

### Heap Snapshot Analysis (Chrome/Node.js)

```javascript
// In Chrome DevTools or Node.js:
// 1. Take heap snapshot
// 2. Compare snapshots over time
// 3. Look for growing object counts
// 4. Find retaining paths

// Node.js programmatic snapshot
const { writeHeapSnapshot } = require('v8');
writeHeapSnapshot('/tmp/heapdump-' + Date.now() + '.heapsnapshot');
```

### Async Stack Traces

```javascript
// Enable async stack traces in Node.js
node --async-stack-traces script.js

// In Chrome DevTools:
// Settings -> Enable async stack traces
```

### Logging for Race Conditions

```typescript
// Use correlation IDs to trace requests
function logWithContext(context: string, ...args: unknown[]) {
  const correlationId = getCorrelationId();
  const timestamp = new Date().toISOString();
  console.log(`[${timestamp}] [${correlationId}] [${context}]`, ...args);
}

// Log at key points
async function processRequest(request: Request) {
  logWithContext('processRequest', 'start', { id: request.id });
  
  const step1 = await step1(request);
  logWithContext('processRequest', 'step1 complete', { result: step1.id });
  
  const step2 = await step2(step1);
  logWithContext('processRequest', 'step2 complete', { result: step2.id });
  
  return step2;
}
```

---

## 🔷 ADVANCED-06: Circuit Breaker Pattern

> **VIP EXPERT NOTE:** When an external service is down, continuing to call it
> makes everything worse (thread exhaustion, cascading timeouts). The circuit
> breaker stops calling after N failures and retries after a cooldown.

```typescript
class CircuitBreaker {
  private failures = 0;
  private lastFailureTime = 0;
  private state: 'closed' | 'open' | 'half-open' = 'closed';

  constructor(
    private readonly maxFailures: number = 5,
    private readonly cooldownMs: number = 30_000,
  ) {}

  async execute<T>(fn: () => Promise<T>): Promise<T> {
    if (this.state === 'open') {
      if (Date.now() - this.lastFailureTime > this.cooldownMs) {
        this.state = 'half-open'; // Allow one test request
      } else {
        throw new CircuitOpenError('Circuit breaker is open — service unavailable');
      }
    }

    try {
      const result = await fn();
      this.onSuccess();
      return result;
    } catch (error) {
      this.onFailure();
      throw error;
    }
  }

  private onSuccess(): void {
    this.failures = 0;
    this.state = 'closed';
  }

  private onFailure(): void {
    this.failures++;
    this.lastFailureTime = Date.now();
    if (this.failures >= this.maxFailures) {
      this.state = 'open';
    }
  }
}

// Usage:
const paymentCircuit = new CircuitBreaker(5, 30_000);

async function processPayment(data: PaymentInput): Promise<PaymentResult> {
  return paymentCircuit.execute(() => paymentGateway.charge(data));
}
```

---

## 🔷 ADVANCED-07: Graceful Shutdown

```typescript
// ❌ BROKEN: Hard shutdown — in-flight requests are dropped, DB connections leak
process.on('SIGTERM', () => process.exit(0));

// ✅ CORRECT: Graceful shutdown — finish in-flight work, close connections
function createGracefulShutdown(server: http.Server, resources: Closeable[]) {
  let isShuttingDown = false;

  async function shutdown(signal: string): Promise<void> {
    if (isShuttingDown) return;
    isShuttingDown = true;
    console.log(`\n[${signal}] Graceful shutdown started...`);

    // 1. Stop accepting new requests
    server.close(() => console.log('HTTP server closed'));

    // 2. Wait for in-flight requests (with timeout)
    const timeout = setTimeout(() => {
      console.error('Shutdown timeout — forcing exit');
      process.exit(1);
    }, 30_000);

    // 3. Close resources (DB pools, Redis, message queues)
    for (const resource of resources) {
      try {
        await resource.close();
        console.log(`Closed: ${resource.constructor.name}`);
      } catch (error) {
        console.error(`Error closing ${resource.constructor.name}:`, error);
      }
    }

    clearTimeout(timeout);
    console.log('Shutdown complete');
    process.exit(0);
  }

  process.on('SIGTERM', () => shutdown('SIGTERM'));
  process.on('SIGINT', () => shutdown('SIGINT'));
}
```

---

## 🔷 VIP EXPERT NOTE: STRUCTURED LOGGING & OBSERVABILITY

> The difference between "we found the bug in 5 minutes" and "we spent 3 days" is
> almost always the quality of logging. Structured logs are searchable; console.log is not.

```typescript
// ❌ WRONG: Unstructured logging
console.log('User created:', userId);
console.log('Error!', error);

// ✅ CORRECT: Structured logging with context
import pino from 'pino';

const logger = pino({
  level: process.env.LOG_LEVEL || 'info',
  transport: process.env.NODE_ENV === 'development'
    ? { target: 'pino-pretty' }   // Human readable in dev
    : undefined,                    // JSON in production
});

// Create child logger with request context
function createRequestLogger(req: Request) {
  return logger.child({
    requestId: req.headers['x-request-id'] ?? crypto.randomUUID(),
    method: req.method,
    path: req.path,
    userId: req.user?.id,
  });
}

// Usage in route handler:
app.post('/api/orders', async (req, res) => {
  const log = createRequestLogger(req);
  log.info({ input: req.body }, 'Creating order');

  try {
    const order = await orderService.create(req.body);
    log.info({ orderId: order.id }, 'Order created successfully');
    return res.status(201).json(order);
  } catch (error) {
    if (error instanceof ValidationError) {
      log.warn({ fields: error.fields }, 'Order validation failed');
      return res.status(422).json({ error: error.fields });
    }
    log.error({ error }, 'Unexpected error creating order');
    return res.status(500).json({ error: 'Internal server error' });
  }
});

// The structured output looks like:
// {"level":30,"time":1711234567890,"requestId":"abc-123","userId":"usr_456",
//  "method":"POST","path":"/api/orders","orderId":"ord_789","msg":"Order created successfully"}
// This is searchable, filterable, and alertable in production logging systems.
```

### Key Logging Rules:

```
✅ DO log: request IDs, user IDs, operation outcomes, timing, error details
✅ DO use: structured JSON format, correlation IDs, log levels
✅ DO include: enough context to reproduce the issue without accessing the codebase

❌ NEVER log: passwords, API keys, tokens, credit card numbers, PII
❌ NEVER use: console.log in production (use a proper logger)
❌ NEVER: log-and-continue without handling the error
```

---

## 🔷 WHEN TO ESCALATE

If you encounter these scenarios, escalate to senior engineers or use specialized debugging:

- Distributed system deadlocks across services
- Database deadlock analysis
- Low-level memory corruption (C/C++/Rust)
- Kernel-level issues
- Production incidents requiring immediate resolution
- Security vulnerabilities discovered during debugging

---

*This module covers advanced debugging scenarios. Use systematic debugging methodology and escalate when needed.*


---

## PART 8: ANTI-PATTERNS

# 06 — Anti-Patterns: What NOT to Do

> **Principle:** Bad code gives you feedback; perfect code doesn't. Err on the side of writing simple, explicit code.  
> **Sources:** [Superpowers TDD](https://github.com/obra/superpowers) · [Professional Programming](https://github.com/charlax/professional-programming) · [Google Eng Practices](https://github.com/google/eng-practices) · [Microsoft Playbook](https://github.com/microsoft/code-with-engineering-playbook)

---

## 🎯 CONSTANT CORE — APPLY BEFORE EVERY CODE ACTION

```
STEP 0 — MANDATORY SELF-CHECK
□ Am I about to write/fix code before writing a failing test? → STOP
□ Am I rationalizing why a rule doesn't apply "this time"? → STOP
□ Am I adding multiple unrelated changes in one edit? → STOP
□ Am I skipping adjacent-code verification? → STOP
□ Select the matching anti-pattern section below if you need a specific reminder
```

```
STEP 0 — UNIVERSAL ANTI-PATTERN CONTRACT
1. Never write code you don't fully understand.
2. Never keep unverified code out of sunk-cost attachment.
3. Never add abstraction "just in case." YAGNI.
4. Never mock more than you test.
5. Never skip the adjacent-code compile/test step.
```

```
STEP 0 — MANDATORY ONLINE SEARCH TOOL
□ If the rule, pattern, or framework behavior is unfamiliar or may have changed, search SearXNG first for the most updated official notes and solutions.
□ SearXNG: https://github.com/searxng/searxng — free, open-source metasearch engine that aggregates 70+ search engines without tracking users or storing queries.
□ Do not guess based on stale knowledge. Verify with up-to-date sources before proceeding.
```

## 📑 TASK INDEX — Jump to your specific anti-pattern category

```
Task     Topic                                         When to Use
----------------------------------------------------------------------------------
TASK 1   Universal Instant-Rejection Patterns  →  Banned in any language
TASK 2   JavaScript/TypeScript Anti-Patterns  →  JS/TS specific mistakes
TASK 3   React Anti-Patterns  →  React component/hook mistakes
TASK 4   Python Anti-Patterns  →  Python specific mistakes
TASK 5   SQL & Database Anti-Patterns  →  Query and DB mistakes
TASK 6   CSS & Frontend Anti-Patterns  →  Styling and DOM mistakes
TASK 7   AI-Specific Cognitive Traps  →  Mental traps in AI coding
TASK 8   Design Smells & Code Rot  →  Architecture degradation
TASK 9   Common Rationalizations & Their Reality  →  Pushing back on excuses
TASK 10  Red Flags: STOP Immediately  →  Emergency stop signals
```

---

# TASK 1 — Universal Instant-Rejection Patterns
*These patterns must NEVER appear in generated or fixed code, any language.*

| Pattern | Why Banned | Fix |
|---------|------------|-----|
| `catch(e) {}` | Silent failure hides bugs | Handle or re-throw explicitly |
| `catch(e) { console.log(e) }` | Log-and-continue swallows errors | Handle or propagate |
| `as any` / `@ts-ignore` | Escapes type safety | Fix the type or narrow properly |
| `==` instead of `===` | Type coercion causes subtle bugs | Use strict equality |
| `var` | Function-scoped, hoisted confusion | Use `const` / `let` |
| Nested ternary > 1 level | Unreadable logic | Use `if/else` or early returns |
| Function > 60 lines | Violates single responsibility | Extract helpers |
| File > 500 lines | God file / module | Split by feature |
| Magic numbers inline | No semantic meaning | Name the constant |
| Mutating function parameters | Hidden side effects | Return a new value |
| SQL string concatenation | Injection vector | Use parameterized queries |
| Storing secrets in code | Security violation | Use env vars / secret managers |
| Async function without try/catch | Unhandled async errors | Wrap async boundaries |
| `TODO` without ticket reference | Orphaned work item | Add issue ID or remove |
| `eval()` / `new Function()` | Remote code execution risk | Use safe parsing |
| `with` statement | Unpredictable scope | Explicit property access |

### ⚠️ Common Errors While Avoiding These Patterns
- **Forgetting to ban `eval` in config-driven code** — dynamic config loaded from JSON/YAML can still execute if parsed unsafely.
- **Allowing `console.log` in production error handlers** — logs may leak PII or secrets to observability platforms.
- **Not catching `==` in generated/template code** — template engines or code generators sometimes emit loose equality.
- **Missing `await` in `catch` blocks** — `catch(e) { await logError(e); }` is fine, but `catch(e) { logError(e); }` where `logError` is async is a floating promise.

### 🧩 Complex Errors / Edge Cases
- **`with` statement in VM contexts:** Some sandboxed environments use `with` to inject globals — this leaks scope unpredictably.
- **`new Function` in template engines:** Even "safe" template engines can execute arbitrary code if user input reaches the template.
- **Dynamic imports executing untrusted code:** `import(userControlledPath)` can load malicious modules.
- **`catch(e) { sentry.captureException(e) }` without re-throw:** The error is logged but the program continues in an invalid state.

### 🎯 Expert Precision Tips
- Run **ESLint + Semgrep** in CI with zero-tolerance rules for these patterns. Don't allow overrides without a security review.
- Use `--unhandled-rejections=strict` in Node.js to catch floating promises at runtime.
- Ban `eval` and `new Function` at the build tool level (webpack/vite plugin).
- Treat every `TODO` as a ticket or delete it. There is no middle ground.

---

# TASK 2 — JavaScript/TypeScript Anti-Patterns
*Common mistakes specific to JS/TS ecosystems.*

## 2.1 Type Safety Escapes
```typescript
// ❌ BANNED
const data = response as any;
// @ts-ignore
const result = unsafeCall();

// ✅ CORRECT
const data = parseResponse(response); // narrow explicitly
```

## 2.2 Implicit Coercion Traps
```typescript
// ❌ BANNED
if (value == null) { } // ambiguous
if (count == 0) { }     // coerces types

// ✅ CORRECT
if (value === null || value === undefined) { }
if (count === 0) { }
```

## 2.3 Floating Promise / Unhandled Rejection
```typescript
// ❌ BANNED
fetchData(); // Promise ignored

// ✅ CORRECT
await fetchData();
// OR
fetchData().catch(handleError);
```

## 2.4 Prototype Pollution
```typescript
// ❌ BANNED
const merged = Object.assign({}, userInput); // can pollute prototype

// ✅ CORRECT
const merged = Object.assign(Object.create(null), userInput);
// OR use structuredClone for deep safe copy
```

## 2.5 Incorrect Array Methods
```typescript
// ❌ BANNED: mutates original
users.sort((a,b) => a.id - b.id);

// ✅ CORRECT
const sorted = [...users].sort((a,b) => a.id - b.id);
```

### ⚠️ Common Errors While Avoiding JS/TS Anti-Patterns
- **Using `as` for third-party types** instead of module augmentation or declaration merging.
- **`typeof x === 'object'` check that passes for `null`** — classic JavaScript footgun.
- **Using `instanceof` across iframe boundaries** — fails because each iframe has its own prototype chain.
- **`JSON.stringify` producing `undefined`** for functions/symbols, causing silent data loss.
- **`parseInt` without radix** — `parseInt('08')` can parse as octal in older engines.

### 🧩 Complex Errors / Edge Cases
- **`Array.from` with a mapping function on sparse arrays** — skips holes differently than `map()`.
- **`Object.keys` returning strings** even for numeric keys, causing type mismatches.
- **`Promise.race` with a never-settling Promise** — can leak memory if the loser holds references.
- **`Error` subclassing without `Object.setPrototypeOf`** — `instanceof` may fail in transpiled code.

### 🎯 Expert Precision Tips
- Prefer **Zod** or **Valibot** for runtime validation over manual `typeof` chains.
- Use `structuredClone` for deep copies instead of `JSON.parse(JSON.stringify(...))`.
- Always provide radix to `parseInt`: `parseInt(x, 10)`.
- Use `Array.isArray` instead of `instanceof Array` (works across frames).
- For optional chaining, prefer `??` over `||` when `0`, `''`, or `false` are valid values.

---

# TASK 3 — React Anti-Patterns
*Mistakes that break React's component model or cause subtle bugs.*

| Pattern | Why Banned | Fix |
|---------|------------|-----|
| `useEffect` with missing deps | Stale closures, infinite loops | Include all dependencies |
| `setState` in render | Infinite loop | Move to event handler or useEffect |
| Direct DOM mutation | Breaks virtual DOM reconciliation | Use refs and React state |
| Array index as dynamic `key` | Wrong component reuse on reorder | Use stable unique IDs |
| `useEffect(() => {}, [])` for data fetch without cleanup | Memory leaks, race conditions | Add AbortController or cancellation flag |
| Passing new object/array as default prop | Unnecessary re-renders | Memoize or define outside component |
| `useMemo` for trivial computations | Overhead exceeds benefit | Only for expensive calculations |
| `dangerouslySetInnerHTML` without sanitization | XSS vulnerability | Use DOMPurify or textContent |

## Example: Missing useEffect Cleanup
```typescript
// ❌ BANNED
useEffect(() => {
  const subscription = source.subscribe(setData);
}, [source]); // leak on unmount

// ✅ CORRECT
useEffect(() => {
  const subscription = source.subscribe(setData);
  return () => subscription.unsubscribe();
}, [source]);
```

### ⚠️ Common Errors While Avoiding React Anti-Patterns
- **Using `useEffect` for data fetching when framework loaders exist** — Next.js `getServerSideProps` or Remix loaders are more robust.
- **`useCallback` without memoized children** — the callback is stable, but the child re-renders anyway.
- **Resetting form state with `useEffect` on prop change** — this is a code smell; derive state or use a key.
- **Calling `setState` synchronously inside an event handler that already triggers a re-render** — causes double renders.

### 🧩 Complex Errors / Edge Cases
- **Context value object identity causing mass re-render:** A new object passed to `Provider` re-renders every consumer, even if values are semantically identical.
- **Server Component accidentally importing client-only hooks:** Causes a build-time or runtime error in Next.js App Router.
- **Refs not triggering re-renders:** Updating `ref.current` doesn't cause a re-render, so UI stays stale if you use refs as state.
- **Concurrent Mode tearing:** Reading external mutable stores during render causes inconsistent UI.

### 🎯 Expert Precision Tips
- If a state update causes another state update in the same render, use a **reducer** or derive the value instead.
- Keep `useEffect` deps honest. If ESLint complains, 95% of the time it's a real bug.
- Use `useMemo` only for expensive calculations (>1ms) or stable object references passed to memoized children.
- Prefer `<form>` native validation + React state over complex `useEffect` form syncing.
- For lists, generate stable IDs at data creation time, never during render.

---

# TASK 4 — Python Anti-Patterns
*Mistakes specific to Python code.*

## 4.1 Mutable Default Arguments
```python
# ❌ BANNED
def append_item(item, items=[]):
    items.append(item)
    return items

# ✅ CORRECT
def append_item(item, items=None):
    if items is None:
        items = []
    items.append(item)
    return items
```

## 4.2 Bare Except
```python
# ❌ BANNED
try:
    risky()
except:  # catches KeyboardInterrupt, SystemExit
    pass

# ✅ CORRECT
try:
    risky()
except ValueError as e:
    logger.error(e)
```

## 4.3 Using `list` or `dict` as default kwargs
See 4.1 — same rule applies to any mutable default.

## 4.4 Implicit String Concatenation in Tuples
```python
# ❌ BANNED (accidental tuple)
items = (
    "a",
    "b"  # missing comma
    "c"
)
# items is ("a", "bc") — not a syntax error!

# ✅ CORRECT: use trailing commas
items = ("a", "b", "c")
```

## 4.5 `is` for Value Equality
```python
# ❌ BANNED
if x is 0:  # works by accident (interning), semantically wrong
    pass

# ✅ CORRECT
if x == 0:
    pass
```

### ⚠️ Common Errors While Avoiding Python Anti-Patterns
- **Using `isinstance(x, list)` instead of abstract base classes** — breaks tuples, generators, and numpy arrays. Use `collections.abc.Sequence`.
- **Mutable class attributes shared across instances:** `class Foo: items = []` creates one list for all instances.
- **Monkey-patching standard library:** Breaks invariants for all downstream code and dependencies.
- **Not handling encoding explicitly** — `open(path)` uses the system encoding, causing cross-platform bugs.

### 🧩 Complex Errors / Edge Cases
- **`__del__` destructor resurrection:** An object is revived during finalization, causing unpredictable garbage collection behavior.
- **Circular imports in type hints:** Resolved only at runtime when the hint is evaluated, causing `ImportError` or `NameError`.
- **`asyncio` task exceptions swallowed until awaited:** Un awaited tasks don't surface errors until garbage collection.
- **Global Interpreter Lock (GIL) misconceptions:** CPU-bound threads don't run in parallel; use processes or native extensions.

### 🎯 Expert Precision Tips
- Use `pathlib.Path` over `os.path` for all filesystem operations.
- Use `datetime.timezone.utc` or `zoneinfo` — never naive datetimes for anything crossing a system boundary.
- Use `with` context managers for all resource acquisition (files, locks, connections).
- Prefer `dataclasses` or **Pydantic** over manual `__init__` boilerplate.
- Always use `logger.exception()` inside an `except` block to capture the full traceback.

---

# TASK 5 — SQL & Database Anti-Patterns
*Mistakes that cause performance issues or security vulnerabilities.*

## 5.1 String Concatenation in Queries
```sql
-- ❌ BANNED
SELECT * FROM users WHERE name = '%s' % user_input;

-- ✅ CORRECT
SELECT * FROM users WHERE name = ?;
```

## 5.2 SELECT *
```sql
-- ❌ BANNED (breaks when schema changes, wastes bandwidth)
SELECT * FROM users;

-- ✅ CORRECT
SELECT id, name, email FROM users;
```

## 5.3 Missing Index on Foreign Keys / Filters
- Always index columns used in `WHERE`, `JOIN`, and `ORDER BY`.
- Use `EXPLAIN` to verify query plans.

## 5.4 Long-Running Transactions
- Keep transactions as short as possible.
- Avoid user-facing I/O inside a transaction.

### ⚠️ Common Errors While Avoiding DB Anti-Patterns
- **Using ORM bulk operations that bypass application-level validation** — data integrity is compromised.
- **Not handling `NULL` in `UNIQUE` constraints** — SQL allows multiple `NULL`s in a unique column.
- **Blindly adding composite indexes** without considering query selectivity.
- **Using `SELECT FOR UPDATE` on large ranges** — causes lock contention and deadlocks.

### 🧩 Complex Errors / Edge Cases
- **Lock escalation from row to table:** In some DB engines, updating too many rows in one transaction escalates to a table lock.
- **Implicit type casting preventing index use:** Comparing a `text` column to an `integer` forces a sequential scan.
- **N+1 in ORM lazy loading:** Hidden in loops, especially with GraphQL field resolvers.
- **Deadlocks due to inconsistent lock ordering:** Transaction A updates rows 1→2, Transaction B updates rows 2→1.

### 🎯 Expert Precision Tips
- Write raw SQL for complex queries instead of fighting the ORM.
- Always use explicit column lists — `SELECT *` is a breaking change waiting to happen.
- Run `EXPLAIN (ANALYZE, BUFFERS)` on production-like data before deploying schema or query changes.
- Separate read and write transactions where possible. Long read transactions block vacuum and replication.
- For pagination, use keyset pagination (cursor-based) over `OFFSET` for large datasets.

---

# TASK 6 — CSS & Frontend Anti-Patterns
*Mistakes in styling and DOM manipulation.*

| Pattern | Why Banned | Fix |
|---------|------------|-----|
| `!important` | Abuse of cascade, hard to maintain | Fix specificity hierarchy |
| Inline styles for dynamic theming | Not cacheable, breaks CSP | Use CSS variables/classes |
| Magic pixel values | No semantic meaning | Use design tokens / variables |
| `display: none` for a11y hiding | Removed from accessibility tree | Use visually-hidden pattern |
| `* { margin: 0; padding: 0; }` in component CSS | Leaks global reset | Scope resets to component root |

### ⚠️ Common Errors While Avoiding CSS Anti-Patterns
- **Using `px` for font sizes** — breaks user zoom preferences and accessibility.
- **Not testing responsive layouts at intermediate breakpoints** — designs often break at 768px or 1024px.
- **Over-nesting in CSS preprocessors** — generates bloated selectors and specificity wars.
- **Animating `width`, `height`, `top`, `left`** — triggers layout thrashing. Use `transform` and `opacity`.

### 🧩 Complex Errors / Edge Cases
- **Container query vs viewport media query precedence:** Layout breaks inside nested components but works at the page level.
- **CSS specificity wars in component libraries:** Library styles override local styles unpredictably due to load order.
- **Focus-visible vs focus pseudo-classes:** Removing all focus outlines breaks keyboard navigation.
- **Sub-pixel rendering differences:** 1px borders look different on Retina vs non-Retina displays.

### 🎯 Expert Precision Tips
- Use `rem` for typography, `px` for borders, and CSS custom properties (variables) for theming.
- Scope global resets to the component root or use CSS modules/Shadow DOM.
- Prefer `transform: translate()` and `opacity` for animations to stay on the compositor thread.
- Use `prefers-reduced-motion` media queries for accessibility.
- For hiding elements accessibly, use the `.visually-hidden` pattern (absolute positioning off-screen) rather than `display: none`.

---

# TASK 7 — AI-Specific Cognitive Traps
*Mental traps that lead AI-generated code astray.*

## 7.1 The Sunk-Cost Trap
- **Excuse:** "I already wrote X lines; deleting is wasteful."
- **Reality:** Keeping unverified code is technical debt. If it was written before a failing test, **delete it**.

## 7.2 The "Spirit Not Ritual" Rationalization
- **Excuse:** "I'll test after — it achieves the same goal."
- **Reality:** Tests-after verify "what does this do?" Tests-first verify "what should this do?" They are not equivalent.

## 7.3 The Mock Overdose
- **Symptom:** Tests have more mocks than real code.
- **Result:** You're testing your imagination, not the system.
- **Fix:** Test real integrations at boundaries; mock only external I/O.

## 7.4 The Speculative Generality
- **Symptom:** Adding abstraction "in case we need it later."
- **Result:** Over-engineering that complicates the present.
- **Fix:** Solve the problem you have now. YAGNI.

## 7.5 The Adjacent-Code Blindness
- **Symptom:** Fix works in isolation but breaks imports, types, or siblings.
- **Fix:** Before submitting, compile/test the whole module.

## 7.6 The "Trust the User Input" Trap
- **Symptom:** Assuming inputs are well-formed because "the frontend validates."
- **Fix:** Validate at every boundary. Frontend validation is UX, not security.

### ⚠️ Common Errors While Avoiding Cognitive Traps
- **Rationalizing why TDD "doesn't fit this micro-task"** — if it's too small to test, it's too small to need code.
- **Keeping broken code because "the user will review"** — you're the expert; ship verified code.
- **Over-fitting to the example in the prompt** while missing edge cases.
- **Imitating patterns from outdated training data** — e.g., class components in React when hooks are standard.

### 🧩 Complex Errors / Edge Cases
- **Confirmation bias in debugging:** You find evidence that supports your first hypothesis and ignore contradictory data.
- **Authority bias:** Assuming a library or framework can't be the source of the bug.
- **Anchoring on the user's proposed solution** instead of independently verifying the root cause.

### 🎯 Expert Precision Tips
- When in doubt, **apply the constant core**. The rules exist because they prevent the exact failure mode you're experiencing.
- If you feel the urge to skip a step, that's the signal to **double down** on that step.
- Treat every piece of generated code as guilty until proven innocent by a test.
- If you don't understand why a fix works, you haven't finished debugging.

---

# TASK 8 — Design Smells & Code Rot
*Indicators that architecture is degrading.*

| Smell | Indicator | Refactor Target |
|-------|-----------|-----------------|
| **Feature Envy** | Function uses more data from another module than its own | Move the function |
| **Primitive Obsession** | Passing raw strings/ints instead of domain types | Introduce value objects |
| **Shotgun Surgery** | One change requires edits in many files | Consolidate responsibility |
| **Divergent Change** | One file changes for unrelated reasons | Split by feature |
| **Data Clumps** | Same groups of variables appear together | Extract into a class/struct |
| **Temporary Field** | Object has fields only used sometimes | Move fields to where they're used |
| **God Object** | One class knows everything | Extract responsibilities |
| **Leaky Abstraction** | Caller must know implementation details | Hide internals behind clean interface |

### ⚠️ Common Errors While Remediating Design Smells
- **Refactoring a smell without understanding why it emerged** — the smell will return.
- **Extracting classes that have no coherent behavior** — abstraction for abstraction's sake.
- **Moving the function but not the tests** — tests become orphaned and break.
- **Breaking the public API** to fix an internal smell without a migration path.

### 🧩 Complex Errors / Edge Cases
- **Distributed feature envy across microservices:** A service constantly calls another for data it should own.
- **Primitive obsession in API contracts:** Changing a `string` to a value object requires coordination across multiple services.
- **Leaky abstractions in framework wrappers:** The wrapper exposes framework-specific types, coupling all callers.
- **Over-correction:** Extracting 50 tiny classes from one god object, creating a navigation nightmare.

### 🎯 Expert Precision Tips
- Fix the smell **closest to the data**. If a function envies another module, move it there.
- When introducing value objects, start with **read-only wrappers** around primitives to minimize blast radius.
- If one change requires edits in >3 files, stop and redesign the boundary.
- Use the **boy scout rule** for smells: clean up the area you touched, but don't rewrite the whole codebase.

---

# TASK 9 — Common Rationalizations & Their Reality
*When you hear these in your head, push back.*

| Excuse | Reality |
|--------|---------|
| "Issue is simple, don't need process" | Simple bugs have root causes too. Process is fast for simple bugs. |
| "Emergency, no time for process" | Systematic debugging is FASTER than guess-and-check thrashing. |
| "I'll write tests after confirming the fix" | Untested fixes don't stick. Test first proves it. |
| "Multiple fixes at once saves time" | Can't isolate what worked. Causes new bugs. |
| "TDD is dogmatic, I'm being pragmatic" | TDD IS pragmatic. It finds bugs before commit. |
| "This is different because..." | It's not. The rules exist because they work. |
| "It's just a quick hack" | Quick hacks become permanent production code. |
| "The compiler will catch it" | Compilers catch type errors, not logic or design errors. |

### How to Push Back
```
When you think: "I'll test after."
Say instead: "I'll write the test now so I know what 'fixed' means."

When you think: "This is too small to need a test."
Say instead: "If it's too small to test, it's too small to need code."

When you think: "One more fix attempt won't hurt."
Say instead: "Three failures means my model is wrong. Time to escalate."
```

---

# TASK 10 — Red Flags: STOP Immediately
*If you catch yourself doing any of these, STOP and return to first principles.*

- Proposing solutions before understanding the problem
- Adding "just one more feature" to an already-large PR
- Rationalizing why a rule doesn't apply "this time"
- Writing code before a failing test exists
- Making multiple unrelated changes in one edit
- Skipping adjacent-code verification
- Committing with a message like "WIP" or "trying something"
- Ignoring a failing CI check because "it's not related to my change"
- Using `any`, `eval`, or string concatenation in SQL "just this once"

**All of these mean: STOP. Return to first principles.**


---

## PART 9: RESEARCH & ANALYSIS

# Category: Research & Analysis Prompts
## Complete Guide with Methods, Use Cases, and Best Practices

---

## Table of Contents
1. [Overview](#overview)
2. [Deep Research with Source Grading](#deep-research-with-source-grading)
3. [Technology Comparison Matrix](#technology-comparison-matrix)
4. [Codebase Analysis Protocol](#codebase-analysis-protocol)
5. [Dependency Security Audit](#dependency-security-audit)
6. [Performance Analysis](#performance-analysis)
7. [Learning/Teaching Prompts](#learningteaching-prompts)
8. [Quick Research Checklists](#quick-research-checklists)

---

## Overview

### When to Use Research Prompts

| Scenario | Recommended Method |
|----------|-------------------|
| Evaluating new technologies | Technology Comparison Matrix |
| Researching best practices | Deep Research with Source Grading |
| Understanding a codebase | Codebase Analysis Protocol |
| Security audit | Dependency Security Audit |
| Performance optimization | Performance Analysis |
| Learning new concepts | Learning/Teaching Prompts |

### Research Principles

**Key Practices:**
1. **Source Quality** — Not all sources are equal; grade them
2. **Recency** — Technology changes fast; prefer recent sources
3. **Verification** — Cross-reference conflicting information
4. **Practicality** — Focus on actionable findings
5. **Honesty** — Acknowledge uncertainty and knowledge boundaries

---

## Deep Research with Source Grading

### When to Use
Use this for any research where accuracy and reliability matter.

### Why It Works
Source grading exposes AI's confidence level; conflict surfacing is the most valuable critical thinking step; uncertainty labeling prevents costly wrong decisions.

### The Prompt:

```
Research this topic with the rigor of a technical writer producing documentation 
for a production team.

TOPIC
[Your research question, e.g., "Best practices for JWT token rotation in 2024", 
"PocketBase vs Supabase for production use", "Nginx rate limiting configuration options"]

RESEARCH REQUIREMENTS

1. SOURCE QUALITY STANDARDS
For each piece of information, cite the source and grade it:
- Tier 1 (Most trusted): Official documentation, RFC/spec, peer-reviewed paper, 
  core maintainer post
- Tier 2 (Reliable): Major tech company engineering blog, well-known expert with 
  credited expertise
- Tier 3 (Use with caution): Community articles, tutorials — must be corroborated 
  by Tier 1/2

2. RECENCY FILTER
- Prefer sources from [CURRENT YEAR] or [CURRENT YEAR - 1]
- Flag any information that may be outdated (technology versions change fast)
- For anything pre-2022: explicitly note "this may have changed — verify against current docs"

3. CONFLICTING INFORMATION
If you find sources that contradict each other, DO NOT silently pick one. Show me:
- Source A says X, Source B says Y
- Why they might disagree (version difference, different use cases, outdated info)
- Which to trust and why
- How to verify for my specific situation

4. PRACTICAL EXTRACTION
After the research, give me:
- The 5 most actionable findings
- The 3 most common mistakes people make on this topic
- Exact commands, configs, or code snippets that are verified to work
- What to check/test to confirm the information applies to my setup

5. KNOWLEDGE BOUNDARIES
Be explicit about:
- What you know with high confidence (from well-documented Tier 1 sources)
- What you believe but cannot fully verify (label: [Unverified — check source])
- What has likely changed since your training data (label: [May be outdated — verify])

DO NOT present uncertain information confidently. It is better to say "I'm not 
certain, verify at [URL]" than to state something wrong with confidence.
```

### Source Tier Reference:

| Tier | Examples | Trust Level |
|------|----------|-------------|
| Tier 0 (Gold) | Official docs, RFCs, peer-reviewed journals | Highest |
| Tier 1 | Core maintainer posts, official blogs | Very High |
| Tier 2 | Major tech blogs, verified experts | High |
| Tier 3 | Community articles, tutorials | Medium — verify |
| Tier 4 | Forum posts, unverified sources | Low — avoid |

---

## Technology Comparison Matrix

### When to Use
Use this when choosing between technologies, libraries, or frameworks.

### Why It Works
Weighted scoring by stated priorities prevents generic answers; red flags requirement forces balanced coverage.

### The Prompt:

```
Compare these technologies for my use case. I need an objective comparison, 
not a popularity contest.

TECHNOLOGIES TO COMPARE
[e.g., PocketBase vs Firebase vs Supabase / Redis vs Memcached / 
Next.js vs Nuxt vs SvelteKit]

MY USE CASE CONTEXT
Scale: [expected users/requests]
Team size: [solo / small / large]
Budget: [self-hosted / managed / enterprise]
Key requirements: [list  →  non-negotiables]
Nice-to-haves: [list  →  ]

COMPARISON FRAMEWORK

For each technology, evaluate on these dimensions:
1. Maturity & stability (version, release cadence, breaking changes history)
2. Performance benchmarks (cite specific benchmarks, not opinions)
3. Developer experience (setup time, learning curve, documentation quality)
4. Production reliability (known outages, limitations at scale, failure modes)
5. Security track record (CVE history, security model, auth capabilities)
6. Community & ecosystem (package ecosystem, job market, long-term viability)
7. Cost at scale (calculate for my stated scale)
8. Self-host vs managed tradeoffs

DECISION MATRIX
Create a table scoring each technology  →  on each dimension, weighted by 
MY stated priorities.

RED FLAGS
For each technology: list the top  →  reasons NOT to choose it for my 
use case specifically.

HONEST RECOMMENDATION
Based only on my stated context, recommend ONE. Explain why, and explicitly 
state what would change your recommendation.

Cite sources for any benchmark numbers or factual claims. Do not recommend 
what is most popular — recommend what fits MY requirements.
```

---

## Codebase Analysis Protocol

### When to Use
Use this for comprehensive code audits, security reviews, or understanding legacy code.

### Why It Works
The 8-phase structure eliminates gaps; evidence mandate eliminates hallucinations; confidence ratings eliminate false positives.

### The Prompt:

```
You are a senior software architect performing a comprehensive code audit. 
Analyze the project at [PASTE CODE / REPO STRUCTURE / FILES HERE].

PHASE 1 — INVENTORY
List every language, framework, library, and version detected. For each: 
state its purpose, and flag if it is outdated, deprecated, or has known CVEs. 
Cite exact file evidence.

PHASE 2 — ARCHITECTURE & DESIGN
Identify the architectural pattern (MVC, microservices, monolith, etc.). 
Evaluate: separation of concerns, coupling, cohesion, naming conventions, 
folder structure logic. Rate each  →  with reasoning.

PHASE 3 — ENVIRONMENT & CONFIGURATION
List every environment variable, config file, secret, API key reference, 
and hardcoded credential you detect. Flag: missing .env.example, secrets 
in version control, insecure defaults.

PHASE 4 — BUG CLASSES
Scan for these bug categories — for each finding, cite exact file+line, 
explain impact, rate confidence (High/Medium/Low), and give a short fix:
- Logic errors & off-by-one bugs
- Null/undefined dereferences
- Race conditions or async misuse
- Memory leaks or resource non-closure
- Incorrect error handling or swallowed exceptions
- Type mismatches or implicit coercions
- Infinite loops or recursion risks

PHASE 5 — SECURITY AUDIT
For each finding: state CWE ID if applicable, severity (Critical/High/Medium/Low), 
attack vector, and remediation. Check:
- Injection (SQL, NoSQL, command, LDAP)
- Authentication & session management weaknesses
- Broken access control (IDOR, privilege escalation)
- Sensitive data exposure
- XSS, CSRF, SSRF
- Insecure dependencies
- Improper error messages leaking internals

PHASE 6 — MISSING PARTS
What is incomplete, missing, or placeholder? List TODOs, stubs, unimplemented 
error handling, missing tests, missing docs.

PHASE 7 — FUTURE RISKS
Predict 5 technical debt risks that will become critical within 12 months if 
unaddressed. For each: explain why, estimate effort to fix now vs. later, and 
give a prevention strategy.

PHASE 8 — CODE INTERACTIONS
Map the data flow: how does data enter, transform, and exit the system? 
Identify any broken contracts between modules, inconsistent interfaces, or 
undocumented side effects.

CRITICAL RULES:
- NEVER report a finding without citing exact evidence (file, line, or code snippet).
- For every warning, state your confidence level (High / Medium / Low) and your reasoning.
- Do NOT list generic security advice not backed by evidence in THIS codebase.
- If something looks suspicious but you cannot confirm, say "Possible — verify manually" 
  and explain why.
- End with a PRIORITY ACTION LIST: top 10 items ordered by risk × effort.
```

---

## Dependency Security Audit

### When to Use
Use this for regular security audits of project dependencies.

### Why It Works
Forces CVE IDs (verifiable), separates known facts from inference, covers supply-chain — a frequently missed attack surface.

### The Prompt:

```
You are a DevSecOps engineer. Analyze [package.json / requirements.txt / 
Gemfile / pom.xml / go.mod — paste contents] and the environment configuration 
from [.env / config files — paste].

DEPENDENCY AUDIT
For each dependency:
- Current version vs latest stable version
- Any known CVEs (with CVE ID and severity)
- Is it actively maintained? (last commit date if you know it)
- Is it actually used or is it dead weight?
- Transitive risk: does it pull in vulnerable sub-dependencies?

ENVIRONMENT HYGIENE
- List every variable. Categorize: secret / config / feature-flag / infra
- Flag: missing variables that code references but are not defined
- Flag: variables with weak default values (e.g., DEBUG=true, SECRET=changeme)
- Flag: variables that should be secrets but are config (like DB URLs with credentials embedded)
- Recommend: minimum required vs optional variables for production

SUPPLY CHAIN RISK
- Any packages from non-official registries?
- Any packages with very low download counts or single-maintainer risk?
- Any packages that request excessive permissions?

Output format: table for dependencies, bullet list for env, risk matrix at end.
Do not list CVEs unless you are confident they exist. Mark uncertain entries 
as [Verify at nvd.nist.gov]
```

---

## Performance Analysis

### When to Use
Use this for performance optimization and bottleneck identification.

### The Prompt:

```
Analyze the performance of this code/system:

CODE/SYSTEM
[Paste code or describe system]

CURRENT PERFORMANCE
[Observed metrics: response time, throughput, resource usage]

EXPECTED PERFORMANCE
[Target metrics]

Provide:

1. BOTTLENECK IDENTIFICATION
   - Hot paths analysis
   - Resource contention points
   - Algorithmic complexity issues

2. PROFILING RECOMMENDATIONS
   - Tools to use
   - Metrics to collect
   - How to interpret results

3. OPTIMIZATION OPPORTUNITIES
   - Quick wins (low effort, high impact)
   - Medium-term improvements
   - Architectural changes

4. BENCHMARKING PLAN
   - How to measure before/after
   - Test scenarios
   - Success criteria
```

---

## Learning/Teaching Prompts

### The "Teach Me" Pattern

### When to Use
Use this when you want to understand a concept deeply, not just get working code.

### Why It Works
The step-by-step approach with common mistakes helps build true understanding.

### The Prompt:

```
Teach me how [technology/concept] works by building [concrete example] step by step.

For each step:
1. Show the code
2. Explain what it does and WHY this approach is used
3. Show a common mistake beginners make at this step
4. Then move to the next step

Start from [starting point] and end with [end goal].
```

### The "Explain Like I'm a Senior" Pattern

```
Explain how [complex topic] works. Assume I have 5+ years of programming 
experience but am new to this specific technology.

Include:
1. Core concepts and terminology
2. How it differs from [familiar alternative]
3. When to use it vs. when NOT to use it
4. Common pitfalls and how to avoid them
5. Best practices for production use
```

### The "Deep Dive" Pattern

```
I need: [functionality]

But I also want to understand. After writing the code, explain:

1. Architecture decisions: Why this approach over alternatives?
2. Key patterns: What design patterns are used and why?
3. Trade-offs: What was sacrificed and what was gained?
4. Scaling: How would this need to change at 10x scale?
5. Security: What attack vectors were considered?
6. Extensions: How would I add [likely future feature]?

Format:
- Code first (with comments)
- Then detailed explanation in sections
```

---

## Quick Research Checklists

### Before Making Technology Choices

- [ ] Requirements clearly defined
- [ ] At least 3 alternatives considered
- [ ] Sources verified (Tier 1/2)
- [ ] Information is recent (< 2 years)
- [ ] Conflicting information resolved
- [ ] Trade-offs explicitly stated
- [ ] Team expertise matches
- [ ] Long-term viability assessed

### Research Quality Checklist

| Criteria | Check |
|----------|-------|
| Sources cited | Every claim has a source |
| Source quality | Tier 1/2 preferred |
| Recency | Information is current |
| Conflicts addressed | Contradictions explained |
| Practical | Findings are actionable |
| Boundaries stated | Uncertainty acknowledged |

### Codebase Analysis Checklist

- [ ] All dependencies inventoried
- [ ] Security vulnerabilities identified
- [ ] Architecture pattern recognized
- [ ] Technical debt catalogued
- [ ] Missing tests documented
- [ ] Performance bottlenecks noted
- [ ] Priority action list created

---

## Research Output Templates

### Technology Comparison Output

```markdown
## Executive Summary
[One-paragraph recommendation]

## Comparison Matrix
| Criteria | Option A | Option B | Option C |
|----------|----------|----------|----------|
| Maturity | 4/5 | 5/5 | 3/5 |
| ... | ... | ... | ... |

## Recommendation
[Detailed rationale]

## Red Flags
- Option A: [concern]
- Option B: [concern]

## Migration Path
[If switching, how to do it]
```

### Security Audit Output

```markdown
## Summary
[X Critical, Y High, Z Medium, W Low severity findings]

## Critical Findings
| ID | Issue | Location | CWE | Fix |
|----|-------|----------|-----|-----|
| SEC-001 | SQL Injection | file.ts:42 | CWE-89 | Use parameterized queries |

## Dependency Risks
[Outdated/vulnerable packages]

## Action Items
[Prioritized list]
```


---

## PART 10: SEARCH & NAVIGATION

# 08 — Searching & Navigation Tools

> **The fastest way to understand a codebase is to find exactly what you're looking for — and to know what tool reaches for what question.**

---

## Table of Contents

1. [Category Overview](#category-overview)
2. [Comparison Matrix](#comparison-matrix)
3. [Text Search — ripgrep (Deep Dive)](#text-search--ripgrep-deep-dive)
4. [Interactive Navigation — fzf (Deep Dive)](#interactive-navigation--fzf-deep-dive)
5. [Structural Search — ast-grep & tree-sitter](#structural-search--ast-grep--tree-sitter)
6. [Code Intelligence — Sourcegraph & ctags](#code-intelligence--sourcegraph--ctags)
7. [Search Integration — Combining Search with Visualization](#search-integration--combining-search-with-visualization)
8. [Tool Deep-Dives](#tool-deep-dives)
9. [Search Workflow Recipes](#search-workflow-recipes)
10. [Best Practices — When to Use Which Tool](#best-practices--when-to-use-which-tool)

---

## Category Overview

Every developer, regardless of experience level, spends a significant portion of their day searching. Finding where a function is defined, locating all callers of an API, tracking down a TODO left three sprints ago, understanding the reach of a config key change, discovering every route that touches a database table — these are not edge cases; they are the daily fabric of software engineering.

Fast, precise code search is not a luxury. It is the difference between confidently refactoring and hesitantly guessing. It is the difference between understanding a monorepo in minutes versus days. Modern search and navigation tools have evolved dramatically beyond `grep`, and understanding the landscape — what each tool excels at, where they overlap, and how they compose — is one of the highest-leverage skills a developer can build.

This guide consolidates recommendations from multiple expert analyses (GPT toolkit, Nemotron toolkit, Opus toolkit) into a single, authoritative reference for choosing and using search and navigation tools effectively.

### Why Fast Code Search Matters

| Pain Point | Without Good Tools | With Good Tools |
|---|---|---|
| "Where is this function used?" | Manual file-by-file scanning | Instant cross-reference |
| "Find all TODOs in the codebase" | `grep -r "TODO" .` (slow, noisy) | `rg "TODO|FIXME" --type ts` (fast, scoped) |
| "Which files touch the `payment` module?" | Guessing from folder names | `rg "payment" -l \| fzf` |
| "Find all `if` statements missing error handling" | Reading every file | `ast-grep` pattern matching on AST |
| "Navigate a 50k-file monorepo" | Getting lost in directories | `fzf`, `ctags`, Sourcegraph |

---

## Comparison Matrix

The following matrix compares every search and navigation tool mentioned across all analyzed sources, organized by capability.

| Tool | Type | Speed | Language-Aware | Interactive | Best For |
|---|---|---|---|---|---|
| **ripgrep (rg)** | Text search | ⚡⭐⭐⭐⭐⭐ | Partial (file-type aware) | No (pipe-friendly) | Symbol lookup, string search, TODOs, config keys, routes, SQL, general "find X everywhere" |
| **fzf** | Fuzzy finder | ⚡⭐⭐⭐⭐⭐ | No (list-based) | **Yes** | Interactive file/command/result selection; pairs with ripgrep for instant search UI |
| **ast-grep** | Structural search | ⭐⭐⭐⭐ | **Yes** (AST-based) | No (CLI) | Syntax-aware search, refactoring, finding patterns like "all `if` without `else`", API misuse detection |
| **tree-sitter** | Parsing engine | ⭐⭐⭐⭐ | **Yes** (grammar-based) | No (library) | Foundation for structural tools; grammar definitions for 100+ languages |
| **ctags / universal-ctags** | Symbol indexer | ⭐⭐⭐⭐ | **Yes** (100+ languages) | No (tags file) | Instant jump-to-definition in editors (vim, Emacs, VS Code, Sublime) |
| **Sourcegraph** | Code intelligence platform | ⭐⭐⭐⭐ | **Yes** (cross-repo) | **Yes** (web UI) | Cross-references, definitions, call hierarchies, cross-repo search in large monorepos |
| **CodeSee + ripgrep** | Visual search integration | ⭐⭐⭐ | Partial (file-based) | **Yes** (visual) | Highlighting search results on architecture maps |

### Dimension Breakdown

- **Speed**: ripgrep and fzf are the fastest. Both are written in Rust and designed for near-instant results on projects of any size.
- **Language awareness**: ast-grep, tree-sitter, ctags, and Sourcegraph understand code structure. ripgrep and fzf work on raw text.
- **Interactivity**: fzf, Sourcegraph, and CodeSee provide interactive experiences. The rest are pipe-oriented CLI tools.

---

## Text Search — ripgrep (Deep Dive)

### What It Is

ripgrep (`rg`) is a line-oriented search tool that recursively searches directories for regex patterns. Written in Rust, it is the fastest general-purpose search tool available and respects `.gitignore` by default.

All three analyzed sources — GPT, Nemotron, and Opus — place ripgrep at the top of their recommendations. The Nemotron toolkit calls it "the single most-used tool in most developers' daily workflow." The GPT toolkit calls it "probably the single most useful codebase navigation tool outside your editor."

### Why Use It

- **Speed**: Orders of magnitude faster than `grep -r`, `ack`, or `ag` on large codebases.
- **.gitignore respect**: Automatically ignores files your project already ignores — no noise from `node_modules`, `.git`, `build/`, etc.
- **Binary file handling**: Automatically skips binary files unless you explicitly include them.
- **PCRE2 regex**: Full Perl-compatible regex support when needed (`-P` flag).
- **File-type filtering**: `--type ts`, `--type py`, `--type rs` to scope searches to specific languages.
- **Pipe-friendly**: Outputs clean paths and matches, perfect for piping into `fzf`, `xargs`, `sed`, or CodeSee.

### When to Use It

| Scenario | Command |
|---|---|
| Find every occurrence of a symbol | `rg "user_id"` |
| Find all TODOs and FIXMEs | `rg "TODO\|FIXME"` |
| Find all class definitions matching a pattern | `rg "class .*Service"` |
| Search only TypeScript files | `rg "payment" --type ts` |
| Find all route definitions | `rg "router\.(get\|post\|put\|delete)" --type ts` |
| Search for SQL queries touching a table | `rg "FROM users"` |
| Find config keys | `rg "DATABASE_URL"` |
| List files containing a pattern (no line content) | `rg -l "auth"` |
| Search with context (2 lines before/after) | `rg "error" -C 2` |
| Count matches per file | `rg -c "import"` |
| PCRE2 complex patterns | `rg -P "function\s+\w+\(.*callback.*\)"` |

### How to Do It Best

1. **Always let ripgrep use `.gitignore`** — don't fight it with `--no-ignore` unless you have a specific reason.
2. **Use `--type` filters** to narrow results. Searching "user" across 50k files is noisy; `rg "user" --type ts` is surgical.
3. **Use `-l` for file-level results** — perfect for piping into other tools (`rg -l "payment" | xargs dirname | sort -u`).
4. **Use `--sort path`** for deterministic output, essential for scripting.
5. **Use `-C` for context** when you need to understand surrounding code without opening the file.
6. **Use `--json` output** for programmatic consumption.
7. **Combine with `fzf`** for interactive exploration (see the fzf section below).
8. **Use `--glob` for custom includes/excludes** when `.gitignore` isn't enough: `rg "config" --glob "!*.test.ts"`.

---

## Interactive Navigation — fzf (Deep Dive)

### What It Is

fzf is a general-purpose command-line fuzzy finder. It takes any list of items — files, search results, git branches, process IDs, command history — and provides an interactive, real-time fuzzy filtering interface. Written in Go, it is blindingly fast.

### Why Use It

- **Transforms any list into an interactive UI** — pipe anything into fzf and get instant filtering.
- **Fuzzy matching** — you don't need exact matches; partial, out-of-order characters work.
- **Keyboard-driven** — full navigation, multi-select (`Tab`), and actions without leaving the keyboard.
- **Massive productivity gain** — the Nemotron toolkit and GPT toolkit both highlight it as a critical terminal workflow tool.
- **Universal composability** — pairs with ripgrep, git, docker, `ps`, `kill`, package managers, and more.

### When to Use It

| Scenario | Command |
|---|---|
| Fuzzy-find files in project | `fzf` |
| Interactive search of codebase content | `rg "payment" \| fzf` |
| Browse git branches | `git branch \| fzf` |
| Search command history | `history \| fzf` |
| Find and open a file in vim | `vim $(fzf)` |
| Kill a process interactively | `ps aux \| fzf \| awk '{print $2}' \| xargs kill` |
| Browse docker containers | `docker ps \| fzf` |
| Multi-select files for batch operation | `fzf -m` |
| Search with preview window | `fzf --preview 'bat {}'` |
| CD into a subdirectory | `cd $(find . -type d \| fzf)` |

### How to Do It Best

1. **Always pair with ripgrep for code search**: `rg --no-heading "pattern" | fzf` gives you the best of both worlds — ripgrep's speed and fzf's interactivity.
2. **Use `--preview`** for context: `rg -l "auth" | fzf --preview 'rg "auth" {} --context 3'` lets you see matches as you browse.
3. **Use `--bind` for custom keybindings** — e.g., `--bind 'enter:execute(vim {})'` to open selected files.
4. **Use `-m` for multi-select** when you need to operate on multiple files at once.
5. **Set up shell integration** — fzf provides key bindings for `Ctrl+R` (history), `Ctrl+T` (file picker), and `Alt+C` (cd) that transform your terminal experience.
6. **Use `--sort` and `--tac`** to control result ordering.
7. **Combine with `bat`** for syntax-highlighted previews: `fzf --preview 'bat --color=always {}'`.

---

## Structural Search — ast-grep & tree-sitter

### What It Is

**tree-sitter** is a parsing framework that generates concrete syntax trees (ASTs) for source code. It supports 100+ languages and is used as the underlying technology for modern code intelligence in editors and tools.

**ast-grep** is a CLI tool built on top of tree-sitter that enables structural code search and refactoring. Instead of searching for text patterns, you search for syntax patterns — the actual structure of code.

The GPT toolkit captures the key distinction: *"Text search is useful. Structural search is surgical."*

### Why Use It

- **Syntax-aware**: Understands the difference between a variable named `if` and an `if` statement.
- **Pattern-based**: Search for abstract patterns like "all functions with a callback as the last argument" or "all `if` statements without an `else` branch."
- **Refactoring support**: Can not only find but also transform code structures.
- **Multi-language**: tree-sitter grammars exist for 100+ languages.
- **No false positives from comments/strings**: Structural search knows what is code and what is not.

### When to Use It

| Scenario | Tool | Pattern / Command |
|---|---|---|
| Find all `if` statements without `else` | ast-grep | `ast-grep --pattern 'if ($A) { $$$B }' --lang ts` |
| Find all functions with callback as last arg | ast-grep | `ast-grep --pattern 'function $A($$$B, $C) { $$$D }'` |
| Find all `console.log` calls | ast-grep | `ast-grep --pattern 'console.log($$$A)' --lang ts` |
| Detect API misuse patterns | ast-grep | Custom patterns for specific anti-patterns |
| Find all async functions without await | ast-grep | Pattern matching on function bodies |
| Build custom code analysis | tree-sitter | Programmatic AST traversal in Rust/Node/Python |

### How to Do It Best

1. **Start with the `--pattern` DSL** — ast-grep's pattern language uses `$NAME` for wildcards and `$$$NAME` for multi-node wildcards. This is intuitive and powerful.
2. **Specify `--lang`** to ensure correct parsing: `ast-grep --pattern '...' --lang python`.
3. **Use `--rule`** with YAML rule files for complex, reusable search/refactoring rules.
4. **Use `--json` output** for integrating ast-grep results into scripts or CI pipelines.
5. **For custom analysis beyond ast-grep's DSL**, use tree-sitter directly — it provides programmatic AST access in Rust, Node.js, Python, and more.
6. **Use structural search when text search gives too many false positives** — if `rg "error"` returns 500 results and 400 are in comments or strings, ast-grep can find only the actual error-handling code.
7. **Combine with ripgrep for a two-pass approach** — use `rg` for broad initial search, then `ast-grep` for precise structural filtering.

---

## Code Intelligence — Sourcegraph & ctags

### Sourcegraph

#### What It Is

Sourcegraph is a web-based code intelligence and search platform. It provides code navigation, cross-references, and search across single repositories or entire fleets of repositories.

#### Why Use It

- **Cross-references**: Instantly see every file that imports, calls, or references a symbol.
- **Definitions**: Jump to where any symbol is defined, even across repository boundaries.
- **Call hierarchies**: Trace the complete call chain — callers and callees.
- **Cross-repo search**: Search across every repository in your organization simultaneously.
- **Very strong for large monorepos** — the GPT toolkit specifically recommends it for this use case.

#### When to Use It

| Scenario | Why Sourcegraph |
|---|---|
| "Where is this function used across all our repos?" | Cross-repo references |
| "What depends on this shared library?" | Dependency analysis |
| "Show me the complete call chain for this API endpoint" | Call hierarchies |
| "Find the definition of this interface" | Jump-to-definition across repos |
| "Search for a pattern across 200 repositories" | Unified search index |

#### How to Do It Best

1. **Use "Find References"** as your first action when landing on unfamiliar code — it instantly answers "what uses this?"
2. **Use the search query language** for advanced filtering: `repo:my-org/.* lang:typescript "PaymentService"`.
3. **Use code navigation in your browser** — Sourcegraph works as a browser extension for GitHub/GitLab, adding intelligence directly to PR reviews.
4. **For monorepo teams**, invest in a self-hosted Sourcegraph instance — the ROI on developer navigation time is significant.
5. **Use "Search-based code review"** — before merging, search for patterns that might be affected by your change.

### ctags / universal-ctags

#### What It Is

universal-ctags generates a tags index file that maps symbol names to their file locations. Editors (vim, Emacs, VS Code, Sublime) use this index to provide instant jump-to-definition.

#### Why Use It

- **Instant navigation**: Jump to any function, class, variable, or macro definition with a single keystroke.
- **100+ language support**: Covers virtually every language in active use.
- **Editor-agnostic**: The tags file format is universal — every major editor supports it.
- **Zero network dependency**: Works entirely offline, unlike Sourcegraph.
- **Fast**: Generating tags for even large projects takes seconds.

#### When to Use It

| Scenario | How |
|---|---|
| Jump to function definition in vim | `:tag functionName` or `Ctrl-]` |
| Auto-complete from project symbols | Editor reads tags file |
| Navigate classes in a Java project | `ctags -R --languages=Java .` |
| Generate tags for a specific language | `ctags -R --languages=Python .` |
| Update tags on file save | Editor plugin or `ctags -R` in a watch script |

#### How to Do It Best

1. **Generate tags recursively**: `ctags -R .` from project root.
2. **Filter by language** for faster indexing: `ctags -R --languages=TypeScript .`.
3. **Exclude test/build directories**: `ctags -R --exclude=node_modules --exclude=dist .`.
4. **Use `--fields=+l`** to include language of each tag.
5. **Integrate with your editor** — vim's `tagbar` plugin, VS Code's `ctags` extension, or Emacs's `etags` provide rich tag browsing UIs.
6. **Auto-regenerate on save** — most editor plugins can do this automatically.
7. **Use with `fzf`** for interactive tag browsing: `ctags -R . \| awk '{print \$1}' \| sort -u \| fzf`.

---

## Search Integration — Combining Search with Visualization

### ripgrep + CodeSee

The Opus toolkit identifies a powerful integration pattern: piping ripgrep results into CodeSee for visual, map-based code exploration.

#### How It Works

1. **Search with ripgrep**: `rg -l "auth.js"` finds all files related to authentication.
2. **Pipe into CodeSee**: `rg -l "auth.js" | codesee filter` highlights only auth-related nodes on the architecture map.
3. **Visual exploration**: Search results appear directly on CodeSee's dependency graph, letting you see how auth-related files connect to the rest of the system.

#### When to Use This Pattern

- **Understanding impact**: "If I change this auth module, what else is affected?" — search + visualization answers this immediately.
- **Onboarding**: New team members can search for a feature keyword and see its full architectural context.
- **Refactoring scope assessment**: Before refactoring, search for all related files and see their connections on the map.
- **Security audits**: Search for security-sensitive patterns and visualize their reach across the codebase.

### ripgrep + fzf + Editor

The most common and powerful integration pattern:

```bash
# Search code interactively, open result in vim
rg --no-heading "pattern" | fzf --bind 'enter:execute(vim {1} +{2})'

# Search with syntax-highlighted preview
rg -l "" | fzf --preview 'bat --color=always {}'

# Search with ripgrep, filter with fzf, preview with bat
rg --color=always --no-heading "pattern" | fzf --ansi --preview 'bat --color=always {1} --highlight-line {2}'
```

### ast-grep + CI Pipeline

Structural search results can feed into CI for automated code quality checks:

```bash
# Fail CI if console.log found in production code
ast-grep --pattern 'console.log($$$A)' --lang ts src/ && echo "PASS" || echo "FAIL: console.log found"

# Check for specific anti-patterns
ast-grep --rule no-var-rule.yaml --lang js src/
```

---

## Tool Deep-Dives

### ripgrep (`rg`)

| Attribute | Detail |
|---|---|
| **What** | Line-oriented recursive regex search tool |
| **Language** | Rust |
| **Speed** | Fastest text search tool available; benchmarked faster than grep, ack, ag |
| **Default behavior** | Respects `.gitignore`, skips binary files, searches hidden files only if explicitly told |
| **Regex engine** | Default DFA; PCRE2 available with `-P` |
| **Install** | `cargo install ripgrep`, `brew install ripgrep`, `apt install ripgrep`, `choco install ripgrep` |
| **Key flags** | `-l` (files only), `-c` (count), `-C N` (context), `--type`, `--glob`, `--json`, `-P` (PCRE2), `--no-heading` |
| **Weaknesses** | Not language-aware (can't distinguish code from comments); no interactive UI natively |

### fzf

| Attribute | Detail |
|---|---|
| **What** | General-purpose interactive fuzzy finder |
| **Language** | Go |
| **Speed** | Near-instant on lists of any size |
| **Input** | Any newline-separated list (from stdin, file, or built-in commands) |
| **Output** | Selected items to stdout |
| **Key features** | Fuzzy matching, multi-select (`-m`), preview (`--preview`), custom keybindings (`--bind`), shell integration |
| **Install** | `brew install fzf`, `apt install fzf`, `choco install fzf`, git clone from GitHub |
| **Weaknesses** | No understanding of code structure; only as good as the list you feed it |

### ast-grep (`sg`)

| Attribute | Detail |
|---|---|
| **What** | AST-based structural code search and refactoring tool |
| **Language** | Rust (built on tree-sitter) |
| **Speed** | Fast for structural search; slower than text search for simple patterns |
| **Pattern DSL** | `$NAME` for single-node wildcards, `$$$NAME` for multi-node wildcards |
| **Languages** | All tree-sitter supported languages (50+) |
| **Key flags** | `--pattern`, `--lang`, `--rule` (YAML), `--json`, `--rewrite` |
| **Install** | `cargo install ast-grep`, `npm install @ast-grep/cli`, `brew install ast-grep` |
| **Weaknesses** | Requires tree-sitter grammar for target language; pattern DSL has a learning curve; not ideal for simple text searches |

### tree-sitter

| Attribute | Detail |
|---|---|
| **What** | Incremental parsing system that generates concrete syntax trees |
| **Language** | C (runtime); grammars in JavaScript |
| **Purpose** | Foundation for code intelligence — used by ast-grep, neovim, Helix, GitHub, and more |
| **Languages** | 100+ grammar definitions |
| **Use as tool** | Typically used programmatically (Rust, Node.js, Python bindings) rather than directly as a CLI |
| **Key strength** | Incremental parsing — re-parses only changed portions, enabling real-time analysis in editors |
| **Install** | `npm install tree-sitter-cli`, `cargo install tree-sitter-cli` |

### Sourcegraph

| Attribute | Detail |
|---|---|
| **What** | Web-based code intelligence and search platform |
| **Deployment** | Cloud (sourcegraph.com) or self-hosted |
| **Key features** | Cross-references, definitions, call hierarchies, cross-repo search, code navigation in browser |
| **Languages** | All major languages |
| **Integration** | Browser extensions for GitHub/GitLab; VS Code extension; API |
| **Best for** | Large monorepos, multi-repo organizations, code review, cross-team dependency analysis |
| **Weaknesses** | Requires setup (self-hosted) or internet access (cloud); overkill for small projects |

### ctags / universal-ctags

| Attribute | Detail |
|---|---|
| **What** | Symbol indexing tool that generates a tags file for editor navigation |
| **Languages** | 100+ |
| **Editor support** | vim, Emacs, VS Code, Sublime Text, and virtually every code editor |
| **Speed** | Tags generation is fast; lookup is instant |
| **Key flags** | `-R` (recursive), `--languages=`, `--exclude=`, `--fields=+l`, `-o` (output file) |
| **Install** | `brew install universal-ctags`, `apt install universal-ctags` |
| **Weaknesses** | Static index — must regenerate when code changes; no cross-reference (only definitions, not usages); no interactive UI |

---

## Search Workflow Recipes

### Recipe 1: "Where is this used?" (Quick)

```bash
# Fast text-based usage search
rg "functionName" --type ts
```

### Recipe 2: "Where is this used?" (Thorough, with ctags)

```bash
# Generate tags, then find all references
ctags -R --languages=TypeScript .
rg "functionName" --type ts
# In vim: :tag functionName  (jumps to definition)
```

### Recipe 3: "Where is this used?" (Cross-repo, with Sourcegraph)

Use Sourcegraph's web UI or CLI to search across all repositories simultaneously. Navigate to the symbol and use "Find References."

### Recipe 4: Interactive Codebase Search

```bash
# Search everything, filter interactively, open in editor
rg --no-heading "" | fzf --bind 'enter:execute(vim {1} +{2})'
```

### Recipe 5: Find All TODOs and FIXMEs

```bash
# By language
rg "TODO|FIXME|HACK|XXX" --type ts
rg "TODO|FIXME|HACK|XXX" --type py

# With file names only (for a list)
rg -l "TODO|FIXME"
```

### Recipe 6: Audit Error Handling

```bash
# Text-based: find catch blocks
rg "catch" --type ts -C 3

# Structural: find try without catch
ast-grep --pattern 'try { $$$A }' --lang ts
```

### Recipe 7: Impact Analysis Before Refactoring

```bash
# Step 1: Find all files that mention the module
rg -l "UserService" --type ts

# Step 2: See connections on CodeSee map
rg -l "UserService" | codesee filter

# Step 3: Interactive exploration with fzf
rg --no-heading "UserService" | fzf --preview 'bat {1} --highlight-line {2}'
```

### Recipe 8: Find All API Endpoints

```bash
# Express-style routes
rg "router\.(get|post|put|delete|patch)" --type ts

# FastAPI-style routes
rg "@app\.(get|post|put|delete)" --type py

# Spring-style routes
rg "@(GetMapping|PostMapping|PutMapping|DeleteMapping)" --type java
```

### Recipe 9: Dead Code Detection

```bash
# Find exported functions with no imports (approximate)
# Step 1: List all exports
rg "export (function|const|class)" --type ts -o | awk '{print $3}' | sort -u > /tmp/exports.txt

# Step 2: Check each export for imports
while read name; do
  count=$(rg "import.*$name" --type ts -c 2>/dev/null || echo 0)
  echo "$name: $count imports"
done < /tmp/exports.txt | sort -t: -k2 -n | head -20
```

### Recipe 10: Security Pattern Search

```bash
# Find eval() calls
rg "\beval\(" --type ts --type js

# Find hardcoded secrets (common patterns)
rg -i "password\s*=\s*['\"]" --type ts --type py --type js

# Find SQL injection risks
rg "SELECT.*\+.*\breq\b" --type ts
```

### Recipe 11: Batch File Operations with fzf

```bash
# Multi-select files and open all in vim tabs
files=$(fzf -m)
vim -p $files

# Multi-select files and count lines
fzf -m | xargs wc -l

# Find and delete selected files
fzf -m | xargs rm -i
```

### Recipe 12: Git-Aware Search

```bash
# Search only files changed in the current branch vs main
rg "pattern" $(git diff --name-only main)

# Search only staged files
rg "pattern" $(git diff --name-only --cached)

# Search files modified in the last commit
rg "pattern" $(git diff --name-only HEAD~1 HEAD)
```

---

## Best Practices — When to Use Which Tool

### Decision Framework

```
What are you searching for?
│
├── A specific string, symbol, or regex pattern
│   ├── Need interactivity? → ripgrep | fzf
│   └── Need scripting/piping? → ripgrep alone
│
├── A code structure (if/else, function signatures, patterns)
│   ├── One-time search → ast-grep --pattern
│   └── Reusable rule → ast-grep --rule (YAML)
│
├── Jump to a definition
│   ├── In your editor → ctags (instant, offline)
│   └── Cross-repo → Sourcegraph
│
├── "What uses this?" / cross-references
│   ├── Single repo → ripgrep (fast) or ctags (if indexed)
│   └── Multi-repo → Sourcegraph
│
├── Visual/architectural context
│   └── ripgrep | CodeSee filter
│
└── Browse/explore interactively
    └── fzf (files, results, commands, history)
```

### Rules of Thumb

1. **Reach for ripgrep first**. It solves 80% of search tasks and is the fastest option. As the Nemotron toolkit states, it is "the single most-used tool in most developers' daily workflow."

2. **Add fzf when you need interactivity**. If you find yourself running the same ripgrep command multiple times with slight variations, pipe it through fzf.

3. **Use ast-grep when ripgrep gives false positives**. If text search returns matches in comments, strings, or unrelated contexts, switch to structural search. As the GPT toolkit says: "Text search is useful. Structural search is surgical."

4. **Use Sourcegraph for cross-repo questions**. If your code spans multiple repositories, Sourcegraph is the only tool that provides unified cross-reference intelligence.

5. **Use ctags for instant editor navigation**. It is lightweight, offline, and supported by every editor. Generate tags, set up your editor, and never manually search for a definition again.

6. **Use CodeSee for architectural understanding**. When you need to see how search results connect in the broader system, visual tools provide context that text results cannot.

7. **Combine tools for maximum power**. The real productivity multiplier is composition: ripgrep finds, fzf filters, ast-gref refines, ctags navigates, and Sourcegraph connects across boundaries. No single tool does everything; the best developers use them together.

### Common Mistakes to Avoid

- **Using `grep -r` instead of `rg`** — ripgrep is faster, smarter, and produces cleaner output. There is no reason to use raw `grep` for code search.
- **Ignoring `.gitignore`** — if you override ripgrep's default ignore behavior, you will get flooded with results from `node_modules`, build artifacts, and vendor directories.
- **Using ast-grep for simple text searches** — structural search has overhead. For finding a string like `"user_id"`, ripgrep is the right tool.
- **Not indexing with ctags** — if you are manually navigating to definitions in vim or Emacs, you are wasting time. Set up ctags.
- **Searching monorepos without Sourcegraph** — if your organization has 50+ repositories, cross-repo search with ripgrep (running 50 times) is painful. Sourcegraph indexes everything once.

---

## Summary

| Question | Tool |
|---|---|
| "Find this string/symbol everywhere" | **ripgrep** |
| "Let me interactively browse search results" | **ripgrep → fzf** |
| "Find all code matching this syntax pattern" | **ast-grep** |
| "Jump to this definition" | **ctags** |
| "What references this across all our repos?" | **Sourcegraph** |
| "Show me how these files connect architecturally" | **ripgrep → CodeSee** |
| "I need to understand code structure programmatically" | **tree-sitter** |
| "Let me interactively pick from any list" | **fzf** |

The ecosystem of search and navigation tools is one of the most mature and well-designed in the developer toolchain. Investing time in learning these tools — not just installing them, but internalizing their composition patterns — pays dividends every single day. The difference between a developer who types `grep -r` and a developer who types `rg --type ts | fzf --preview 'bat {}'` is not just speed; it is clarity, confidence, and the ability to ask questions of a codebase that would otherwise be unanswerable.


---

## PART 11: REACT PATTERNS

# React Patterns — Bug Examples & Fixes

## 🔷 CUSTOM HOOK PATTERN (Data Fetching)

```tsx
// ✅ GOLD STANDARD: Custom hook with all states handled
// VIP NOTE: This hook properly handles cancellation, error typing, and all 4 states.
function useAsync<T>(asyncFn: () => Promise<T>, deps: React.DependencyList) {
  const [state, setState] = useState<
    | { status: 'idle' }
    | { status: 'loading' }
    | { status: 'success'; data: T }
    | { status: 'error'; error: Error }
  >({ status: 'idle' });

  useEffect(() => {
    let cancelled = false;
    setState({ status: 'loading' });

    asyncFn()
      .then((data) => { if (!cancelled) setState({ status: 'success', data }); })
      .catch((error) => {
        if (!cancelled) setState({
          status: 'error',
          error: error instanceof Error ? error : new Error(String(error)),
        });
      });

    return () => { cancelled = true; };
    // Note: deps is intentionally spread here because callers control the dependency
    // array. In production, consider using a linter plugin that understands this pattern,
    // or switch to React Query / SWR which handles this out of the box.
    // eslint-disable-next-line react-hooks/exhaustive-deps -- caller controls deps
  }, deps);

  return state;
}

// Usage — TypeScript knows exact shape in each branch
function UserPage({ userId }: { userId: string }) {
  const state = useAsync(() => fetchUser(userId), [userId]);

  if (state.status === 'idle' || state.status === 'loading') return <Spinner />;
  if (state.status === 'error') return <ErrorMessage error={state.error} />;
  return <UserProfile user={state.data} />; // TypeScript: data is User
}
```

---

## 🔷 FRONTEND UI ENGINEERING PATTERNS

### Avoid the AI Aesthetic
AI-generated UI has recognizable patterns. Avoid all of them:

| AI Default | Why It Is a Problem | Production Quality |
|---|---|---|
| Purple/indigo everything | Models default to visually safe palettes | Use the project actual color palette |
| Excessive gradients | Gradients add visual noise | Flat or subtle gradients matching design system |
| Rounded everything (rounded-2xl) | Maximum rounding ignores hierarchy | Consistent border-radius from design system |
| Generic hero sections | Template-driven layout with no user need | Content-first layouts |
| Lorem ipsum-style copy | Placeholder text hides layout problems | Realistic placeholder content |
| Oversized padding everywhere | Equal padding destroys visual hierarchy | Consistent spacing scale |
| Stock card grids | Uniform grids ignore information priority | Purpose-driven layouts |
| Shadow-heavy design | Shadows compete with content | Subtle or no shadows unless specified |

### Container/Presentation Pattern
Separate data fetching from rendering:


### Skeleton Loading


---

## 🔷 FORM STATE PATTERN

```tsx
// ✅ CORRECT: useReducer for complex form state
type FormAction =
  | { type: 'SET_FIELD'; field: keyof FormData; value: string }
  | { type: 'SET_ERRORS'; errors: Partial<Record<keyof FormData, string>> }
  | { type: 'SUBMIT_START' }
  | { type: 'SUBMIT_SUCCESS' }
  | { type: 'SUBMIT_ERROR'; error: string };

interface FormState {
  data: { name: string; email: string; password: string };
  errors: Partial<Record<'name' | 'email' | 'password', string>>;
  isSubmitting: boolean;
  submitError: string | null;
}

function formReducer(state: FormState, action: FormAction): FormState {
  switch (action.type) {
    case 'SET_FIELD':
      return {
        ...state,
        data: { ...state.data, [action.field]: action.value },
        errors: { ...state.errors, [action.field]: undefined }, // clear error on change
      };
    case 'SET_ERRORS':
      return { ...state, errors: action.errors };
    case 'SUBMIT_START':
      return { ...state, isSubmitting: true, submitError: null };
    case 'SUBMIT_SUCCESS':
      return { ...state, isSubmitting: false };
    case 'SUBMIT_ERROR':
      return { ...state, isSubmitting: false, submitError: action.error };
    default:
      return state;
  }
}

function RegisterForm() {
  const [state, dispatch] = useReducer(formReducer, {
    data: { name: '', email: '', password: '' },
    errors: {},
    isSubmitting: false,
    submitError: null,
  });

  const handleSubmit = async (e: React.FormEvent) => {
    e.preventDefault();
    const errors = validateForm(state.data);
    if (Object.keys(errors).length > 0) {
      dispatch({ type: 'SET_ERRORS', errors });
      return;
    }
    dispatch({ type: 'SUBMIT_START' });
    try {
      await registerUser(state.data);
      dispatch({ type: 'SUBMIT_SUCCESS' });
    } catch (error) {
      dispatch({ type: 'SUBMIT_ERROR', error: String(error) });
    }
  };

  return (
    <form onSubmit={handleSubmit}>
      <input
        value={state.data.name}
        onChange={e => dispatch({ type: 'SET_FIELD', field: 'name', value: e.target.value })}
        aria-invalid={!!state.errors.name}
        aria-describedby={state.errors.name ? 'name-error' : undefined}
      />
      {state.errors.name && <span id="name-error" role="alert">{state.errors.name}</span>}
      {/* ... other fields */}
      <button type="submit" disabled={state.isSubmitting}>
        {state.isSubmitting ? 'Registering...' : 'Register'}
      </button>
      {state.submitError && <ErrorBanner message={state.submitError} />}
    </form>
  );
}
```

---

## 🔷 COMPOUND COMPONENT PATTERN

```tsx
// ✅ For complex UI components — avoids deep prop drilling within component family
interface TabsContextValue {
  activeTab: string;
  setActiveTab: (id: string) => void;
}

const TabsContext = createContext<TabsContextValue | null>(null);

function useTabs() {
  const ctx = useContext(TabsContext);
  if (!ctx) throw new Error('Tab components must be used within <Tabs>');
  return ctx;
}

function Tabs({ defaultTab, children }: { defaultTab: string; children: React.ReactNode }) {
  const [activeTab, setActiveTab] = useState(defaultTab);
  return (
    <TabsContext.Provider value={{ activeTab, setActiveTab }}>
      <div role="tablist">{children}</div>
    </TabsContext.Provider>
  );
}

function Tab({ id, label }: { id: string; label: string }) {
  const { activeTab, setActiveTab } = useTabs();
  return (
    <button
      role="tab"
      aria-selected={activeTab === id}
      onClick={() => setActiveTab(id)}
    >
      {label}
    </button>
  );
}

function TabPanel({ id, children }: { id: string; children: React.ReactNode }) {
  const { activeTab } = useTabs();
  if (activeTab !== id) return null;
  return <div role="tabpanel">{children}</div>;
}

// Usage — clean, composable, no prop drilling
<Tabs defaultTab="overview">
  <Tab id="overview" label="Overview" />
  <Tab id="settings" label="Settings" />
  <TabPanel id="overview"><Overview /></TabPanel>
  <TabPanel id="settings"><Settings /></TabPanel>
</Tabs>
```

---

## 🔷 ERROR BOUNDARY (Class Component Required)

```tsx
interface ErrorBoundaryState {
  hasError: boolean;
  error: Error | null;
}

class ErrorBoundary extends React.Component<
  { children: React.ReactNode; fallback?: React.ComponentType<{ error: Error; reset: () => void }> },
  ErrorBoundaryState
> {
  state: ErrorBoundaryState = { hasError: false, error: null };

  static getDerivedStateFromError(error: Error): ErrorBoundaryState {
    return { hasError: true, error };
  }

  componentDidCatch(error: Error, info: React.ErrorInfo) {
    logger.error('React error boundary caught error', {
      error: error.message,
      stack: error.stack,
      componentStack: info.componentStack,
    });
  }

  reset = () => this.setState({ hasError: false, error: null });

  render() {
    if (this.state.hasError && this.state.error) {
      const FallbackComponent = this.props.fallback ?? DefaultErrorFallback;
      return <FallbackComponent error={this.state.error} reset={this.reset} />;
    }
    return this.props.children;
  }
}

function DefaultErrorFallback({ error, reset }: { error: Error; reset: () => void }) {
  return (
    <div role="alert">
      <h2>Something went wrong</h2>
      <p>{error.message}</p>
      <button onClick={reset}>Try again</button>
    </div>
  );
}
```

---

## 🔷 DEBOUNCED VALUE HOOK

```tsx
function useDebouncedValue<T>(value: T, delay: number): T {
  const [debouncedValue, setDebouncedValue] = useState(value);

  useEffect(() => {
    const timer = setTimeout(() => setDebouncedValue(value), delay);
    return () => clearTimeout(timer);
  }, [value, delay]);

  return debouncedValue;
}

// Usage: Debounce search input
function SearchInput() {
  const [query, setQuery] = useState('');
  const [results, setResults] = useState<SearchResult[]>([]);
  const debouncedQuery = useDebouncedValue(query, 300);

  useEffect(() => {
    if (!debouncedQuery) { setResults([]); return; }
    const controller = new AbortController();
    searchApi(debouncedQuery, { signal: controller.signal })
      .then(setResults)
      .catch(err => { if (err.name !== 'AbortError') console.error(err); });
    return () => controller.abort();
  }, [debouncedQuery]);

  return <input value={query} onChange={e => setQuery(e.target.value)} />;
}
```

---

## 🔷 PREVIOUS VALUE HOOK

```tsx
function usePrevious<T>(value: T): T | undefined {
  const ref = useRef<T>();

  useEffect(() => {
    ref.current = value;
  }, [value]);

  return ref.current;
}

// Usage: Detect when value changes
function Component({ userId }: { userId: string }) {
  const prevUserId = usePrevious(userId);

  useEffect(() => {
    if (prevUserId !== userId) {
      console.log(`User ID changed from ${prevUserId} to ${userId}`);
    }
  }, [userId, prevUserId]);
}
```

---

## 🔷 INTERSECTION OBSERVER HOOK

```tsx
function useIntersectionObserver(
  ref: RefObject<HTMLElement>,
  options?: IntersectionObserverInit
): boolean {
  const [isIntersecting, setIsIntersecting] = useState(false);

  // ⚠️ VIP NOTE: If caller passes inline options object, this will re-create
  // the observer on every render. Callers should useMemo their options:
  //   const options = useMemo(() => ({ threshold: 0.1 }), []);
  useEffect(() => {
    const element = ref.current;
    if (!element) return;

    const observer = new IntersectionObserver(([entry]) => {
      setIsIntersecting(entry.isIntersecting);
    }, options);

    observer.observe(element);
    return () => observer.disconnect();
  }, [ref, options]);

  return isIntersecting;
}

// Usage: Lazy load when visible
function LazyImage({ src, alt }: { src: string; alt: string }) {
  const ref = useRef<HTMLDivElement>(null);
  const isVisible = useIntersectionObserver(ref, { threshold: 0.1 });

  return (
    <div ref={ref} style={{ minHeight: 200 }}>
      {isVisible ? <img src={src} alt={alt} /> : <Placeholder />}
    </div>
  );
}
```

---

## 🔷 WINDOW SIZE HOOK

```tsx
function useWindowSize() {
  const [size, setSize] = useState({ width: window.innerWidth, height: window.innerHeight });

  useEffect(() => {
    const handleResize = () => {
      setSize({ width: window.innerWidth, height: window.innerHeight });
    };

    window.addEventListener('resize', handleResize);
    return () => window.removeEventListener('resize', handleResize);
  }, []);

  return size;
}

// Usage: Responsive rendering
function Component() {
  const { width } = useWindowSize();
  const isMobile = width < 768;

  return isMobile ? <MobileLayout /> : <DesktopLayout />;
}
```

---

## 🔷 MEDIA QUERY HOOK (SSR-Safe)

```tsx
// ✅ SSR-safe: doesn't call window on server, uses matchMedia for efficiency
function useMediaQuery(query: string): boolean {
  const [matches, setMatches] = useState(() => {
    // SSR-safe: check if window exists
    if (typeof window === 'undefined') return false;
    return window.matchMedia(query).matches;
  });

  useEffect(() => {
    const mediaQuery = window.matchMedia(query);
    const handler = (event: MediaQueryListEvent) => setMatches(event.matches);
    
    // Set initial value
    setMatches(mediaQuery.matches);
    
    mediaQuery.addEventListener('change', handler);
    return () => mediaQuery.removeEventListener('change', handler);
  }, [query]);

  return matches;
}

// Usage:
function Component() {
  const isMobile = useMediaQuery('(max-width: 768px)');
  const prefersReducedMotion = useMediaQuery('(prefers-reduced-motion: reduce)');
  const isDarkMode = useMediaQuery('(prefers-color-scheme: dark)');
  
  return isMobile ? <MobileLayout /> : <DesktopLayout />;
}
```

> **VIP NOTE — useMediaQuery vs useWindowSize:**
> Prefer `useMediaQuery` over `useWindowSize` for responsive rendering.
> `matchMedia` is more performant (only fires on breakpoint changes),
> while `resize` fires continuously during drag (60+ times/second).

---

## 🔷 VIP EXPERT NOTE: REACT 19+ & SERVER COMPONENTS

```
Key patterns for modern React:

1. Server Components (default in Next.js App Router):
   - Components are server-rendered by default
   - Add 'use client' directive ONLY for components using hooks, event handlers, or browser APIs
   - Keep server components for data fetching, heavy computation

2. use() hook (React 19):
   - Replaces useEffect for data fetching in many cases
   - Works with Promises and Context
   - Integrates with Suspense boundaries

3. Form Actions (React 19):
   - Use action={} prop on <form> instead of onSubmit + e.preventDefault()
   - Server actions for form submissions that hit the server directly
   - useActionState() for form submission status

4. Key Decision Framework:
   ┌──────────────────────────────────────────────────┐
   │ Does it use useState, useEffect, onClick? │
   │   YES → 'use client' component              │
   │   NO  → Server component (default)           │
   │                                              │
   │ Does it fetch data?                          │
   │   Server Component → async/await directly    │
   │   Client Component → React Query / SWR       │
   └──────────────────────────────────────────────────┘
```

---

*This module provides React-specific patterns and best practices.*


---

## PART 12: PYTHON PATTERNS

# Python Patterns — Bug Examples & Fixes

> **VIP EXPERT NOTE:** Python's dynamic typing makes it *especially* vulnerable to
> runtime type errors that TypeScript would catch at compile time. Compensate with:
> type hints on every function, Pydantic/dataclass validation at boundaries,
> and mypy/pyright in strict mode in your CI pipeline.

## 🔷 MUTABLE DEFAULT ARGUMENTS (Classic Python Bug)

```python
# ❌ BROKEN: Default list is created ONCE at function definition
def add_item(item: str, items: list = []) -> list:
    items.append(item)
    return items

add_item("apple")   # ['apple']
add_item("banana")  # ['apple', 'banana'] ← BUG! Shares same list
add_item("cherry")  # ['apple', 'banana', 'cherry']

# ✅ CORRECT: Use None as sentinel, create new object each call
def add_item(item: str, items: list[str] | None = None) -> list[str]:
    if items is None:
        items = []
    items.append(item)
    return items
```

---

## 🔷 CONTEXT MANAGERS FOR RESOURCE SAFETY

```python
# ❌ BROKEN: Resource leak if exception occurs
def read_and_process(filepath: str) -> str:
    f = open(filepath)
    data = f.read()    # if this raises → file never closed
    result = process(data)
    f.close()
    return result

# ✅ CORRECT: Context manager guarantees cleanup
from pathlib import Path

def read_and_process(filepath: Path) -> str:
    with filepath.open(encoding='utf-8') as f:
        data = f.read()
    return process(data)

# Custom context manager for complex resources
from contextlib import contextmanager
from typing import Generator

@contextmanager
def get_db_connection(url: str) -> Generator[Connection, None, None]:
    conn = create_connection(url)
    try:
        yield conn
        conn.commit()
    except Exception:
        conn.rollback()
        raise
    finally:
        conn.close()  # ALWAYS runs

# Usage
with get_db_connection(DATABASE_URL) as conn:
    execute_query(conn, "INSERT INTO users ...")
```

---

## 🔷 DATACLASSES AND PYDANTIC FOR VALIDATED DATA

```python
# ❌ BROKEN: Raw dict — no validation, no type safety, no IDE support
def create_order(data: dict) -> dict:
    return {
        "user_id": data["user_id"],   # KeyError if missing
        "total": data["total"],        # no type validation
        "items": data.get("items", []),
    }

# ✅ CORRECT: Pydantic v2 model — validation at boundary
from pydantic import BaseModel, EmailStr, field_validator, Field
from decimal import Decimal
from uuid import UUID, uuid4

class OrderItem(BaseModel):
    product_id: UUID
    quantity: int = Field(gt=0, description="Must be positive")
    unit_price: Decimal = Field(ge=0)

    @property
    def subtotal(self) -> Decimal:
        return self.unit_price * self.quantity

class CreateOrderRequest(BaseModel):
    user_id: UUID
    items: list[OrderItem] = Field(min_length=1)
    shipping_address: str = Field(min_length=10)

    @field_validator('items')
    @classmethod
    def items_must_be_unique(cls, items: list[OrderItem]) -> list[OrderItem]:
        product_ids = [item.product_id for item in items]
        if len(product_ids) != len(set(product_ids)):
            raise ValueError('Duplicate product IDs in order')
        return items

    @property
    def total(self) -> Decimal:
        return sum(item.subtotal for item in self.items)

# FastAPI automatically validates and documents:
@app.post("/orders", response_model=OrderResponse)
async def create_order(request: CreateOrderRequest) -> OrderResponse:
    order = await order_service.create(request)
    return OrderResponse.from_order(order)

# VIP NOTE on Pydantic v1 vs v2:
#   v1: @validator('field')           → v2: @field_validator('field')
#   v1: class Config: ...             → v2: model_config = ConfigDict(...)
#   v1: .dict()                       → v2: .model_dump()
#   v1: .parse_obj(data)              → v2: .model_validate(data)
```

---

## 🔷 GENERATOR PATTERN FOR LARGE DATA PROCESSING

```python
# ❌ BROKEN: Loads entire dataset into memory
def get_all_records(db_url: str) -> list[dict]:
    conn = get_connection(db_url)
    return conn.execute("SELECT * FROM records").fetchall()  # 10M rows in memory!

def process_all():
    records = get_all_records(DATABASE_URL)  # OOM if large table
    for record in records:
        process(record)

# ✅ CORRECT: Generator — processes one at a time, O(1) memory
from typing import Generator, Iterator

def stream_records(
    db_url: str,
    batch_size: int = 1000,
) -> Iterator[dict]:
    conn = get_connection(db_url)
    offset = 0
    while True:
        batch = conn.execute(
            "SELECT * FROM records ORDER BY id LIMIT ? OFFSET ?",
            (batch_size, offset)
        ).fetchall()
        if not batch:
            break
        yield from batch
        offset += batch_size

def process_all():
    for record in stream_records(DATABASE_URL):
        process(record)  # only one record in memory at a time
```

---

## 🔷 EXCEPTION HANDLING BEST PRACTICES

```python
# ❌ BROKEN: Catches everything, loses information
def fetch_user(user_id: str) -> dict | None:
    try:
        return api_client.get(f"/users/{user_id}")
    except:  # catches SystemExit, KeyboardInterrupt, etc!
        return None

# ❌ ALSO BAD: Too broad, swallows bugs
def fetch_user(user_id: str) -> dict | None:
    try:
        return api_client.get(f"/users/{user_id}")
    except Exception:
        return None  # hides programming errors too

# ✅ CORRECT: Specific exceptions, preserve context
class UserNotFoundError(Exception):
    def __init__(self, user_id: str) -> None:
        super().__init__(f"User {user_id!r} not found")
        self.user_id = user_id

class ApiConnectionError(Exception):
    pass

def fetch_user(user_id: str) -> dict:
    """Fetch user by ID.
    
    Raises:
        UserNotFoundError: If user does not exist.
        ApiConnectionError: If the API is unreachable.
        ValueError: If user_id is empty.
    """
    if not user_id or not isinstance(user_id, str):
        raise ValueError(f"user_id must be a non-empty string, got {user_id!r}")
    
    try:
        response = api_client.get(f"/users/{user_id}")
    except requests.ConnectionError as exc:
        raise ApiConnectionError(f"Failed to reach API: {exc}") from exc
    
    if response.status_code == 404:
        raise UserNotFoundError(user_id)
    
    response.raise_for_status()  # raises for other 4xx/5xx
    return response.json()

# Caller handles specifically:
try:
    user = fetch_user(user_id)
except UserNotFoundError:
    return {"error": "User not found"}, 404
except ApiConnectionError as exc:
    logger.error("API unreachable", exc_info=exc)
    return {"error": "Service temporarily unavailable"}, 503
```

---

## 🔷 ASYNC PYTHON BEST PRACTICES

```python
# ✅ CORRECT: Async with proper error handling and concurrency
import asyncio
import aiohttp
from typing import NamedTuple

class FetchResult(NamedTuple):
    user_id: str
    data: dict | None
    error: str | None

async def fetch_user_async(
    session: aiohttp.ClientSession,
    user_id: str,
    timeout: float = 10.0,
) -> FetchResult:
    try:
        async with session.get(
            f"/users/{user_id}",
            timeout=aiohttp.ClientTimeout(total=timeout),
        ) as response:
            if response.status == 404:
                return FetchResult(user_id=user_id, data=None, error="not_found")
            response.raise_for_status()
            data = await response.json()
            return FetchResult(user_id=user_id, data=data, error=None)
    except asyncio.TimeoutError:
        return FetchResult(user_id=user_id, data=None, error="timeout")
    except aiohttp.ClientError as exc:
        return FetchResult(user_id=user_id, data=None, error=str(exc))

async def fetch_many_users(user_ids: list[str]) -> list[FetchResult]:
    async with aiohttp.ClientSession(base_url="https://api.example.com") as session:
        tasks = [fetch_user_async(session, uid) for uid in user_ids]
        return await asyncio.gather(*tasks)  # concurrent, not sequential
```

---

## 🔷 TYPE HINTS BEST PRACTICES

```python
from typing import TypeVar, Generic, Callable, Protocol
from collections.abc import Iterable

# Generic types
T = TypeVar('T')

class Repository(Generic[T]):
    def __init__(self, model_class: type[T]) -> None:
        self.model_class = model_class
    
    def find_by_id(self, id: int) -> T | None:
        ...

# Protocol for duck typing
class Drawable(Protocol):
    def draw(self) -> None: ...

def render(items: Iterable[Drawable]) -> None:
    for item in items:
        item.draw()

# Callable types
Handler = Callable[[Request], Response]

def register_handler(handler: Handler) -> None:
    ...

# Type aliases
JsonDict = dict[str, object]
UserId = int
UserMap = dict[UserId, 'User']
```

---

## 🔷 DECORATOR PATTERNS

```python
from functools import wraps
from typing import TypeVar, Callable, ParamSpec

P = ParamSpec('P')
R = TypeVar('R')

# Timing decorator
def timed(func: Callable[P, R]) -> Callable[P, R]:
    @wraps(func)
    def wrapper(*args: P.args, **kwargs: P.kwargs) -> R:
        start = time.perf_counter()
        result = func(*args, **kwargs)
        elapsed = time.perf_counter() - start
        logger.info(f"{func.__name__} took {elapsed:.3f}s")
        return result
    return wrapper

# Retry decorator
def retry(max_attempts: int = 3, delay: float = 1.0):
    def decorator(func: Callable[P, R]) -> Callable[P, R]:
        @wraps(func)
        def wrapper(*args: P.args, **kwargs: P.kwargs) -> R:
            last_error: Exception | None = None
            for attempt in range(max_attempts):
                try:
                    return func(*args, **kwargs)
                except Exception as e:
                    last_error = e
                    if attempt < max_attempts - 1:
                        time.sleep(delay * (2 ** attempt))  # exponential backoff
            raise last_error
        return wrapper
    return decorator

# Usage
@timed
@retry(max_attempts=3)
def fetch_data(url: str) -> dict:
    return requests.get(url).json()
```

---

## 🔷 DATA CLASS PATTERNS

```python
from dataclasses import dataclass, field, asdict
from datetime import datetime

@dataclass
class User:
    id: int
    name: str
    email: str
    created_at: datetime = field(default_factory=datetime.now)
    tags: list[str] = field(default_factory=list)
    
    def to_dict(self) -> dict:
        return asdict(self)
    
    @classmethod
    def from_dict(cls, data: dict) -> 'User':
        return cls(**data)

# Frozen dataclass for immutability
@dataclass(frozen=True)
class Point:
    x: float
    y: float
    
    def distance_to(self, other: 'Point') -> float:
        return ((self.x - other.x) ** 2 + (self.y - other.y) ** 2) ** 0.5
```

---

## 🔷 VIP EXPERT NOTE: PYTHON PROJECT STRUCTURE

```
my-project/
├── src/
│   └── my_project/
│       ├── __init__.py
│       ├── models/          # Pydantic/dataclass models
│       ├── services/        # Business logic
│       ├── repositories/    # Data access
│       ├── api/             # FastAPI routes or Flask blueprints
│       └── utils/           # Pure utility functions
├── tests/
│   ├── conftest.py      # Shared fixtures
│   ├── test_models.py
│   ├── test_services.py
│   └── test_api.py
├── pyproject.toml           # Modern Python project config (PEP 621)
├── .env.example             # Document required env vars
└── README.md

Key rules:
• Use pyproject.toml (not setup.py) for new projects
• Use src/ layout to prevent import confusion
• Co-locate tests with same naming: services/user.py → tests/test_user.py
• Pin dependencies in pyproject.toml or requirements.txt
```

---

## 🔷 VIP EXPERT NOTE: ASYNC CONTEXT MANAGERS

```python
# For async resources (DB connections, HTTP sessions, etc.)
from contextlib import asynccontextmanager
from typing import AsyncGenerator

@asynccontextmanager
async def get_db_session() -> AsyncGenerator[AsyncSession, None]:
    session = AsyncSession(engine)
    try:
        yield session
        await session.commit()
    except Exception:
        await session.rollback()
        raise
    finally:
        await session.close()

# Usage:
async def create_user(data: CreateUserInput) -> User:
    async with get_db_session() as session:
        user = User(**data.model_dump())
        session.add(user)
        # commit happens automatically on exit
        return user

# FastAPI lifespan pattern (replaces @app.on_event):
from contextlib import asynccontextmanager

@asynccontextmanager
async def lifespan(app: FastAPI):
    # Startup: initialize resources
    db_pool = await create_db_pool()
    redis = await connect_redis()
    app.state.db = db_pool
    app.state.redis = redis
    
    yield  # Application runs here
    
    # Shutdown: cleanup resources
    await db_pool.close()
    await redis.close()

app = FastAPI(lifespan=lifespan)
```

---

## 🔷 VIP EXPERT NOTE: TESTING PATTERNS FOR PYTHON

```python
# Golden rule: Use fixtures for setup, parametrize for variations, factories for data.

import pytest
from unittest.mock import AsyncMock, patch

# Async test support
@pytest.mark.asyncio
async def test_create_user_sends_welcome_email():
    mock_mailer = AsyncMock()
    service = UserService(mailer=mock_mailer)
    
    user = await service.create({"name": "Alice", "email": "alice@test.com"})
    
    mock_mailer.send.assert_called_once_with(
        to="alice@test.com",
        subject="Welcome!",
    )

# Testing exceptions with context
def test_negative_amount_raises_value_error():
    with pytest.raises(ValueError, match="Amount must be positive"):
        transfer_funds(from_id="a", to_id="b", amount=-100)

# Freezing time for deterministic tests
from freezegun import freeze_time

@freeze_time("2024-01-15 12:00:00")
def test_subscription_expires_after_30_days():
    sub = create_subscription()
    assert sub.expires_at == datetime(2024, 2, 14, 12, 0, 0)
```

---

*This module provides Python-specific patterns and best practices.*


---

## PART 13: TYPESCRIPT PATTERNS

# TypeScript Patterns — Type Safety & Common Bugs

> **VIP EXPERT NOTE:** TypeScript's type system is your most powerful bug prevention
> tool. 60% of runtime crashes in JavaScript apps are type-related errors that
> TypeScript catches at compile time — *if you use it correctly*. The patterns below
> show how to extract maximum safety from the type system.

## 🔷 DISCRIMINATED UNIONS (Most Powerful TypeScript Pattern)

```typescript
// ✅ GOLD STANDARD: Discriminated union — TypeScript narrows types automatically
type ApiResponse<T> =
  | { status: 'success'; data: T; requestId: string }
  | { status: 'error'; code: string; message: string; requestId: string }
  | { status: 'loading' };

function renderResponse<T>(response: ApiResponse<T>, render: (data: T) => React.ReactNode) {
  switch (response.status) {
    case 'loading':
      return <Spinner />;
    case 'error':
      return <ErrorBanner code={response.code} message={response.message} />;
      // TypeScript knows: response.data does NOT exist here
    case 'success':
      return render(response.data);
      // TypeScript knows: response.data is T here — no casting needed
  }
}

// Domain modeling with discriminated unions:
type PaymentMethod =
  | { type: 'credit_card'; last4: string; expiry: string; brand: 'visa' | 'mastercard' | 'amex' }
  | { type: 'paypal'; email: string }
  | { type: 'bank_transfer'; accountLast4: string; bankName: string }
  | { type: 'crypto'; address: string; currency: 'BTC' | 'ETH' | 'USDC' };

function getPaymentDisplayName(method: PaymentMethod): string {
  switch (method.type) {
    case 'credit_card': return `${method.brand} ****${method.last4}`;
    case 'paypal': return `PayPal (${method.email})`;
    case 'bank_transfer': return `${method.bankName} ****${method.accountLast4}`;
    case 'crypto': return `${method.currency} (${method.address.slice(0, 6)}...)`;
    default: {
      const _exhaustive: never = method;
      throw new Error(`Unknown payment method: ${JSON.stringify(_exhaustive)}`);
    }
  }
}
```

---

## 🔷 UTILITY TYPES (Use, Don't Reinvent)

```typescript
// ✅ Use built-in utility types instead of duplicating types

interface User {
  id: string;
  name: string;
  email: string;
  passwordHash: string;
  role: 'admin' | 'editor' | 'viewer';
  createdAt: Date;
  updatedAt: Date;
}

// For API responses (exclude sensitive fields):
type PublicUser = Omit<User, 'passwordHash'>;

// For update requests (all fields optional except id):
type UpdateUserInput = Partial<Omit<User, 'id' | 'createdAt' | 'updatedAt'>>;

// For create requests (no auto-generated fields):
type CreateUserInput = Omit<User, 'id' | 'createdAt' | 'updatedAt'>;

// Read-only version (prevents mutation):
type ImmutableUser = Readonly<User>;

// Pick specific fields:
type UserCredentials = Pick<User, 'email' | 'passwordHash'>;

// Record type for lookups:
type UserById = Record<string, User>;

// Extract data from generic types:
type ApiResponseData<T> = T extends ApiResponse<infer D> ? D : never;

// VIP NOTE: These are all BUILT-IN utility types. Don't reinvent them!
// TypeScript provides: Partial, Required, Readonly, Pick, Omit, Record,
// Exclude, Extract, NonNullable, ReturnType, Parameters, InstanceType,
// Awaited, and more. Check the docs before creating your own.
```

---

## 🔷 GENERIC CONSTRAINTS

```typescript
// ❌ BROKEN: Too loose — accepts anything
function getProperty(obj: any, key: string) {
  return obj[key]; // returns any
}

// ✅ CORRECT: Constrained generic — type-safe property access
function getProperty<T extends object, K extends keyof T>(obj: T, key: K): T[K] {
  return obj[key];
}

const user = { id: '1', name: 'Alice', age: 30 };
const name = getProperty(user, 'name');   // TypeScript: string
const age = getProperty(user, 'age');     // TypeScript: number
const bad = getProperty(user, 'email');  // TypeScript ERROR: 'email' not in User

// Generic repository pattern:
interface Repository<T extends { id: string }> {
  findById(id: string): Promise<T | null>;
  findMany(filter: Partial<T>): Promise<T[]>;
  create(data: Omit<T, 'id'>): Promise<T>;
  update(id: string, data: Partial<Omit<T, 'id'>>): Promise<T>;
  delete(id: string): Promise<void>;
}

class UserRepository implements Repository<User> {
  async findById(id: string): Promise<User | null> {
    return db.users.findUnique({ where: { id } });
  }
  // ... fully typed implementation
}
```

---

## 🔷 MAPPED TYPES FOR VALIDATION

```typescript
// ✅ Generate validation schemas from types automatically
type ValidationRule<T> = {
  required?: boolean;
  validator?: (value: T) => string | null; // null = valid, string = error message
};

// Mapped type: same keys as T, but each value is a ValidationRule
type ValidationSchema<T> = {
  [K in keyof T]?: ValidationRule<T[K]>;
};

function validate<T extends object>(
  data: T,
  schema: ValidationSchema<T>
): Record<keyof T, string | null> {
  const errors = {} as Record<keyof T, string | null>;

  for (const key in schema) {
    const rule = schema[key];
    const value = data[key];

    if (rule?.required && (value === null || value === undefined || value === '')) {
      errors[key] = `${String(key)} is required`;
      continue;
    }

    if (rule?.validator && value !== null && value !== undefined) {
      errors[key] = rule.validator(value);
    } else {
      errors[key] = null;
    }
  }

  return errors;
}

// Usage — fully typed, no magic strings
const schema: ValidationSchema<CreateUserInput> = {
  name: { required: true, validator: (v) => v.length > 100 ? 'Name too long' : null },
  email: { required: true, validator: (v) => v.includes('@') ? null : 'Invalid email' },
  password: { required: true, validator: (v) => v.length >= 8 ? null : 'Too short' },
};
```

---

## 🔷 TEMPLATE LITERAL TYPES

```typescript
// ✅ Type-safe string patterns
type HttpMethod = 'GET' | 'POST' | 'PUT' | 'PATCH' | 'DELETE';
type ApiVersion = 'v1' | 'v2';
type ApiEndpoint = `/${ApiVersion}/${string}`;

// Typed event names:
type UserEvent = `user:${'created' | 'updated' | 'deleted' | 'login' | 'logout'}`;
type OrderEvent = `order:${'placed' | 'shipped' | 'delivered' | 'cancelled'}`;
type AppEvent = UserEvent | OrderEvent;

function emit(event: AppEvent, payload: unknown): void {
  eventBus.emit(event, payload);
}

emit('user:created', { id: '1' });  // ✅ valid
emit('user:banned', { id: '1' });   // ✅ TypeScript ERROR

// CSS class name type safety:
type Breakpoint = 'sm' | 'md' | 'lg' | 'xl';
type SpacingValue = 1 | 2 | 4 | 8 | 16;
type TailwindPadding = `p-${SpacingValue}` | `p${Breakpoint}:p-${SpacingValue}`;
```

---

## 🔷 TYPE GUARDS AND NARROWING

```typescript
// ✅ Custom type guards for safe narrowing
function isUser(value: unknown): value is User {
  return (
    typeof value === 'object' &&
    value !== null &&
    'id' in value && typeof (value as any).id === 'string' &&
    'email' in value && typeof (value as any).email === 'string' &&
    'role' in value && ['admin', 'editor', 'viewer'].includes((value as any).role)
  );
}

// Use in API response parsing
async function fetchUser(id: string): Promise<User> {
  const response = await api.get(`/users/${id}`);
  const data = await response.json();

  if (!isUser(data)) {
    throw new TypeError(`API returned invalid user shape: ${JSON.stringify(data)}`);
  }

  return data; // TypeScript knows this is User
}

// Assertion function (throws instead of returning bool):
function assertIsUser(value: unknown): asserts value is User {
  if (!isUser(value)) {
    throw new TypeError(`Expected User, got: ${JSON.stringify(value)}`);
  }
}

// Usage
function processUser(data: unknown) {
  assertIsUser(data);
  // TypeScript knows data is User here
}
```

---

## 🔷 BRANDED TYPES FOR TYPE-SAFE IDs

```typescript
// ✅ Prevent mixing up IDs of different types
type Brand<T, B> = T & { __brand: B };

type UserId = Brand<string, 'UserId'>;
type OrderId = Brand<string, 'OrderId'>;
type ProductId = Brand<string, 'ProductId'>;

// Create branded IDs
function createUserId(id: string): UserId {
  return id as UserId;
}

// Now TypeScript prevents mixing
function getUser(id: UserId): User { /* ... */ }
function getOrder(id: OrderId): Order { /* ... */ }

const userId = createUserId('user-123');
const orderId = 'order-456' as OrderId;

getUser(userId);   // ✅ OK
getUser(orderId);  // ❌ TypeScript ERROR: OrderId not assignable to UserId
```

---

## 🔷 CONST ASSERTIONS

```typescript
// ✅ Lock down literal types with const assertion
const ROLES = ['admin', 'editor', 'viewer'] as const;
type Role = typeof ROLES[number]; // 'admin' | 'editor' | 'viewer'

const CONFIG = {
  apiUrl: 'https://api.example.com',
  timeout: 5000,
  retries: 3,
} as const;
// Type is { readonly apiUrl: "https://api.example.com"; readonly timeout: 5000; readonly retries: 3; }

// Instead of:
const CONFIG_BAD = {
  apiUrl: 'https://api.example.com',
  timeout: 5000,
  retries: 3,
};
// Type is { apiUrl: string; timeout: number; retries: number; }
```

---

## 🔷 SATISFIES OPERATOR (TypeScript 4.9+)

```typescript
// ✅ Ensure type matches while preserving literal types
type Routes = {
  home: '/';
  about: '/about';
  contact: '/contact';
};

const routes = {
  home: '/',
  about: '/about',
  contact: '/contact',
  blog: '/blog', // Error: 'blog' not in Routes
} satisfies Routes;

// routes.home is '/' not string
const home: '/' = routes.home; // ✅ OK
```

---

## 🔷 ZOD + TYPESCRIPT INTEGRATION (Runtime + Compile-Time Safety)

> **VIP EXPERT NOTE:** TypeScript types disappear at runtime. Zod gives you
> runtime validation that *generates* TypeScript types — single source of truth.

```typescript
import { z } from 'zod';

// Define schema ONCE — get both runtime validation AND TypeScript type
const UserSchema = z.object({
  id: z.string().uuid(),
  name: z.string().min(1).max(100),
  email: z.string().email(),
  role: z.enum(['admin', 'editor', 'viewer']),
  metadata: z.record(z.unknown()).optional(),
  createdAt: z.string().datetime(),
});

// Derive TypeScript type from schema (never goes out of sync!)
type User = z.infer<typeof UserSchema>;

// API handler with automatic validation:
async function handleCreateUser(req: Request): Promise<Response> {
  const result = UserSchema.safeParse(req.body);
  
  if (!result.success) {
    // Zod provides detailed, field-level error messages
    return Response.json(
      { errors: result.error.flatten().fieldErrors },
      { status: 422 }
    );
  }
  
  // result.data is fully typed as User — no casting needed
  const user = await db.users.create(result.data);
  return Response.json(user, { status: 201 });
}

// Transform + validate in one step:
const CreateUserSchema = UserSchema.omit({ id: true, createdAt: true }).extend({
  password: z.string().min(8).regex(/[A-Z]/, 'Must contain uppercase'),
});
type CreateUserInput = z.infer<typeof CreateUserSchema>;
```

---

## 🔷 VIP EXPERT NOTE: ERROR HANDLING WITH TYPE NARROWING

```typescript
// The typed error pattern — eliminates "error is unknown" frustration:

// Step 1: Define error hierarchy
class AppError extends Error {
  constructor(message: string, public readonly code: string) {
    super(message);
    this.name = this.constructor.name;
  }
}

class NotFoundError extends AppError {
  constructor(resource: string, id: string) {
    super(`${resource} ${id} not found`, 'NOT_FOUND');
  }
}

class ValidationError extends AppError {
  constructor(public readonly fields: Record<string, string>) {
    super('Validation failed', 'VALIDATION_ERROR');
  }
}

// Step 2: Use Result type instead of throwing
type Result<T, E extends Error = AppError> =
  | { success: true; data: T }
  | { success: false; error: E };

function ok<T>(data: T): Result<T, never> {
  return { success: true, data };
}

function fail<E extends Error>(error: E): Result<never, E> {
  return { success: false, error };
}

// Step 3: Use in functions
async function getUser(id: string): Promise<Result<User, NotFoundError>> {
  const user = await db.users.findById(id);
  if (!user) return fail(new NotFoundError('User', id));
  return ok(user);
}

// Step 4: Caller gets exhaustive type narrowing
const result = await getUser('123');
if (!result.success) {
  // TypeScript knows: result.error is NotFoundError
  console.log(result.error.code); // 'NOT_FOUND'
  return;
}
// TypeScript knows: result.data is User
console.log(result.data.name);
```

---

## 🔷 VIP EXPERT NOTE: MODERN TYPESCRIPT FEATURES (4.9+)

```typescript
// 1. satisfies operator (4.9) — type-check without widening
const routes = {
  home: '/',
  about: '/about',
} satisfies Record<string, string>;
// routes.home is '/' (literal), not string

// 2. const type parameters (5.0) — infer literal types
function createConfig<const T extends Record<string, unknown>>(config: T): T {
  return config;
}
const config = createConfig({ port: 3000, host: 'localhost' });
// config.port is 3000 (literal), not number

// 3. using keyword with Disposable (5.2) — automatic cleanup
class TempFile implements Disposable {
  constructor(public readonly path: string) {
    writeFileSync(path, '');
  }
  [Symbol.dispose](): void {
    unlinkSync(this.path);
  }
}

function processData() {
  using tmpFile = new TempFile('/tmp/data.tmp');
  // Use tmpFile...
  // Automatically cleaned up when scope exits (even on throw!)
}

// 4. NoInfer utility type (5.4) — prevent unwanted inference
function createEvent<T>(type: NoInfer<T>, handler: (data: T) => void): void {
  // T is not inferred from 'type' parameter — only from 'handler'
}
```

---

*This module provides TypeScript-specific patterns and best practices.*


---

## PART 14: PROPERTY TESTING TEMPLATES

```javascript
// test-helpers/property-test-patterns.js
// Property-based testing templates using fast-check
// Reference: https://fast-check.dev/docs/tutorials/quick-start/

import fc from 'fast-check';

// =============================================================================
// Template 1: "Function should never throw on valid inputs"
// =============================================================================
// Invariant: For all valid inputs generated by fast-check, calling the
// function does not throw an exception.
//
// How to adapt:
//   1. Replace `myFunction` with your actual function.
//   2. Replace `fc.string()` with the appropriate arbitrary for your domain
//      (e.g., fc.array(fc.integer()), fc.record({ ... }), fc.jsonValue()).
//   3. Add fc.pre(...) if you need to filter out certain generated values.
// =============================================================================

it('should never throw on valid string inputs', () => {
  fc.assert(
    fc.property(fc.string(), (input) => {
      // Example: call your function and assert it does not throw
      expect(() => myFunction(input)).not.toThrow();
    }),
    { numRuns: 1000 }
  );
});

// =============================================================================
// Template 2: "Output should maintain structural invariants"
// =============================================================================
// Invariant: The output of the function obeys a structural rule that can be
// checked independently of the implementation.
//
// Examples of structural invariants:
//   - An HTML sanitizer always returns balanced tags.
//   - A sort function returns an array of the same length as the input.
//   - A parser returns an object with specific required keys.
//
// How to adapt:
//   1. Replace `processData` with your actual data-transformation function.
//   2. Replace the arbitrary with the input type for your function.
//   3. Replace the invariant check (e.g., `result.length === input.length`)
//      with the rule that must hold for your domain.
// =============================================================================

it('should preserve array length after transformation', () => {
  fc.assert(
    fc.property(fc.array(fc.integer()), (input) => {
      const result = processData(input);
      // Structural invariant: output length equals input length
      expect(result).toHaveLength(input.length);
    }),
    { numRuns: 1000 }
  );
});

// =============================================================================
// Template 3: "Idempotency / Consistency"
// =============================================================================
// Invariant: Running the function twice yields the same result, OR applying
// a function and its inverse returns the original value, OR the operation is
// deterministic for the same input.
//
// Examples:
//   - normalizeText(normalizeText(x)) === normalizeText(x)
//   - JSON.parse(JSON.stringify(obj)) is deep-equal to obj
//   - encode(decode(x)) === x
//
// How to adapt:
//   1. Replace `normalize` with the function you want to test.
//   2. Choose the idempotency flavor that fits:
//      a) Twice-application: `f(f(x))` deep-equals `f(x)`
//      b) Inverse pair: `decode(encode(x))` equals `x`
//      c) Determinism: `f(x)` deep-equals `f(x)` when called twice
//   3. Replace the arbitrary with the correct input generator.
// =============================================================================

it('should be idempotent: normalize(normalize(x)) equals normalize(x)', () => {
  fc.assert(
    fc.property(fc.string(), (input) => {
      const once = normalize(input);
      const twice = normalize(once);
      // Idempotency invariant
      expect(twice).toEqual(once);
    }),
    { numRuns: 1000 }
  );
});

// =============================================================================
// Additional fast-check reference snippets
// =============================================================================

// Common arbitraries you can compose:
//   fc.string()               — arbitrary strings
//   fc.integer()              — arbitrary integers
//   fc.array(fc.integer())    — arbitrary arrays of integers
//   fc.oneof(fc.string(), fc.integer()) — arbitrary union type
//   fc.record({ name: fc.string(), age: fc.integer() }) — arbitrary objects
//   fc.jsonValue()            — arbitrary JSON-compatible values
//   fc.anything()             — arbitrary values of any type

// Shrinking: when fast-check finds a counterexample, it automatically tries
// to find the smallest/simplest input that still fails. You don't need to
// configure this; it is built into fc.assert().

// Verbose mode (useful for debugging a failing property):
//   fc.assert(fc.property(...), { verbose: 2 });

// Custom examples (always run these in addition to generated ones):
//   fc.assert(
//     fc.property(fc.string(), (s) => { ... }),
//     { examples: [['hello'], ['']] }
//   );

```

---

## PART 15: ERROR PREVENTION & OPERATIONS ARSENAL

# 15. ERROR SYMPTOM FAST DECODER — Universal Coding Edition

> **Purpose:** Given a symptom (error message, behavior), immediately know the root cause and fix. This is "ER triage" for code — no wandering, no guessing.

---

## 15.1 JavaScript / TypeScript Symptom Decoder

| Error / Symptom | Root Cause | Fix |
|----------------|------------|-----|
| `TypeError: Cannot read properties of null` | Variable is null when accessed | Add null check at source. Don't patch with `?.` — fix WHY it's null |
| `TypeError: X is not a function` | Import missing, wrong export, or calling non-function | Check import path. Verify default vs named export. Check if value is defined. |
| `ReferenceError: X is not defined` | Variable used before declaration or out of scope | Check spelling. Check if imported. Check if in the right scope. |
| `Unexpected token '<'` when importing JS | Server returns HTML instead of JS (wrong URL or 404) | Check the import path. Check dev server config. Check if file exists in build output. |
| `Module not found: Can't resolve 'X'` | Package not installed or wrong import path | Run `npm install X`. Check if path is relative (./X) vs package (X). |
| `Promise { <pending> }` in console | Missing `await` on async function call | Add `await` before the async call. Check if calling function is `async`. |
| `Hydration mismatch` (React/Next.js) | Server HTML differs from client render | Don't use `typeof window`, `Date.now()`, or `Math.random()` in initial render. Use `useEffect` for client-only code. |
| `Rendered more hooks than during previous render` | Hook called inside conditional or loop | Move ALL hooks to top level. Never `if (x) useEffect(...)`. |
| `Maximum update depth exceeded` | `setState` called during render, causing infinite loop | Move state update to `useEffect` or event handler. Never set state in render body. |
| `Each child in a list should have a unique "key"` | Missing or non-unique key prop | Add `key={item.id}`. Never use array index for dynamic lists. |
| `Objects are not valid as a React child` | Rendering object instead of string/JSX | Access specific property: `{obj.name}` not `{obj}`. Or use `JSON.stringify()`. |
| `Assignment to constant variable` | Reassigning a `const` variable | Use `let` if reassignment needed. Or use spread to create new object. |
| `ERR_REQUIRE_ESM` | Importing ESM package with `require()` | Switch to `import` syntax. Or add `"type": "module"` to package.json. |
| Build succeeds but page is blank | JS error thrown before render. No error boundary. | Check browser console. Add ErrorBoundary. Check that root component renders. |

## 15.2 Python Symptom Decoder

| Error / Symptom | Root Cause | Fix |
|----------------|------------|-----|
| `TypeError: 'NoneType' has no attribute 'X'` | Function returns None when you expect a value | Check function's return paths. Look for missing return statements. |
| `ImportError: cannot import name 'X' from 'Y'` | Function/class renamed or removed in newer version | Check package version: `pip show Y`. Read migration guide. |
| `AttributeError: 'dict' has no attribute 'X'` | Using attribute access on dict instead of subscript | Use `d['X']` or `d.get('X')`. Convert to dataclass/Pydantic model. |
| `RuntimeError: Event loop is already running` | `asyncio.run()` called inside an existing loop | Use `await` directly. In Jupyter, install `nest_asyncio`. |
| `RecursionError: maximum recursion depth exceeded` | Infinite recursion or deep data structure | Check base case. Increase `sys.setrecursionlimit()`. Or convert to iteration. |
| `UnicodeDecodeError: 'utf-8' codec can't decode` | File has different encoding (latin-1, windows-1252) | Detect encoding with `chardet`. Open with correct encoding. |
| `ModuleNotFoundError: No module named 'X'` | Package not installed in active virtualenv | Check `which python`. Activate venv. Run `pip install X`. |
| `pydantic.errors.PydanticUserError` | Using Pydantic v1 API with v2 installed | Migrate: `validator` → `field_validator`, `Config` → `model_config`. |
| `SyntaxError: f-string: unmatched '{'` | Literal `{` in f-string without escaping | Use `{{` for literal braces: `f"dict: {{'key': {value}}}"`. |
| `TypeError: X() got an unexpected keyword argument` | Function signature changed or args misspelled | Check function definition. Check if using correct version of library. |

## 15.3 React / Frontend Symptom Decoder

| Error / Symptom | Root Cause | Fix |
|----------------|------------|-----|
| Component renders but data is stale | Stale closure in useEffect/useCallback | Add ALL referenced variables to dependency array |
| Infinite re-render loop | Setting state unconditionally in useEffect or render | Add condition before setState. Check deps array. |
| Click handler fires twice | React 18 StrictMode double-invokes effects in dev | This is normal in dev. Ensure effects are idempotent. |
| Form input loses focus on every keystroke | Component re-creates input on each render | Move component definition outside render. Use stable keys. |
| CSS not applying to component | CSS specificity issue or module scoping | Check className prop. Check CSS module import. Inspect with DevTools. |
| API called twice on mount | React 18 StrictMode. Or missing cleanup in useEffect. | Add cleanup function. This is expected in dev (double mount). |
| useContext returns undefined | Provider not in component tree above consumer | Wrap the consuming component tree with the Provider. |
| `window is not defined` (Next.js) | Accessing browser API in Server Component | Use `'use client'` directive. Or check `typeof window !== 'undefined'`. |
| Images/assets not loading after build | Wrong path relative to build output | Use `import` for assets. Or put in `/public` and reference with `/filename`. |

## 15.4 Database / SQL Symptom Decoder

| Error / Symptom | Root Cause | Fix |
|----------------|------------|-----|
| `relation "X" does not exist` | Table not created or migration not run | Run pending migrations. Check schema name. |
| Query returns empty but data exists | Wrong WHERE clause, wrong schema, or case sensitivity | Check exact column values. Check if using correct database/schema. |
| `deadlock detected` | Two transactions lock each other's rows | Use consistent lock ordering. Reduce transaction scope. |
| Query suddenly slow (was fast) | Missing index, table grew, or stale query plan | Run `EXPLAIN ANALYZE`. Add index on WHERE/JOIN columns. |
| `duplicate key value violates unique constraint` | Inserting row with existing unique key | Use `ON CONFLICT` (Postgres) or `INSERT IGNORE` (MySQL). |
| Connection pool exhausted | Not releasing connections after use | Always use `try/finally` to release. Increase pool size. Check for leaks. |
| ORM generates N+1 queries | Lazy loading related entities in a loop | Use eager loading: `.include()` / `.joinedload()` / `.prefetch_related()`. |

---

## 15.5 FIX CONFIDENCE SCORECARD

**Before committing ANY fix, score it. Prevents shipping half-understood patches.**

```markdown
SCORE YOUR FIX (1-10 scale for each):

1. ROOT CAUSE CLARITY: Can you write ONE sentence explaining WHY the bug exists?
   1 = "Something is wrong" → 10 = "The fetchUser function returns undefined
   when the API returns 404 because the catch block swallows the error"

2. REPRODUCTION: Can you trigger the bug on demand?
   1 = "It happened once" → 10 = "Run this test: test_null_user_crash()"

3. MINIMALITY: Is this the SMALLEST possible fix?
   1 = "I rewrote the entire module" → 10 = "I changed one line"

4. TEST COVERAGE: Do you have a test that FAILS before and PASSES after?
   1 = "No test" → 10 = "Automated regression test included"

5. BLAST RADIUS: How much adjacent code could break?
   1 = "Changed a shared utility used everywhere" → 10 = "Changed one local variable"

6. ROLLBACK SAFETY: Can this be reverted without data loss?
   1 = "Changes database schema" → 10 = "Pure code change, easily revertible"

TOTAL: ___/60

Scoring guide:  →  : Ship with confidence  →  : Ship but monitor closely  →  : Get a code review first  →  : You probably don't understand the bug yet  →  : STOP. Go back to diagnosis.
```

---

## 15.6 EMERGENCY DEBUG RECIPES

**When you're stuck and need to move fast:**

### JavaScript / TypeScript Emergency

```bash
# 1. Find all usages of a function/variable
grep -rn "functionName" --include="*.ts" --include="*.tsx" .

# 2. Find where a value becomes null/undefined
# Add this temporarily at the suspect location:
console.trace('VALUE:', JSON.stringify(suspectValue));

# 3. Check what version of a package is actually installed
npm ls package-name
# or
node -e "console.log(require('package-name/package.json').version)"

# 4. Find circular dependencies
npx madge --circular src/

# 5. Check bundle size impact
npx bundlephobia package-name

# 6. Find unused exports
npx ts-unused-exports tsconfig.json
```

### Python Emergency

```bash
# 1. Find all usages of a function
grep -rn "function_name" --include="*.py" .

# 2. Check what version of a package
pip show package-name | grep Version

# 3. Find where an exception is being swallowed
grep -rn "except:" --include="*.py" .
grep -rn "except Exception" --include="*.py" .

# 4. Profile a slow function
python -m cProfile -s cumtime script.py

# 5. Find circular imports
python -c "import module_name" 2>&1 | grep -i circular

# 6. Memory profiling
pip install memory-profiler
python -m memory_profiler script.py
```

### React Emergency

```javascript
// 1. Find what's causing re-renders
// Add to any component:
import { useEffect, useRef } from 'react';
function useWhyDidYouRender(name, props) {
  const prev = useRef(props);
  useEffect(() => {
    const changes = {};
    Object.entries(props).forEach(([key, val]) => {
      if (prev.current[key] !== val) changes[key] = { from: prev.current[key], to: val };
    });
    if (Object.keys(changes).length) console.log(`[${name}] re-rendered:`, changes);
    prev.current = props;
  });
}

// 2. Debug useEffect dependency array
// Temporarily log deps to see what's changing:
useEffect(() => {
  console.log('Effect triggered. Deps:', { dep1, dep2, dep3 });
  // ... original effect
}, [dep1, dep2, dep3]);

// 3. Find memory leaks in components
// In Chrome DevTools → Memory → Heap Snapshot → take before and after
// Filter by "Detached" to find orphaned DOM nodes
```

### Database Emergency

```sql
-- 1. Find slow queries (PostgreSQL)
SELECT query, mean_exec_time, calls
FROM pg_stat_statements
ORDER BY mean_exec_time DESC
LIMIT 10;

-- 2. Find missing indexes (queries doing sequential scans)
SELECT relname, seq_scan, seq_tup_read
FROM pg_stat_user_tables
WHERE seq_scan > 1000
ORDER BY seq_tup_read DESC;

-- 3. Find blocking queries
SELECT blocked.pid, blocked.query, blocking.pid, blocking.query
FROM pg_stat_activity blocked
JOIN pg_locks bl ON bl.pid = blocked.pid
JOIN pg_locks bbl ON bbl.locktype = bl.locktype
JOIN pg_stat_activity blocking ON blocking.pid = bbl.pid
WHERE NOT bl.granted AND bbl.granted;

-- 4. Check table size
SELECT pg_size_pretty(pg_total_relation_size('table_name'));
```

---

## 15.7 DATABASE / ORM TRAP ENCYCLOPEDIA

```markdown
TRAP 1: N+1 Query Problem
  Symptom: Page loads slowly, DB shows 100+ queries for one page
  Cause: Lazy loading related entities in a loop
  Fix (SQLAlchemy): Use joinedload() or subqueryload():
    session.query(User).options(joinedload(User.posts)).all()
  Fix (Prisma): Use include:
    prisma.user.findMany({ include: { posts: true } })
  Fix (Django): Use select_related() / prefetch_related():
    User.objects.select_related('profile').prefetch_related('posts')

TRAP 2: Transactions Not Committed
  Symptom: Data saved in code but not visible in database
  Cause: Auto-commit off, missing commit() call
  Fix: Always use explicit transaction blocks with commit:
    with session.begin(): session.add(record)  # auto-commits

TRAP 3: Timezone-Naive Timestamps
  Symptom: Times are wrong by X hours, depending on server location
  Cause: Using datetime.now() instead of datetime.now(UTC)
  Fix: Store ALL timestamps as UTC. Convert to local in presentation layer.
    Column: TIMESTAMP WITH TIME ZONE (not WITHOUT)

TRAP 4: String-Based Queries
  Symptom: SQL injection vulnerability
  Cause: f"SELECT * FROM users WHERE id = {user_input}"
  Fix: ALWAYS use parameterized queries:
    cursor.execute("SELECT * FROM users WHERE id = %s", (user_input,))

TRAP 5: Connection Pool Exhaustion
  Symptom: "too many connections" error under load
  Cause: Creating new connection per request instead of pooling
  Fix: Use connection pooling (pgbouncer, SQLAlchemy pool, Prisma pool)
    Set pool_size appropriately (start with 10, increase based on load)

TRAP 6: Schema Migrations Not Idempotent
  Symptom: Migration fails on re-run with "already exists" error
  Cause: Migration assumes fresh state, no IF NOT EXISTS check
  Fix: Use IF NOT EXISTS / IF EXISTS in all DDL statements
    Or use migration tools (Alembic, Prisma Migrate) that track state

TRAP 7: Soft Delete vs Hard Delete Mismatch
  Symptom: "Deleted" records still appear in queries
  Cause: Soft delete sets is_deleted=true but queries don't filter
  Fix: Add default scope/filter: WHERE is_deleted = false on all queries
    Or use database views that pre-filter deleted records
```

---

## 15.8 CI/CD ERROR PREVENTION CHECKLIST

```markdown
BEFORE PUSHING TO CI:
□ All tests pass locally (not just the one you changed)
□ TypeScript/mypy compiles with zero errors
□ ESLint/pylint/ruff passes with zero warnings
□ No secrets in code or .env files committed
□ package-lock.json / poetry.lock is committed and up to date
□ Environment variables documented and present in CI config
□ Build works in production mode (npm run build / python -m build)
□ Database migrations are included and tested
□ API contracts haven't changed without updating consumers

COMMON CI FAILURES AND THEIR FIXES:
1. "Works locally, fails in CI"
   → Check: Node.js/Python version match? Same OS? Same env vars?
   → Fix: Pin exact versions in CI config. Use Docker for consistency.

2. "Test passes locally, flaky in CI"
   → Check: Timing-dependent? DB state? Network dependency?
   → Fix: Mock external services. Use fixed timestamps. Increase timeouts.

3. "Build succeeds but deploy fails"
   → Check: CORS config? DB connection string? SSL certificates?
   → Fix: Use staging environment that mirrors production exactly.

4. "'X' is not defined" only in CI
   → Check: Is it a dev dependency used in production build?
   → Fix: Move from devDependencies to dependencies, or fix import.

5. "Out of memory" in CI
   → Check: Running too many tests in parallel? Large test fixtures?
   → Fix: Increase CI memory. Run tests sequentially. Optimize fixtures.
```

---

*End of Part 15. This section is designed to be a quick-reference emergency toolkit — use it when standard debugging isn't finding the answer fast enough.*


---

## PART 16: SYSTEM DESIGN & ARCHITECTURE

# System Design & Architecture — Power Patterns for Scalable Systems

> **VIP EXPERT NOTE:** These patterns separate junior code from senior engineering. When building anything that serves more than one user, these concepts determine whether your system survives growth or collapses under it.

---

## 🔷 CAP THEOREM & SCALING FUNDAMENTALS

**CAP THEOREM:** In a distributed system, you can only guarantee 2 of 3:

```
  CONSISTENCY      AVAILABILITY    PARTITION TOLERANCE
  All nodes see    Every request   System works despite
  same data        gets response   network failures
```

NETWORKS ARE NOT RELIABLE → You **MUST** choose Partition Tolerance.  
Real choice: **CONSISTENCY vs AVAILABILITY**

**CP SYSTEMS** (Consistency + Partition Tolerance):
- Wait for response from partitioned node → might timeout
- Good for: Financial transactions, inventory, atomic operations
- Examples: HBase, etcd, PostgreSQL synchronous replication

**AP SYSTEMS** (Availability + Partition Tolerance):
- Return most readily available version (might be stale)
- Good for: Social media feeds, DNS, content delivery
- Examples: DynamoDB, Cassandra, CouchDB

**CONSISTENCY PATTERNS:**
- **Weak:** Real-time (VoIP, gaming) — may not see recent writes
- **Eventual:** DNS, email — will see it eventually (ms typically)
- **Strong:** Banking, inventory — immediate visibility

**SCALING:**
- **Performance problem:** Slow for a single user
- **Scalability problem:** Fast for one, slow under load

| Scaling Type | Pros | Cons |
|-------------|------|------|
| **Vertical** (scale up) | Simple, no code changes | Single point of failure, hardware limits, expensive |
| **Horizontal** (scale out) | Higher availability, infinite potential | Requires stateless design, more complex |

**STATELESS DESIGN CHECKLIST:**
- Servers do not store user sessions locally
- Sessions in centralized cache (Redis, Memcached)
- File uploads to object storage (S3, GCS)
- Any server can handle any request

---

## 🔷 CLEAN ARCHITECTURE

**LAYER STRUCTURE (Inner → Outer):**

```
LAYER 1: DOMAIN (Innermost)
  • Entities with rich behavior
  • Value objects (immutable)
  • Domain events
  • Business rules and invariants
  Dependencies: NONE (pure business logic)

LAYER 2: USE CASES / APPLICATION
  • Application services (orchestration)
  • DTOs for input/output
  • Transaction boundaries
  • No framework dependencies
  Dependencies: Domain Layer

LAYER 3: INTERFACE ADAPTERS
  • Controllers (HTTP handlers)
  • Presenters (response formatting)
  • Repository implementations
  • External service clients
  Dependencies: Use Cases, Domain

LAYER 4: FRAMEWORKS & DRIVERS (Outer)
  • Web frameworks (Express, FastAPI)
  • Database drivers (PostgreSQL, MongoDB)
  • External APIs
  • UI frameworks (React, Vue)
  Dependencies: All inner layers
```

**THE DEPENDENCY RULE:** Source code dependencies can only point **INWARD**. Inner layers know nothing about outer layers.

```typescript
// Layer 1: Domain
class Order extends AggregateRoot {
  public addItem(item: OrderItem): Result<void, DomainError> {
    if (this.props.status !== OrderStatus.PENDING) {
      return Err(DomainError.cannotModifyPlacedOrder());
    }
    this.props.items.push(item);
    return Ok(undefined);
  }
}

// Layer 2: Use Case
class CreateOrderUseCase {
  constructor(
    private orderRepo: OrderRepository,
    private eventBus: EventBus
  ) {}
  
  async execute(dto: CreateOrderDTO): Promise<Result<OrderDTO, Error>> {
    const order = Order.create({...});
    await this.orderRepo.save(order);
    await this.eventBus.publish(new OrderCreatedEvent(order));
    return Ok(OrderDTO.fromEntity(order));
  }
}

// Layer 3: Repository Interface
interface OrderRepository {
  findById(id: OrderId): Promise<Order | null>;
  save(order: Order): Promise<void>;
}

// Layer 4: Repository Implementation
class PostgresOrderRepository implements OrderRepository {
  constructor(private db: Knex) {}
  async findById(id: OrderId): Promise<Order | null> {
    const row = await this.db('orders').where('id', id.value).first();
    return row ? this.toDomain(row) : null;
  }
}
```

---

## 🔷 DATABASE SCALING

**SQL vs NoSQL:**

| Choose SQL When | Choose NoSQL When |
|-----------------|-------------------|
| ACID transactions required | Rapid horizontal scaling required |
| Complex relationships/joins | Unstructured/flexible schema |
| Strong consistency required | Massive read/write volumes |
| Complex aggregations | Eventual consistency acceptable |

**NoSQL TYPES:**
- **Key-Value:** Redis, DynamoDB — Sessions, caching
- **Document:** MongoDB, Firestore — Content, catalogs
- **Wide-Column:** Cassandra, Bigtable — Time-series, IoT
- **Graph:** Neo4j, Neptune — Social networks, recommendations

**REPLICATION:**
- **Master-Slave:** Master (R+W), Slaves (R only). Good for read scaling, backups.
- **Master-Master:** Both masters R+W. Conflict resolution needed. High complexity.

**SHARDING:**
- **Vertical (by feature):** Users DB, Orders DB, Products DB
- **Horizontal (by row):** User IDs A-M on Shard 1, N-Z on Shard 2

**SHARD KEY STRATEGIES:**
- **Hash-based:** Even distribution, hard to add shards
- **Range-based:** Good for range queries, hot spots possible
- **Geo-based:** Data locality, compliance (GDPR)

**INDEXING BEST PRACTICES:**
- ✓ Index columns used in WHERE, JOIN, ORDER BY
- ✓ Composite indexes: order matters (equality first, then range)
- ✓ Covering indexes: Include all queried columns
- ✗ Avoid indexes on: Low cardinality (boolean), frequently updated columns
- ✗ Remember: Writes become slower with more indexes

---

## 🔷 LOAD BALANCING & CACHING

**LOAD BALANCER TYPES:**
- **Layer 4 (Transport):** IP, Port (TCP/UDP). Faster, less resource intensive. Example: AWS NLB, HAProxy tcp mode.
- **Layer 7 (Application):** Headers, cookies, URL, content. Content-aware routing. Example: AWS ALB, NGINX, Traefik.

**ALGORITHMS:**
- **Round Robin:** Sequential distribution
- **Weighted Round Robin:** Some servers get more
- **Least Connections:** Route to least busy
- **Least Response Time:** Route to fastest
- **IP Hash:** Same client → same server (sessions)

**CACHING STRATEGIES:**

| Strategy | How It Works | Best For |
|----------|---------------|----------|
| **Cache-Aside** (Lazy Loading) | Check cache → miss → read DB → store in cache | Simple, cache only what is needed |
| **Write-Through** | Write to cache → cache writes to DB sync | Always consistent |
| **Write-Behind** (Write-Back) | Write to cache → async write to DB | Fast writes, batching possible |

**EVICTION POLICIES:**
- **LRU:** Least Recently Used (most common)
- **LFU:** Least Frequently Used
- **FIFO:** First In First Out
- **TTL:** Time To Live

**CDN:**
- **Push CDN:** You upload to CDN. Good for large files, videos, low traffic.
- **Pull CDN (Origin Pull):** CDN fetches on first request. Good for high traffic, frequently changing content.

---

## 🔷 MICROSERVICES & MESSAGING

**MICROSERVICES vs MONOLITH:**

| Aspect | Monolith | Microservices |
|--------|----------|---------------|
| Deploy | Single unit | Independent services |
| Codebase | Shared | Separate repos |
| Scale | Entire app | Individual services |
| Tech Stack | One | Multiple (polyglot) |
| Complexity | Lower | Higher |
| Debugging | Easier | Distributed tracing required |

**WHEN TO USE MICROSERVICES:**
- Large teams (Conway's Law)
- Different scaling needs per component
- Independent deployments required
- Clear service boundaries

**SERVICE DISCOVERY:**
- Services register themselves on startup
- Other services query registry to find dependencies
- Tools: Consul, etcd, Eureka, Kubernetes DNS

**API GATEWAY PATTERNS:**
- Request routing (/users → User Service)
- Load balancing
- Authentication/Authorization
- Rate limiting
- SSL termination
- Request/response transformation

**BACKEND FOR FRONTEND (BFF):**
- Separate gateway per client type
- Mobile: Compact responses
- Web: Full data with relations
- IoT: Optimized for low bandwidth

**MESSAGE QUEUES:**
- **Point-to-Point (Queue):** One message → One consumer. Work distribution.
- **Publish-Subscribe (Topic):** One message → Many subscribers. Broadcast.

**DELIVERY GUARANTEES:**
- **At-most-once:** May be lost, never duplicated (metrics)
- **At-least-once:** Always delivered, may duplicate (email)
- **Exactly-once:** Exactly one time (payments) — requires idempotency

---

## 🔷 CQRS & SAGA PATTERNS

**CQRS (Command Query Responsibility Segregation):**
- **Commands (Write):** Change state, validate, emit events
- **Queries (Read):** Optimized for reading, denormalized

**WRITE SIDE:**
- Domain model validation
- Business logic
- Events emitted on changes
- Transactional consistency

**READ SIDE:**
- Optimized views
- Denormalized data
- Fast queries (no joins)
- Eventually consistent

**EVENT SOURCING** (often paired with CQRS):
- Store events, not state
- State = fold(all events)
- Complete audit trail
- Can replay events

**SAGA PATTERN** (Distributed Transactions):
Problem: ACID transactions do not span microservices.
Solution: Saga = Sequence of local transactions. If one fails, run compensating transactions.

**Two Types:**
1. **CHOREOGRAPHY (Event-driven):** Services listen to each other's events
2. **ORCHESTRATION (Central coordinator):** Saga orchestrator directs each step

```typescript
class OrderSaga {
  async execute(orderData: CreateOrderInput) {
    const compensations: (() => Promise<void>)[] = [];
    
    try {
      const order = await orderService.create(orderData);
      compensations.push(() => orderService.cancel(order.id));
      
      const payment = await paymentService.charge(order.id, orderData.amount);
      compensations.push(() => paymentService.refund(payment.id));
      
      await inventoryService.reserve(order.items);
      compensations.push(() => inventoryService.release(order.items));
      
      await shippingService.schedule(order);
      
    } catch (error) {
      for (const compensate of compensations.reverse()) {
        try { await compensate(); }
        catch (compError) { logger.error('Compensation failed', compError); }
      }
      throw error;
    }
  }
}
```

---

## 🔷 SYSTEM DESIGN INTERVIEW FRAMEWORK

**4S FRAMEWORK:**
1. **SCOPE** (5-10 min): Requirements gathering
2. **SKETCH** (10-15 min): High-level design
3. **SCALE** (15-20 min): Deep dive & bottlenecks
4. **SOLIDIFY** (5-10 min): Edge cases & operations

**STEP 1: SCOPE — Gather Requirements**
- Functional: What features? Inputs/outputs? Who are the users?
- Non-Functional: Availability target? Latency? Throughput? Scale (DAU, data volume)?

**STEP 2: SKETCH — High-Level Design**
Components to consider:
- Client (Browser, Mobile)
- CDN (Static content)
- Load Balancer / API Gateway
- Application Servers
- Cache (Redis/Memcached)
- Database (Primary + Replicas)
- Message Queue (if async needed)
- Object Storage (files)

**STEP 3: SCALE — Deep Dive**
Identify bottlenecks:
- Database reads → Cache, Read replicas, CQRS
- Database writes → Sharding, Write-behind queue
- Single point of failure → Replication, Multi-AZ
- Slow queries → Indexing, Materialized views
- Traffic spikes → CDN, Auto-scaling, Rate limiting

**LATENCY NUMBERS TO KNOW:**
```
L1 cache reference:           0.5 ns
Main memory reference:      100 ns
SSD random read:             10 μs
Round trip within datacenter: 500 μs
Disk seek:                   10 ms
Round trip US West to East:  60 ms
Round trip US to Europe:    150 ms
```

---

*This module provides system design and architectural patterns for building scalable, production-grade systems.*


---

## PART 17: DEVOPS & DEPLOYMENT

# DevOps & Deployment — From Localhost to Production

> **VIP EXPERT NOTE:** Code that isn't deployed is inventory, not value. This section covers the full path from Dockerfile to running production cluster.

---

## 🔷 DOCKER & CONTAINERIZATION

**DOCKERFILE BEST PRACTICES:**

```dockerfile
# Build stage
FROM node:20-alpine AS builder
WORKDIR /app
COPY package*.json ./
RUN npm ci
COPY . .
RUN npm run build

# Production stage
FROM node:20-alpine
WORKDIR /app
RUN addgroup -g 1001 -S nodejs
RUN adduser -S nextjs -u 1001
COPY --from=builder --chown=nextjs:nodejs /app/dist ./dist
COPY --from=builder --chown=nextjs:nodejs /app/node_modules ./node_modules
COPY --chown=nextjs:nodejs package.json ./
USER nextjs
EXPOSE 3000
ENV NODE_ENV=production
CMD ["node", "dist/main.js"]
```

**SECURITY:**
- Use specific tags, never `latest`
- Use non-root user
- Scan for vulnerabilities (`trivy image myapp:latest`)
- Minimize layers
- Use `.dockerignore`

**DOCKER COMPOSE TEMPLATE:**

```yaml
version: '3.8'

services:
  app:
    build: .
    ports:
      - "3000:3000"
    environment:
      - NODE_ENV=production
      - DATABASE_URL=postgresql://db:5432/mydb
    depends_on:
      - db
      - redis
    networks:
      - backend
    restart: unless-stopped
    healthcheck:
      test: ["CMD", "curl", "-f", "http://localhost:3000/health"]
      interval: 30s
      timeout: 10s
      retries: 3
  
  db:
    image: postgres:15-alpine
    volumes:
      - postgres_data:/var/lib/postgresql/data
    environment:
      - POSTGRES_USER=myuser
      - POSTGRES_PASSWORD_FILE=/run/secrets/db_password
      - POSTGRES_DB=mydb
    secrets:
      - db_password
    networks:
      - backend
  
  redis:
    image: redis:7-alpine
    volumes:
      - redis_data:/data
    networks:
      - backend

volumes:
  postgres_data:
  redis_data:

networks:
  backend:
    driver: bridge

secrets:
  db_password:
    file: ./secrets/db_password.txt
```

**ESSENTIAL DOCKER COMMANDS:**
```bash
# Build & Run
docker build -t myapp:latest .
docker run -d -p 3000:3000 --name myapp myapp:latest

# Compose
docker-compose up -d
docker-compose down -v       # Remove volumes too
docker-compose logs -f

# Cleanup
docker system prune -f
docker volume prune -f
```

---

## 🔷 KUBERNETES

**DEPLOYMENT:**

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: myapp
  labels:
    app: myapp
spec:
  replicas: 3
  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxSurge: 1
      maxUnavailable: 0
  selector:
    matchLabels:
      app: myapp
  template:
    metadata:
      labels:
        app: myapp
    spec:
      containers:
      - name: myapp
        image: myapp:latest
        ports:
        - containerPort: 3000
        env:
        - name: DATABASE_URL
          valueFrom:
            secretKeyRef:
              name: db-secret
              key: url
        resources:
          requests:
            memory: "128Mi"
            cpu: "100m"
          limits:
            memory: "512Mi"
            cpu: "500m"
        livenessProbe:
          httpGet:
            path: /health
            port: 3000
          initialDelaySeconds: 30
          periodSeconds: 10
        readinessProbe:
          httpGet:
            path: /ready
            port: 3000
          initialDelaySeconds: 5
          periodSeconds: 5
```

**SERVICE & INGRESS:**

```yaml
apiVersion: v1
kind: Service
metadata:
  name: myapp-service
spec:
  type: ClusterIP
  selector:
    app: myapp
  ports:
  - port: 80
    targetPort: 3000
---
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: myapp-ingress
  annotations:
    nginx.ingress.kubernetes.io/rewrite-target: /
    cert-manager.io/cluster-issuer: "letsencrypt"
spec:
  tls:
  - hosts:
    - myapp.example.com
    secretName: myapp-tls
  rules:
  - host: myapp.example.com
    http:
      paths:
      - path: /
        pathType: Prefix
        backend:
          service:
            name: myapp-service
            port:
              number: 80
```

**KUBECTL COMMANDS:**
```bash
kubectl get pods -w              # Watch pods
kubectl logs mypod -f            # Follow logs
kubectl exec -it mypod -- /bin/sh # Shell into pod
kubectl apply -f k8s/            # Apply directory
kubectl scale deployment myapp --replicas=5
kubectl rollout status deployment/myapp
kubectl rollout undo deployment/myapp
kubectl port-forward pod/mypod 8080:3000
```

---

## 🔷 CI/CD PIPELINES

**GITHUB ACTIONS TEMPLATE:**

```yaml
name: CI/CD Pipeline

on:
  push:
    branches: [main, develop]
  pull_request:
    branches: [main]

jobs:
  test:
    runs-on: ubuntu-latest
    strategy:
      matrix:
        node-version: [18.x, 20.x]
    steps:
    - uses: actions/checkout@v4
    - uses: actions/setup-node@v4
      with:
        node-version: ${{ matrix.node-version }}
        cache: 'npm'
    - run: npm ci
    - run: npm run lint
    - run: npm run typecheck
    - run: npm test -- --coverage

  build:
    needs: test
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v4
    - name: Build Docker image
      run: docker build -t myapp:${{ github.sha }} .
    - name: Push to registry
      run: |
        echo ${{ secrets.DOCKER_PASSWORD }} | docker login -u ${{ secrets.DOCKER_USERNAME }} --password-stdin
        docker push myapp:${{ github.sha }}

  deploy-staging:
    needs: build
    runs-on: ubuntu-latest
    if: github.ref == 'refs/heads/develop'
    steps:
    - run: |
        kubectl set image deployment/myapp myapp=myapp:${{ github.sha }} -n staging
        kubectl rollout status deployment/myapp -n staging

  deploy-production:
    needs: build
    runs-on: ubuntu-latest
    if: github.ref == 'refs/heads/main'
    environment: production
    steps:
    - run: |
        kubectl set image deployment/myapp myapp=myapp:${{ github.sha }} -n production
        kubectl rollout status deployment/myapp -n production
```

**PIPELINE STRATEGIES:**
- **Trunk-Based:** Short-lived branches, frequent merges to main, feature flags
- **GitFlow:** main (production), develop (integration), feature/*, release/*, hotfix/*

**DEPLOYMENT STRATEGIES:**
- **Blue/Green:** Two identical environments, instant switchover, easy rollback
- **Canary:** Deploy to small subset, gradual rollout, monitor metrics
- **Rolling:** Replace instances one by one, no extra resources needed

---

## 🔷 INFRASTRUCTURE AS CODE

**TERRAFORM:**

```hcl
terraform {
  required_version = ">= 1.0"
  required_providers {
    aws = {
      source  = "hashicorp/aws"
      version = "~> 5.0"
    }
  }
  backend "s3" {
    bucket = "my-terraform-state"
    key    = "prod/terraform.tfstate"
    region = "us-east-1"
  }
}

provider "aws" {
  region = var.aws_region
}

module "vpc" {
  source = "terraform-aws-modules/vpc/aws"
  name   = "my-vpc"
  cidr   = "10.0.0.0/16"
  azs             = ["us-east-1a", "us-east-1b", "us-east-1c"]
  private_subnets = ["10.0.1.0/24", "10.0.2.0/24", "10.0.3.0/24"]
  public_subnets  = ["10.0.101.0/24", "10.0.102.0/24", "10.0.103.0/24"]
  enable_nat_gateway = true
}
```

**TERRAFORM WORKFLOW:**
```bash
terraform init
terraform plan -out=tfplan
terraform apply tfplan
terraform destroy
terraform fmt
terraform validate
```

**ANSIBLE PLAYBOOK EXAMPLE:**

```yaml
---
- name: Configure web servers
  hosts: webservers
  become: yes
  vars:
    app_version: "1.2.3"
  tasks:
    - name: Install dependencies
      apt:
        name: [nodejs, npm, nginx]
        state: present
    - name: Create app directory
      file:
        path: /opt/myapp
        state: directory
        owner: www-data
    - name: Deploy application
      copy:
        src: ./app/
        dest: /opt/myapp/
      notify: restart app
  handlers:
    - name: restart app
      systemd:
        name: myapp
        state: restarted
```

---

*This module provides DevOps, containerization, and deployment patterns for shipping code to production.*


---

## PART 18: SECURITY HARDENING

# Security Hardening — OWASP, Secrets, and Defense in Depth

> **VIP EXPERT NOTE:** Security is not a feature you add later. Every line of code is either secure or vulnerable — there is no neutral. Assume every input is malicious until proven otherwise.

---

## 🔷 SECURE CODING PRACTICES

**INPUT VALIDATION:**

```typescript
import { z } from 'zod';

const UserSchema = z.object({
  username: z.string().min(3).max(20).regex(/^[a-zA-Z0-9_]+$/),
  email: z.string().email(),
  age: z.number().min(13).max(120)
});

const validated = UserSchema.parse(userInput);
```

```python
from pydantic import BaseModel, field_validator
import re

class UserInput(BaseModel):
    username: str
    email: str
    age: int
    
    @field_validator('username')
    @classmethod
    def validate_username(cls, v):
        if not re.match(r'^[a-zA-Z0-9_]{3,20}$', v):
            raise ValueError('Invalid username')
        return v
```

**OUTPUT ENCODING:**

```javascript
// XSS PREVENTION
// NEVER:
element.innerHTML = userInput;

// SAFE:
element.textContent = userInput;
// OR with sanitization:
import DOMPurify from 'dompurify';
element.innerHTML = DOMPurify.sanitize(userInput);
```

```python
# SQL INJECTION PREVENTION
# NEVER:
query = f"SELECT * FROM users WHERE id = {user_id}"

# ALWAYS:
cursor.execute("SELECT * FROM users WHERE id = %s", (user_id,))
```

**AUTHENTICATION & AUTHORIZATION:**

```python
from passlib.context import CryptContext

pwd_context = CryptContext(schemes=["argon2"], deprecated="auto")

def hash_password(password: str) -> str:
    return pwd_context.hash(password)

def verify_password(password: str, hash: str) -> bool:
    return pwd_context.verify(password, hash)
```

**JWT BEST PRACTICES:**
- Short expiration (15-30 min)
- Refresh tokens for long sessions
- Store in httpOnly cookies
- Validate signature and issuer
- Include minimal claims

```typescript
import jwt from 'jsonwebtoken';

const token = jwt.sign(
  { userId: user.id, role: user.role },
  process.env.JWT_SECRET!,
  { expiresIn: '15m', issuer: 'myapp' }
);
```

---

## 🔷 OWASP TOP 10 (2021)

**A01: BROKEN ACCESS CONTROL**
- Vulnerabilities: IDOR, missing function-level access control, CORS misconfiguration
- Prevention:
  - Deny by default
  - Validate user permissions server-side
  - Use random UUIDs instead of sequential IDs
  - Implement proper CORS policies

```typescript
// BAD: Anyone can access any order
app.get('/orders/:id', (req, res) => {
  const order = db.orders.find(req.params.id);
  res.json(order);
});

// GOOD: Verify ownership
app.get('/orders/:id', authenticate, (req, res) => {
  const order = db.orders.find(req.params.id);
  if (order.userId !== req.user.id) {
    return res.status(403).json({ error: 'Forbidden' });
  }
  res.json(order);
});
```

**A02: CRYPTOGRAPHIC FAILURES**
- Weak encryption algorithms, hardcoded secrets, missing encryption in transit
- Prevention:
  - Use AES-256-GCM for encryption
  - Use TLS 1.3 for transport
  - Store secrets in vaults (not code)
  - Rotate keys regularly

**A03: INJECTION**
- Types: SQL, NoSQL, OS Command, LDAP
- Prevention:
  - Parameterized queries
  - Input validation
  - Use ORM/ODM
  - WAF (Web Application Firewall)

**A04: INSECURE DESIGN**
- Business logic flaws, missing security controls, insufficient threat modeling
- Prevention:
  - Security requirements in design
  - Threat modeling (STRIDE)
  - Defense in depth

**A05: SECURITY MISCONFIGURATION**
- Default credentials, unnecessary features, verbose error messages, missing security headers

```
Strict-Transport-Security: max-age=31536000; includeSubDomains
X-Content-Type-Options: nosniff
X-Frame-Options: DENY
Content-Security-Policy: default-src 'self'
Referrer-Policy: strict-origin-when-cross-origin
```

**A06: VULNERABLE COMPONENTS**
- Prevention:
  - Inventory all dependencies
  - Automated vulnerability scanning
  - Keep dependencies updated
  - Remove unused dependencies

**Tools:** `npm audit`, Snyk, Dependabot, OWASP Dependency-Check

**A07: AUTHENTICATION FAILURES**
- Prevention:
  - Multi-factor authentication
  - Strong password policies
  - Rate limiting on auth endpoints
  - Secure session management

**A08: SOFTWARE & DATA INTEGRITY FAILURES**
- Prevention:
  - Verify software supply chain
  - Code signing
  - Dependency verification
  - CI/CD pipeline security

**A09: SECURITY LOGGING FAILURES**
- **Log:** Authentication attempts, access control failures, input validation failures, system errors
- **NEVER Log:** Passwords, API keys, PII (unmasked), session tokens

**A10: SSRF (Server-Side Request Forgery)**
- Prevention:
  - Validate URLs
  - Deny access to internal networks
  - Use allowlists for domains
  - Disable unused URL schemas

---

## 🔷 SECRETS MANAGEMENT

**PRINCIPLES:**
- Never hardcode secrets
- Never commit secrets to git
- Use environment variables minimally
- Rotate secrets regularly
- Audit secret access

**DOCKER SECRETS:**
```yaml
services:
  app:
    secrets:
      - db_password
secrets:
  db_password:
    external: true
# Accessed in container at /run/secrets/db_password
```

**KUBERNETES SECRETS:**
```bash
kubectl create secret generic db-secret \
  --from-literal=username=admin \
  --from-literal=password='secret123'
```

```yaml
env:
  - name: DB_PASSWORD
    valueFrom:
      secretKeyRef:
        name: db-secret
        key: password
```

**HASHICORP VAULT:**
```bash
vault kv put secret/myapp/db \
  username=dbuser \
  password=dbpassword
```

**AWS SECRETS MANAGER:**
```python
import boto3
client = boto3.client('secretsmanager')
response = client.get_secret_value(SecretId='prod/myapp/db')
secret = json.loads(response['SecretString'])
```

**DOTENV BEST PRACTICES:**
- `.env.example` (committed) — documents required variables
- `.env` (gitignored) — actual secrets
- `.gitignore`: `.env`, `.env.local`, `*.pem`, `*.key`

**SCAN FOR SECRETS IN HISTORY:**
```bash
trufflehog git file://.
gitGuardian scan
```

---

*This module provides security hardening patterns for production-ready applications.*


---

## PART 19: AI AGENT PATTERNS

# AI Agent Patterns — ReAct, Planning, and Multi-Agent Systems

> **VIP EXPERT NOTE:** Modern coding assistants are not just autocomplete — they are agents that observe, reason, and act. These patterns show how to structure agent behavior for reliability and traceability.

---

## 🔷 AGENT ARCHITECTURE FUNDAMENTALS

**THE AGENT LOOP:**

```
   ┌─────────────┐    ┌─────────────┐    ┌─────────────┐    ┌─────────────┐
   │   OBSERVE   │───►│    THINK    │───►│    ACT      │───►│   LEARN     │
   │  (Sensors)  │    │  (Reason)   │    │  (Tools)    │    │  (Memory)   │
   └─────────────┘    └─────────────┘    └─────────────┘    └─────────────┘
          ▲                                                        │
          └────────────────────────────────────────────────────────┘
```

**AGENT COMPONENTS:**
1. **Perception:** Input parsing, context understanding, intent classification
2. **Reasoning:** Planning, decision making, pattern matching
3. **Action:** Tool selection, tool execution, output formatting
4. **Memory:** Short-term (conversation), long-term (preferences), episodic (experiences)
5. **Learning:** Feedback incorporation, pattern recognition, adaptation

**AGENT TYPES:**
- **Simple Reflex:** Input → Pattern Match → Action (no memory)
- **Model-Based:** Maintains world model, can plan ahead
- **Goal-Based:** Explicit goals, plans to achieve them
- **Utility-Based:** Considers trade-offs, optimizes outcomes
- **Learning:** Adapts over time based on feedback

---

## 🔷 REACT PATTERN (Reasoning + Acting)

**REACT CYCLE:**
Repeat until done:
1. **Thought:** Reason about current state and next action
2. **Action:** Execute tool/action
3. **Observation:** Process result
4. **[Repeat or Final Answer]**

**PSEUDOCODE:**
```python
while not done:
    thought = reason(current_context)
    if thought.requires_action:
        action = select_tool(thought)
        result = execute(action)
        observation = observe(result)
        update_context(observation)
    else:
        return thought.final_answer
```

**EXAMPLE: Code Debugging Agent**

```markdown
User: "Fix the authentication bug in login.py"

Thought 1: I need to examine the login.py file to understand the bug
Action 1: read_file("src/auth/login.py")
Observation 1: [file content shown...]

Thought 2: I see the issue — line 45 doesn't check if user is None before
           accessing user.password. I need to add a null check.
Action 2: edit_file("src/auth/login.py", line=45, new_code="if user and ...")
Observation 2: File updated successfully

Thought 3: Now I should verify the fix by running the tests
Action 3: run_command("pytest tests/auth/test_login.py -v")
Observation 3: 5 tests passed, 0 failed

Thought 4: All issues resolved. I can provide the final answer.
Action 4: [FINAL_ANSWER]

Final Answer: Fixed the null pointer bug in login.py line 45.
```

**TOOL SELECTION STRATEGY:**
- IF task involves file modification → `file_read` → analyze → `file_edit`/`file_write`
- IF task requires information → `search_web` OR read documentation
- IF task needs verification → `run_command` (tests, linting)
- IF task is code search → `search_code`

---

## 🔷 PLAN AND EXECUTE PATTERN

**PLAN → EXECUTE → VERIFY**

1. **PLAN:** Create step-by-step plan
2. **EXECUTE:** Follow plan, adapt as needed
3. **VERIFY:** Check results, retry if needed

**EXAMPLE PLAN:**
```markdown
## Plan: Create a user authentication system

### Step 1: Design database schema
- **Action:** Create users table migration
- **Depends on:** None
- **Verification:** Migration runs successfully

### Step 2: Create User model
- **Action:** Implement Pydantic/User model with validation
- **Depends on:** Step 1
- **Verification:** Model tests pass

### Step 3: Implement password hashing
- **Action:** Add argon2 hashing utility
- **Depends on:** None
- **Verification:** Hash/verify roundtrip test passes

### Step 4: Create registration endpoint
- **Action:** FastAPI/Express POST /register
- **Depends on:** Step 2, Step 3
- **Verification:** HTTP test returns 201

### Step 5: Create login endpoint with JWT
- **Action:** POST /login returning signed JWT
- **Depends on:** Step 2, Step 3
- **Verification:** Login test returns valid token
```

**REPLANNING TRIGGERS:**
- Step fails unexpectedly
- New requirements discovered
- Dependencies unavailable
- Better approach identified

---

## 🔷 MULTI-AGENT SYSTEMS

**AGENT ROLES:**

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                          COORDINATOR AGENT                                   │
│                        (Orchestrates workflow)                               │
└──────────────┬──────────────────┬──────────────────┬────────────────────────┘
               │                  │                  │
    ┌──────────▼────────┐ ┌───────▼────────┐ ┌──────▼─────────┐
    │   CODER AGENT     │ │  TESTER AGENT  │ │  REVIEW AGENT  │
    │ - Implementation  │ │ - Write tests  │ │ - Code review  │
    │ - Debugging       │ │ - Run tests    │ │ - Quality gate │
    └─────────┬─────────┘ └───────┬────────┘ └──────┬─────────┘
              │                   │                 │
              └───────────────────┴─────────────────┘
                                  │
                    ┌─────────────▼──────────────┐
                    │      DEPLOY AGENT          │
                    │   - Deploy to staging      │
                    │   - Smoke tests            │
                    │   - Production deploy      │
                    └────────────────────────────┘
```

**COMMUNICATION PATTERNS:**
- **Direct:** Fast, tight coupling, hard to scale
- **Broker/Mediator:** Loose coupling, scalable, single point of failure
- **Publish-Subscribe:** Decoupled, one-to-many, event-driven

**CONFLICT RESOLUTION:**
1. **Evidence-Based:** Data wins
2. **Voting:** Majority wins
3. **Hierarchy:** Senior agent decides
4. **Human Escalation:** Human makes final call

---

## 🔷 AGENT MEMORY SYSTEMS

**MEMORY TYPES:**
- **Short-Term (Working):** Current conversation, recent actions, active context (~7 items)
- **Long-Term (Persistent):** User preferences, past interactions, learned patterns
- **Episodic:** Specific past events, "what happened", timestamps, outcomes
- **Semantic:** Facts, concepts, relationships
- **Procedural:** How to do things, tool usage, patterns

**RETRIEVAL STRATEGIES:**
- **Recency:** Most recent items first (good for current task context)
- **Relevance (Vector Search):** Semantic similarity
- **Importance:** Marked critical items
- **Associative:** Linked concepts

**MEMORY PROMPT PATTERN:**
```markdown
You have access to the following memories:

[Relevant Memories Retrieved]
{memory_content}

[Current Context]
{current_task}

[Previous Actions This Session]
{action_history}

Use this information to inform your response, but focus on the current task.
```

---

*This module provides patterns for designing reliable AI agents and multi-agent workflows.*


---

## PART 20: FULL-STACK WEB APP BLUEPRINT

# Full-Stack Web App Blueprint — From Idea to Deployed Product

> **VIP EXPERT NOTE:** This section synthesizes everything into an actionable blueprint for building modern web applications. Use it when starting a new project or architecting a major feature.

---

## 🔷 VERTICAL SLICING STRATEGY

**Build in thin vertical slices — one complete user story end-to-end.**

**BAD (horizontal slicing):**
```
Task 1: Build entire database schema
Task 2: Build all API endpoints
Task 3: Build all UI components
Task 4: Connect everything
```
→ No working software until the very end.

**GOOD (vertical slicing):**
```
Task 1: User can create an account (schema + API + UI for registration)
Task 2: User can log in (auth schema + API + UI for login)
Task 3: User can create a task (task schema + API + UI for creation)
```
→ Each slice delivers working, testable functionality.

**TASK SIZING GUIDELINES:**

| Size | Files | Scope | Example |
|------|-------|-------|---------|
| **XS** | 1 | Single function or config change | Add a validation rule |
| **S** |  →  | One component or endpoint | Add a new API endpoint |
| **M** |  →  | One feature slice | User registration flow |
| **L** |  →  | Multi-component feature | Search with filtering and pagination |
| **XL** | 8+ | **Too large — break it down** | — |

---

## 🔷 DDD/CLEAN ARCHITECTURE PROJECT STRUCTURE

**TypeScript Full-Stack Example:**

```
my-app/
├── apps/
│   ├── web/                    # Next.js / React frontend
│   │   ├── src/
│   │   │   ├── app/            # Next.js App Router pages
│   │   │   ├── components/     # Reusable UI components
│   │   │   ├── hooks/          # Custom React hooks
│   │   │   ├── lib/            # API clients, utilities
│   │   │   └── types/          # Frontend-specific types
│   │   ├── public/
│   │   └── package.json
│   │
│   └── api/                    # FastAPI / Express backend
│       ├── src/
│       │   ├── domain/         # Entities, value objects, domain events
│       │   ├── application/    # Use cases, DTOs, services
│       │   ├── infrastructure/ # DB repos, external APIs, email
│       │   ├── interface/      # HTTP controllers, presenters
│       │   ├── config.py       # Settings, env vars
│       │   └── main.py         # App entry point
│       ├── tests/
│       ├── migrations/
│       └── pyproject.toml
│
├── packages/
│   ├── shared-types/           # Shared TS types (contracts)
│   ├── ui-kit/                 # Design system components
│   └── eslint-config/          # Shared lint rules
│
├── docker-compose.yml
├── terraform/
└── .github/
    └── workflows/
        └── ci.yml
```

**DEPENDENCY RULE:**
```
Frontend (apps/web) → Shared Types → API Contracts
Backend (apps/api)  → Domain → Application → Infrastructure
```

---

## 🔷 FULL-STACK FEATURE EXAMPLE: USER REGISTRATION

**Step 1: Shared Contract (packages/shared-types)**

```typescript
export const RegisterUserSchema = z.object({
  email: z.string().email(),
  password: z.string().min(8).regex(/[A-Z]/, 'Must contain uppercase'),
  name: z.string().min(1).max(100),
});

export type RegisterUserInput = z.infer<typeof RegisterUserSchema>;

export const RegisterUserResponseSchema = z.object({
  id: z.string().uuid(),
  email: z.string().email(),
  name: z.string(),
  createdAt: z.string().datetime(),
});

export type RegisterUserResponse = z.infer<typeof RegisterUserResponseSchema>;
```

**Step 2: Backend Domain (apps/api/src/domain)**

```python
from dataclasses import dataclass
from uuid import UUID, uuid4
from datetime import datetime

@dataclass(frozen=True)
class UserId:
    value: UUID

@dataclass
class User:
    id: UserId
    email: str
    name: str
    password_hash: str
    created_at: datetime

    @classmethod
    def create(cls, email: str, name: str, password_hash: str) -> "User":
        return cls(
            id=UserId(uuid4()),
            email=email,
            name=name,
            password_hash=password_hash,
            created_at=datetime.now(timezone.utc)
        )
```

**Step 3: Backend Use Case (apps/api/src/application)**

```python
from result import Result, Ok, Err

class DuplicateEmailError(Exception):
    pass

class RegisterUserUseCase:
    def __init__(self, user_repo: UserRepository, hasher: PasswordHasher):
        self.user_repo = user_repo
        self.hasher = hasher
    
    async def execute(self, dto: RegisterUserInput) -> Result[User, DuplicateEmailError]:
        existing = await self.user_repo.find_by_email(dto.email)
        if existing:
            return Err(DuplicateEmailError("Email already registered"))
        
        password_hash = self.hasher.hash(dto.password)
        user = User.create(dto.email, dto.name, password_hash)
        await self.user_repo.save(user)
        return Ok(user)
```

**Step 4: Backend Controller (apps/api/src/interface)**

```python
from fastapi import FastAPI, HTTPException
from shared_types import RegisterUserSchema, RegisterUserResponseSchema

app = FastAPI()

@app.post("/auth/register", response_model=RegisterUserResponseSchema)
async def register(data: RegisterUserSchema):
    result = await register_use_case.execute(data)
    
    if result.is_err():
        raise HTTPException(status_code=409, detail=str(result.error))
    
    user = result.value
    return {
        "id": str(user.id.value),
        "email": user.email,
        "name": user.name,
        "createdAt": user.created_at.isoformat(),
    }
```

**Step 5: Frontend Form (apps/web/src/app/register)**

```tsx
'use client';

import { useState } from 'react';
import { useRouter } from 'next/navigation';
import { RegisterUserSchema } from '@myapp/shared-types';

export default function RegisterPage() {
  const [errors, setErrors] = useState<Record<string, string>>({});
  const router = useRouter();

  async function handleSubmit(e: React.FormEvent<HTMLFormElement>) {
    e.preventDefault();
    const formData = new FormData(e.currentTarget);
    const raw = Object.fromEntries(formData);
    
    const parsed = RegisterUserSchema.safeParse(raw);
    if (!parsed.success) {
      const fieldErrors: Record<string, string> = {};
      parsed.error.errors.forEach(err => {
        if (err.path[0]) fieldErrors[err.path[0]] = err.message;
      });
      setErrors(fieldErrors);
      return;
    }
    
    const res = await fetch('/api/auth/register', {
      method: 'POST',
      headers: { 'Content-Type': 'application/json' },
      body: JSON.stringify(parsed.data),
    });
    
    if (res.status === 409) {
      setErrors({ email: 'Email already registered' });
      return;
    }
    
    if (!res.ok) {
      setErrors({ root: 'Something went wrong. Please try again.' });
      return;
    }
    
    router.push('/login');
  }

  return (
    <form onSubmit={handleSubmit}>
      <input name="name" placeholder="Name" required />
      {errors.name && <span className="error">{errors.name}</span>}
      
      <input name="email" type="email" placeholder="Email" required />
      {errors.email && <span className="error">{errors.email}</span>}
      
      <input name="password" type="password" placeholder="Password" required />
      {errors.password && <span className="error">{errors.password}</span>}
      
      {errors.root && <div className="error">{errors.root}</div>}
      
      <button type="submit">Register</button>
    </form>
  );
}
```

---

## 🔷 STAGED ROLLOUT & FEATURE FLAGS

**FEATURE FLAG STRATEGY:**
Ship behind feature flags to decouple deployment from release:

```typescript
const flags = await getFeatureFlags(userId);
if (flags.taskSharing) {
  return <TaskSharingPanel task={task} />;
}
return null;
```

**LIFECYCLE:**
1. DEPLOY with flag OFF → Code is in production but inactive
2. ENABLE for team/beta → Internal testing in production
3. GRADUAL ROLLOUT → 5% → 25% → 50% → 100%
4. MONITOR at each stage
5. CLEAN UP → Remove flag within 2 weeks of full rollout

**STAGED ROLLOUT DECISION THRESHOLDS:**

| Metric | Advance (green) | Hold (yellow) | Roll back (red) |
|--------|-----------------|---------------|-----------------|
| Error rate | Within 10% of baseline |  →  % above baseline | >2x baseline |
| P95 latency | Within 20% of baseline |  →  % above baseline | >50% above baseline |
| Client JS errors | No new error types | New errors at <0.1% of sessions | New errors at >0.1% of sessions |
| Business metrics | Neutral or positive | Decline <5% | Decline >5% |

**ROLLBACK PLAN TEMPLATE:**
```markdown
## Rollback Plan

### Trigger Conditions
- Error rate > 2x baseline
- P95 latency > [X]ms

### Steps
1. Disable feature flag (if applicable) OR deploy previous version
2. Verify rollback: health check, error monitoring
3. Communicate to team

### Time to Rollback
- Feature flag: < 1 minute
- Redeploy previous version: < 5 minutes
```

---

## 🔷 PRODUCTION READINESS CHECKLIST

Before declaring a web app feature complete:

```markdown
□ All inputs validated / guarded (frontend + backend)
□ All error paths handled explicitly
□ All async operations wrapped in try/catch
□ All TypeScript types explicit (no implicit any)
□ No forbidden patterns present
□ Function length ≤ 40 lines
□ File length ≤ 300 lines
□ Tests exist (unit + integration minimum)
□ API contracts documented or shared
□ Database migrations included and reversible
□ Feature works in production build (not just dev)
□ No secrets in code
□ Security headers configured
□ CORS properly restricted
□ Rate limiting considered
□ Logging and observability in place
□ Feature flag added (for significant changes)
□ Rollback plan documented
```

---

*This module provides the end-to-end blueprint for building, shipping, and operating modern full-stack web applications.*

---

## APPENDIX A: PERFORMANCE & OPTIMIZATION ESSENTIALS

> Apply when optimizing code, investigating slowness, or designing for scale. Complements Part 16 (System Design).

### A.1 Profiling & Measurement
**Rule: Measure first, optimize second.**

**Python:**
- `cProfile` for CPU profiling
- `line_profiler` for line-by-line analysis
- `memory_profiler` for heap analysis
- `py-spy` for sampling profiler (no code changes)

**Node.js:**
- `node --prof` built-in profiler
- `clinic.js` (doctor, bubbleprof, flame)
- `0x` for flame graphs

**Interpreting Flame Graphs:**
- Width = Time spent in function
- Y-axis = Call stack depth
- X-axis = Alphabetical order
- Hot paths = Wide towers

### A.2 Algorithm & Data Structure Optimization
| Complexity | Name | Example |
|---|---|---|
| O(1) | Constant | Hash lookup |
| O(log n) | Logarithmic | Binary search |
| O(n) | Linear | Single loop |
| O(n log n) | Linearithmic | Efficient sort |
| O(n²) | Quadratic | Nested loops (avoid) |

**Example — Optimize Lookup:**
```python
# O(n) - Linear search
def find_user(users, user_id):
    for user in users:
        if user.id == user_id:
            return user

# O(1) - Hash lookup
user_map = {user.id: user for user in users}
def find_user(user_id):
    return user_map.get(user_id)
```

### A.3 Database Query Optimization
- **Index** WHERE clause columns, JOIN columns, ORDER BY columns
- **Avoid N+1 queries** — use `select_related` / `join` / eager loading
- **SELECT only needed columns**
- **Use `EXPLAIN ANALYZE`** before deploying new queries
- **Connection pooling** is mandatory for production

### A.4 Caching Strategies
**Cache Hierarchy:**
- L1: In-memory (application cache)
- L2: Redis/Memcached (distributed cache)
- L3: CDN (edge cache)

**Patterns:**
- **Cache-Aside:** Check cache → miss → query DB → store in cache
- **Write-Through:** Update cache and DB simultaneously
- **Cache Warming:** Pre-populate hot keys on startup/deploy

### A.5 Frontend Performance (Core Web Vitals)
| Metric | Target | What It Measures |
|---|---|---|
| LCP | < 2.5s | Largest Contentful Paint |
| INP | < 200ms | Interaction to Next Paint |
| CLS | < 0.1 | Cumulative Layout Shift |
| TTFB | < 600ms | Time to First Byte |

**Quick Wins:**
- Lazy load images and non-critical components
- Code-split routes
- Preload critical fonts
- Minimize main-thread work
- Debounce/throttle frequent events

### A.6 Load Testing Essentials
**Tools:** k6, Artillery, Locust

**k6 Example:**
```javascript
export const options = {
  stages: [
    { duration: '2m', target: 100 },
    { duration: '5m', target: 100 },
    { duration: '2m', target: 0 },
  ],
  thresholds: {
    http_req_duration: ['p(95)<500'],
    http_req_failed: ['rate<0.1'],
  },
};
```

**Test Types:**
- **Smoke:** Minimal load, verify system works
- **Load:** Expected production load, validate SLAs
- **Stress:** Beyond capacity, find breaking point
- **Spike:** Sudden increase, test auto-scaling
- **Soak:** Extended period, find memory leaks

---

## APPENDIX B: GIT, COLLABORATION & CODE REVIEW STANDARDS

> Apply to every PR, commit, and team interaction. Enforces consistency and quality at the social layer.

### B.1 Conventional Commits
```
<type>(<scope>): <subject>

Types:
  feat     → New feature
  fix      → Bug fix
  refactor → Code change (neither fix nor feature)
  test     → Adding/correcting tests
  docs     → Documentation only
  chore    → Maintenance, deps, config
  perf     → Performance improvement
  security → Security fix
  ci       → CI/CD changes

Examples:
  ✓ fix(auth): handle expired JWT tokens with 401 response
  ✓ feat(users): add email verification on registration
  ✗ Fixed stuff  (vague, past tense)
```

### B.2 Branching Strategy (GitHub Flow)
**Branch Naming:** `<type>/<description>`
- `feature/user-authentication`
- `bugfix/login-redirect-loop-234`
- `hotfix/security-patch-cve-2024`

**Workflow:**
1. Create feature branch from `main`
2. Make small, focused commits
3. Push branch and open PR
4. Code review + CI checks
5. Merge to `main`
6. Delete branch

### B.3 Git Hooks & CI Gates
**Pre-commit checks (run automatically):**
- Linter passes
- Type check passes
- Tests pass
- No secrets detected (gitleaks / truffleHog)

### B.4 Code Review Checklist
**For the Author:**
```
□ PR is small and focused (< 400 lines changed)
□ Tests included and passing
□ No console.logs or debug code left
□ Screenshots attached for UI changes
□ Description explains WHY, not just WHAT
```

**For the Reviewer:**
```
□ Code follows project conventions
□ Error paths are handled
□ No security vulnerabilities introduced
□ No performance regressions (N+1, unnecessary re-renders)
□ Tests adequately cover the change
□ Documentation updated if needed
□ Edge cases considered
```

### B.5 Useful Git Commands
| Command | Purpose |
|---|---|
| `git rebase -i HEAD~5` | Clean up last 5 commits |
| `git stash push -m "WIP"` | Save uncommitted work |
| `git cherry-pick <hash>` | Apply specific commit |
| `git reflog` | Recover from mistakes |
| `git bisect` | Find which commit introduced a bug |

---

*End of Appendices. Return to Constant Core or Master Index for navigation.*

---

## APPENDIX: META-REFERENCE

> Reference material for AI system configuration, prompt engineering, and skill deployment.
> Not needed for day-to-day coding tasks.

## 🔷 LOADING PROTOCOL (Historical Reference)

> Note: This guide is now a single unified file. Use the Part numbers above instead of old filenames.

Read THIS file first. Then load sub-modules based on task type:

| Task Type | Module Loading Order |
|-----------|---------------------|
| **Writing new code** | Part 1 (Core Prompt) → Part 6 (Code Quality) → Part 8 (Anti-Patterns) → Language-specific Part |
| **Unknown bug / debugging** | Part 1 (Core) → Part 3 (Diagnosis) → Part 5 (Fix Patterns) → Part 4 (Test Strategy) |
| **Writing tests** | Part 1 (Core) → Part 4 (Test Strategy) → Language-specific Part |
| **Fixing a known bug** | Part 1 (Core) → Part 5 (Fix Patterns) → Part 3 (Diagnosis) → Part 4 (Test Strategy) |
| **Race condition / async bug** | Part 1 (Core) → Part 7 (Advanced Bugs) → Part 5 (Fix Patterns) |
| **Memory leak / performance** | Part 1 (Core) → Part 7 (Advanced Bugs) → Part 16 (System Design) / Appendix A |
| **React / frontend bug** | Part 1 (Core) → Part 11 (React Patterns) → Part 5 (Fix Patterns) |
| **Python bug** | Part 1 (Core) → Part 12 (Python Patterns) → Part 5 (Fix Patterns) |
| **TypeScript bug** | Part 1 (Core) → Part 13 (TypeScript Patterns) → Part 5 (Fix Patterns) |
| **Code review** | Part 1 (Core) + Part 6 (Code Quality) + Part 8 (Anti-Patterns) + Part 3 (Diagnosis) |
| **Security hardening** | Part 1 (Core) → Part 5 (Fix Patterns: Security) + Part 7 (Advanced Bugs) |
| **Architecture design** | Part 1 (Core) → Part 6 (Code Quality) → Part 8 (Anti-Patterns) |
| **Pull request / process** | Part 1 (Core Prompt) for process discipline |
| **Research & analysis** | Part 9 (Research & Analysis) |
| **Codebase search / navigation** | Part 10 (Search & Navigation) |

**Always-active references in this file:**
- Part 1 (Core Prompt) — Global AI rules, validation gates, debugging protocol
- Part 6 (Code Quality) — Cross-discipline review standards
- Part 14 (Property Testing) — fast-check patterns
- Part 15 (Error Prevention) — Semgrep-style guardrails and systematic debugging workflows

---

## 🔷 TEMPERATURE GUIDELINES

```
Bug fixing:      0.0–0.2  (minimize hallucination)
Code generation: 0.3–0.5  (some creativity for good naming)
Refactoring:     0.2–0.4  (preserve semantics, improve structure)
Architecture:    0.5–0.7  (explore options, weigh trade-offs)
Testing:         0.2–0.3  (systematic coverage)
```

---

## 🔷 QUALITY SCORING RUBRIC

After code generation, score output against this rubric:

| Criterion | Weight | Score (1-5) | Notes |
|-----------|--------|-------------|-------|
| Correctness | 30% | | Does it solve the problem? |
| Type Safety | 15% | | Are all types explicit? |
| Error Handling | 15% | | Are all error paths handled? |
| Test Coverage | 15% | | Is there adequate testing? |
| Code Clarity | 10% | | Is it readable and maintainable? |
| Performance | 10% | | Is it efficient? |
| Security | 5% | | Are there vulnerabilities? |

**Minimum acceptable score: 4.0/5.0**

---

## 🔷 CHAIN-OF-THOUGHT ENFORCEMENT

For complex tasks, force explicit reasoning:

```
"Think step-by-step:
1. First list all possible root causes ranked by likelihood
2. For each cause, describe the evidence that would confirm/deny it
3. Propose 3 candidate fixes with trade-offs
4. Select the best fix and justify the choice
5. Output the final answer wrapped in ```language blocks"
```

---

## 🔷 VIP EXPERT NOTE: ELITE WORKFLOWS & DELIVERY PATTERNS

### 1. Spec-Driven Development (Gated Workflow)

Code without a spec is guessing. Use this four-phase gated workflow for any feature that touches more than one file or takes more than 30 minutes:

```
SPECIFY ──→ PLAN ──→ TASKS ──→ IMPLEMENT
   │          │        │          │
   ▼          ▼        ▼          ▼
 Human      Human    Human      Human
 reviews    reviews  reviews    reviews
```

**Surface assumptions immediately.** Before writing spec content, list what you're assuming:

```markdown
ASSUMPTIONS I'M MAKING:
1. This is a web application (not native mobile)
2. Authentication uses session-based cookies (not JWT)
3. The database is PostgreSQL (based on existing Prisma schema)
→ Correct me now or I'll proceed with these.
```

**Reframe instructions as success criteria.** When receiving vague requirements, translate them into concrete, testable conditions:

```markdown
REQUIREMENT: "Make the dashboard faster"

REFRAMED SUCCESS CRITERIA:
- Dashboard LCP < 2.5s on 4G connection
- Initial data load completes in < 500ms
- No layout shift during load (CLS < 0.1)
→ Are these the right targets?
```

### 2. Incremental Implementation

Build in thin vertical slices — implement one piece, test it, verify it, then expand.

**The Increment Cycle:**
```
Implement ──→ Test ──→ Verify ──→ Commit ──→ Next slice
```

**Rule 0: Simplicity First**
Before writing any code, ask: "What is the simplest thing that could work?"

```markdown
SIMPLICITY CHECK:
✗ Generic EventBus with middleware pipeline for one notification
✓ Simple function call
✗ Abstract factory pattern for two similar components
✓ Two straightforward components with shared utilities
✗ Config-driven form builder for three forms
✓ Three form components
```

**Rule 0.5: Scope Discipline**
Touch only what the task requires. Do NOT:
- "Clean up" code adjacent to your change
- Refactor imports in files you're not modifying
- Add features not in the spec because they "seem useful"

If you notice something worth improving outside scope, note it — don't fix it:
```markdown
NOTICED BUT NOT TOUCHING:
- src/utils/format.ts has an unused import (unrelated to this task)
→ Want me to create a task for this?
```

**Slicing Strategies:**
- **Vertical Slices (preferred):** Build one complete path through the stack (DB → API → UI)
- **Contract-First Slicing:** Define API contract (types/OpenAPI spec) first, then implement backend and frontend in parallel against it
- **Risk-First Slicing:** Tackle the riskiest or most uncertain piece first. If it fails, you discover it before investing in the rest.

### 3. Source-Driven Development

Every framework-specific code decision must be backed by official documentation. Training data goes stale, APIs get deprecated, best practices evolve.

**The Process:**
```
DETECT ──→ FETCH ──→ IMPLEMENT ──→ CITE
```

1. **Detect Stack and Versions:** Read `package.json`, `requirements.txt`, etc. State versions explicitly.
2. **Fetch Official Documentation:** Get the specific docs page for the feature you're implementing. Not the homepage.
3. **Implement Following Documented Patterns:** Use the API signatures from the docs, not from memory.
4. **Cite Your Sources:** Every framework-specific pattern gets a citation.

**Source Hierarchy (most to least authoritative):**
1. Official documentation (react.dev, docs.djangoproject.com)
2. Official blog / changelog
3. Web standards references (MDN, web.dev)
4. Browser/runtime compatibility (caniuse.com)

**Never cite as primary sources:** Stack Overflow, blog posts, AI-generated summaries, or training data.

```typescript
// React 19 form handling with useActionState
// Source: https://react.dev/reference/react/useActionState#usage
const [state, formAction, isPending] = useActionState(submitOrder, initialState);
```

If you cannot find documentation for a pattern, say so explicitly:
```markdown
UNVERIFIED: I could not find official documentation for this pattern.
This is based on training data and may be outdated. Verify before using.
```

### 4. Shipping and Launch

Ship with confidence. The goal is not just to deploy — it's to deploy safely, with monitoring in place and a rollback plan ready.

**Feature Flag Strategy:**
Ship behind feature flags to decouple deployment from release:
```typescript
const flags = await getFeatureFlags(userId);
if (flags.taskSharing) {
  return <TaskSharingPanel task={task} />;
}
return null;
```

**Feature flag lifecycle:**
1. DEPLOY with flag OFF → Code is in production but inactive
2. ENABLE for team/beta → Internal testing in production
3. GRADUAL ROLLOUT → 5% → 25% → 50% → 100%
4. MONITOR at each stage
5. CLEAN UP → Remove flag within 2 weeks of full rollout

**Staged Rollout Decision Thresholds:**

| Metric | Advance (green) | Hold (yellow) | Roll back (red) |
|--------|-----------------|---------------|-----------------|
| Error rate | Within 10% of baseline | 10-100% above baseline | >2x baseline |
| P95 latency | Within 20% of baseline | 20-50% above baseline | >50% above baseline |
| Client JS errors | No new error types | New errors at <0.1% of sessions | New errors at >0.1% of sessions |
| Business metrics | Neutral or positive | Decline <5% | Decline >5% |

**Rollback Plan Template:**
```markdown
## Rollback Plan

### Trigger Conditions
- Error rate > 2x baseline
- P95 latency > [X]ms

### Steps
1. Disable feature flag (if applicable) OR deploy previous version
2. Verify rollback: health check, error monitoring
3. Communicate to team

### Time to Rollback
- Feature flag: < 1 minute
- Redeploy previous version: < 5 minutes
```

---


## Synthesis Sources

| Source | Key Contributions | Links |
|--------|-------------------|-------|
| **OpenAI O3 Pro** | RAG architecture, chain-of-thought, temperature guidelines, few-shot exemplars | — |
| **Codex-5.3** | 3-layer architecture, command router, test matrix, VIP note structure | — |
| **Qwen Plus** | Triple-Anchor pattern, BugFixer Knowledge Vault, what-not-to-do analysis | — |
| **Claude Designs** | Skill file structure, module organization, loading protocols | — |
| **Context Engineering** | Prompt templates, structured reasoning, systematic debugging | — |
| **Superpowers** | Test-driven development, incremental change discipline | [obra/superpowers](https://github.com/obra/superpowers) |
| **Microsoft Engineering Playbook** | Code review, TDD, design patterns, observability | [microsoft/code-with-engineering-playbook](https://github.com/microsoft/code-with-engineering-playbook) |
| **Google Eng Practices** | Code review standards (CL descriptions, reviewer guide) | [google/eng-practices](https://github.com/google/eng-practices) |
| **Professional Programming** | Career-long software engineering best practices | [charlax/professional-programming](https://github.com/charlax/professional-programming) |
| **Semgrep** | Lightweight static analysis for security and code quality | [semgrep/semgrep](https://github.com/semgrep/semgrep) |
| **fast-check** | Property-based testing for JavaScript/TypeScript | [dubzzz/fast-check](https://github.com/dubzzz/fast-check) |
| **mutmut** | Mutation testing for Python | [boxed/mutmut](https://github.com/boxed/mutmut) |
| **Stryker** | Mutation testing for JS/TS/C#/Scala | [stryker-mutator/stryker-js](https://github.com/stryker-mutator/stryker-js) |
| **Playwright** | Reliable E2E testing | [microsoft/playwright](https://github.com/microsoft/playwright) |
| **axe-core** | Accessibility testing engine | [dequelabs/axe-core](https://github.com/dequelabs/axe-core) |

