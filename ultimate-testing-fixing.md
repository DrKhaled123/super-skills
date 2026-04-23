# ULTIMATE SYSTEMATIC DEBUGGING & TESTING ARSENAL v2.0

<!-- IDX:ZERO_CONFIG_AUTOPILOT_START -->
## ⚡ PART 0: ZERO-CONFIG AI AUTO-PILOT ENGINE

> **THIS SECTION IS THE MASTER KEY.** When an AI coding assistant loads this file, it MUST execute the Auto-Pilot Protocol below FIRST. No manual configuration needed. No questions to ask. Just detect → classify → route → fix → verify.

---

### 🔑 THE AUTO-PILOT PRIME DIRECTIVE

```
WHEN YOU RECEIVE ANY BUG REPORT, ERROR, OR TESTING REQUEST:

1. DO NOT ask the user what framework/language/tool they use
2. DO NOT ask what version of Node/Python/etc. they have
3. DO NOT ask for clarification unless the error is genuinely ambiguous
4. INSTEAD: Run the Auto-Detection Protocol below SILENTLY
5. THEN: Execute the correct diagnosis path AUTOMATICALLY
6. DELIVER: Root cause + fix + test + verification — in ONE response
```

---

### 🧠 STEP 1: AUTO-DETECT PROJECT CONTEXT (Run Silently)

**Execute these detection commands IMMEDIATELY when given a project path or error. Do NOT show these to the user — just use the results internally.**

```bash
#!/usr/bin/env bash
# === UNIVERSAL PROJECT AUTO-DETECTOR ===
# Run this mentally or literally to classify any project instantly

PROJECT_DIR="${1:-.}"

# ─── Language Detection ───
detect_languages() {
  local langs=""
  [ -f "$PROJECT_DIR/package.json" ] && langs="$langs javascript/typescript"
  [ -f "$PROJECT_DIR/requirements.txt" ] || [ -f "$PROJECT_DIR/pyproject.toml" ] || [ -f "$PROJECT_DIR/setup.py" ] && langs="$langs python"
  [ -f "$PROJECT_DIR/go.mod" ] && langs="$langs go"
  [ -f "$PROJECT_DIR/Cargo.toml" ] && langs="$langs rust"
  [ -f "$PROJECT_DIR/pom.xml" ] || [ -f "$PROJECT_DIR/build.gradle" ] && langs="$langs java"
  [ -f "$PROJECT_DIR/Gemfile" ] && langs="$langs ruby"
  [ -f "$PROJECT_DIR/composer.json" ] && langs="$langs php"
  find "$PROJECT_DIR" -maxdepth 3 -name "*.sh" -o -name "*.bash" 2>/dev/null | head -1 | grep -q . && langs="$langs shell"
  echo "${langs:-unknown}"
}

# ─── Framework Detection ───
detect_framework() {
  if [ -f "$PROJECT_DIR/package.json" ]; then
    local pkg=$(cat "$PROJECT_DIR/package.json" 2>/dev/null)
    echo "$pkg" | grep -q '"next"' && echo "nextjs" && return
    echo "$pkg" | grep -q '"nuxt"' && echo "nuxt" && return
    echo "$pkg" | grep -q '"astro"' && echo "astro" && return
    echo "$pkg" | grep -q '"svelte"' && echo "sveltekit" && return
    echo "$pkg" | grep -q '"remix"' && echo "remix" && return
    echo "$pkg" | grep -q '"vite"' && echo "vite" && return
    echo "$pkg" | grep -q '"react"' && echo "react" && return
    echo "$pkg" | grep -q '"vue"' && echo "vue" && return
    echo "$pkg" | grep -q '"angular"' && echo "angular" && return
    echo "$pkg" | grep -q '"express"' && echo "express" && return
    echo "$pkg" | grep -q '"fastify"' && echo "fastify" && return
    echo "$pkg" | grep -q '"hono"' && echo "hono" && return
  fi
  [ -f "$PROJECT_DIR/manage.py" ] && echo "django" && return
  [ -f "$PROJECT_DIR/app.py" ] || [ -f "$PROJECT_DIR/wsgi.py" ] && echo "flask" && return
  [ -f "$PROJECT_DIR/main.py" ] && grep -q "FastAPI\|fastapi" "$PROJECT_DIR/main.py" 2>/dev/null && echo "fastapi" && return
  echo "unknown"
}

# ─── Runtime & Version Detection ───
detect_runtime() {
  command -v node &>/dev/null && echo "node:$(node -v 2>/dev/null)"
  command -v bun &>/dev/null && echo "bun:$(bun --version 2>/dev/null)"
  command -v deno &>/dev/null && echo "deno:$(deno --version 2>/dev/null | head -1)"
  command -v python3 &>/dev/null && echo "python:$(python3 --version 2>/dev/null)"
  command -v go &>/dev/null && echo "go:$(go version 2>/dev/null)"
  command -v rustc &>/dev/null && echo "rust:$(rustc --version 2>/dev/null)"
}

# ─── Package Manager Detection ───
detect_pkg_manager() {
  [ -f "$PROJECT_DIR/bun.lockb" ] && echo "bun" && return
  [ -f "$PROJECT_DIR/pnpm-lock.yaml" ] && echo "pnpm" && return
  [ -f "$PROJECT_DIR/yarn.lock" ] && echo "yarn" && return
  [ -f "$PROJECT_DIR/package-lock.json" ] && echo "npm" && return
  [ -f "$PROJECT_DIR/uv.lock" ] && echo "uv" && return
  [ -f "$PROJECT_DIR/poetry.lock" ] && echo "poetry" && return
  [ -f "$PROJECT_DIR/Pipfile.lock" ] && echo "pipenv" && return
  echo "unknown"
}

# ─── Infrastructure Detection ───
detect_infra() {
  [ -f "$PROJECT_DIR/Dockerfile" ] || [ -f "$PROJECT_DIR/docker-compose.yml" ] && echo "docker"
  [ -d "$PROJECT_DIR/.github/workflows" ] && echo "github-actions"
  [ -f "$PROJECT_DIR/.gitlab-ci.yml" ] && echo "gitlab-ci"
  [ -f "$PROJECT_DIR/nginx.conf" ] || [ -d "$PROJECT_DIR/nginx" ] && echo "nginx"
  [ -f "$PROJECT_DIR/Caddyfile" ] && echo "caddy"
  [ -f "$PROJECT_DIR/vercel.json" ] && echo "vercel"
  [ -f "$PROJECT_DIR/fly.toml" ] && echo "fly"
  [ -f "$PROJECT_DIR/railway.json" ] && echo "railway"
}

# ─── Test Framework Detection ───
detect_test_framework() {
  if [ -f "$PROJECT_DIR/package.json" ]; then
    local pkg=$(cat "$PROJECT_DIR/package.json" 2>/dev/null)
    echo "$pkg" | grep -q '"vitest"' && echo "vitest"
    echo "$pkg" | grep -q '"jest"' && echo "jest"
    echo "$pkg" | grep -q '"playwright"' && echo "playwright"
    echo "$pkg" | grep -q '"cypress"' && echo "cypress"
    echo "$pkg" | grep -q '"mocha"' && echo "mocha"
  fi
  [ -f "$PROJECT_DIR/pytest.ini" ] || [ -f "$PROJECT_DIR/pyproject.toml" ] && grep -q "pytest" "$PROJECT_DIR/pyproject.toml" 2>/dev/null && echo "pytest"
  find "$PROJECT_DIR" -maxdepth 2 -name "test_*.py" -o -name "*_test.py" 2>/dev/null | head -1 | grep -q . && echo "pytest"
  find "$PROJECT_DIR" -maxdepth 2 -name "*.test.ts" -o -name "*.spec.ts" 2>/dev/null | head -1 | grep -q . && echo "vitest-or-jest"
}

# ─── Dependency Version Extraction (Critical for correct API usage) ───
detect_key_versions() {
  if [ -f "$PROJECT_DIR/package.json" ]; then
    echo "=== KEY JS/TS DEPENDENCY VERSIONS ==="
    cat "$PROJECT_DIR/package.json" | grep -E '"(react|next|vue|svelte|vite|typescript|zod|prisma|drizzle)"' 2>/dev/null
  fi
  if [ -f "$PROJECT_DIR/requirements.txt" ]; then
    echo "=== KEY PYTHON DEPENDENCY VERSIONS ==="
    grep -iE "(django|flask|fastapi|sqlalchemy|pydantic|pytest)" "$PROJECT_DIR/requirements.txt" 2>/dev/null
  fi
}
```

**AI Internal Processing:** After detection, mentally construct this context card:

```markdown
PROJECT CONTEXT CARD (auto-generated, never show to user):
┌─────────────────────────────────────────────────┐
│ Languages:    [auto-detected]                   │
│ Framework:    [auto-detected]                   │
│ Runtime:      [auto-detected + version]         │
│ Pkg Manager:  [auto-detected]                   │
│ Test Runner:  [auto-detected]                   │
│ Infra:        [auto-detected]                   │
│ Key Versions: [extracted from lockfile/config]   │
│ OS:           [from system context]             │
└─────────────────────────────────────────────────┘
```

---

### 🎯 STEP 2: AUTO-CLASSIFY ERROR SEVERITY & TYPE

**Given ANY error input, classify it instantly using this decision matrix:**

```
INPUT: Error message / symptom / user description
                    │
    ┌───────────────┼───────────────────────────────────────┐
    │               │                                       │
    ▼               ▼                                       ▼
PRODUCTION DOWN   BROKEN BUILD              BEHAVIORAL BUG / IMPROVEMENT
(P0 — URGENT)     (P1 — BLOCKING)           (P2/P3 — NORMAL)
    │               │                                       │
    ▼               ▼                                       ▼
Skip to:          Skip to:                   Run full protocol:
PART V            Error Taxonomy: BUILD      Phase 0 → 1 → 2 → 3 → 4 → 5
(Emergency)       then Phase 4 (Fix)         (Systematic Debugging)
```

**Auto-Classification Rules (AI executes these silently):**

```markdown
IF error contains "ECONNREFUSED" OR "Connection refused" OR "502" OR "503"
  → CLASSIFY: Infrastructure/Network → ROUTE: Production Emergency Protocol

IF error contains "Cannot find module" OR "Module not found" OR "ENOENT"
  → CLASSIFY: Build/Import → ROUTE: Build Error Taxonomy + Dependency Verification

IF error contains "TypeError" OR "Cannot read properties of" OR "undefined is not"
  → CLASSIFY: Runtime Crash → ROUTE: Runtime Crash Taxonomy

IF error contains "CORS" OR "Access-Control" OR "blocked by CORS"
  → CLASSIFY: Network/Config → ROUTE: Backend API + Nginx Anti-Patterns

IF error contains "hydration" OR "mismatch" OR "did not match"
  → CLASSIFY: SSR/Framework → ROUTE: React/Next.js Gotchas

IF error contains "OOM" OR "heap" OR "out of memory" OR "SIGKILL"
  → CLASSIFY: Memory → ROUTE: Memory Leak Taxonomy

IF error contains "timeout" OR "ETIMEDOUT" OR "slow" OR "hanging"
  → CLASSIFY: Performance → ROUTE: Performance Taxonomy + Scenario "IT'S SLOW"

IF error contains "permission denied" OR "EACCES" OR "403"
  → CLASSIFY: Security/Auth → ROUTE: Security Taxonomy

IF error contains "deadlock" OR "lock" OR "race" OR "intermittent"
  → CLASSIFY: Concurrency → ROUTE: Async/Race Taxonomy

IF symptom is "works locally, fails in production/CI"
  → CLASSIFY: Environment → ROUTE: "Works on My Machine" Scenario

IF symptom is "test fails sometimes" OR "flaky"
  → CLASSIFY: Non-deterministic → ROUTE: Flaky Bug Scenario

IF symptom is "no error, but wrong output"
  → CLASSIFY: Logic → ROUTE: Logic Error Taxonomy

DEFAULT → Run Phase 0 Triage, then Phase 1 Root Cause Investigation
```

---

### 🚀 STEP 3: AUTO-EXECUTE THE FIX PIPELINE

**Once classified, the AI MUST follow this exact pipeline WITHOUT asking the user for permission at each step:**

```
┌──────────────────────────────────────────────────────────────────┐
│                   AI AUTO-FIX PIPELINE                           │
│                                                                  │
│  1. DETECT    → Auto-scan project (Step 1 above)                │
│  2. CLASSIFY  → Auto-route to correct section (Step 2 above)    │
│  3. EVIDENCE  → Read the FULL file(s) involved + error context  │
│  4. DIAGNOSE  → Generate 3 hypotheses ranked by probability     │
│  5. FIX       → Implement the smallest surgical fix             │
│  6. TEST      → Write regression test proving the fix works     │
│  7. VERIFY    → Run build + lint + type-check commands          │
│  8. DELIVER   → Present: Root Cause → Fix → Test → Verify      │
│                                                                  │
│  ⏱️ Target: Complete in ONE response, no back-and-forth         │
└──────────────────────────────────────────────────────────────────┘
```

**Verification Commands Auto-Selection (based on detected stack):**

```markdown
IF stack is JavaScript/TypeScript:
  VERIFY WITH: npx tsc --noEmit && npm run build && npm run test 2>/dev/null
  LINT WITH:   npx biome check . || npx eslint . 2>/dev/null
  
IF stack is Python:
  VERIFY WITH: python -m py_compile <file> && python -m pytest tests/ -x 2>/dev/null
  LINT WITH:   ruff check . && mypy src/ --ignore-missing-imports 2>/dev/null

IF stack is Go:
  VERIFY WITH: go build ./... && go test ./... && go vet ./...

IF stack is Rust:
  VERIFY WITH: cargo check && cargo test && cargo clippy

IF stack is Shell:
  VERIFY WITH: shellcheck <file> && bash -n <file>

IF infrastructure involves Docker:
  VERIFY WITH: docker build --no-cache . && docker compose config 2>/dev/null

IF infrastructure involves Nginx:
  VERIFY WITH: nginx -t
```

---

### 📋 STEP 4: AUTO-FORMAT OUTPUT (Mandatory for Every Fix)

**Every fix response MUST follow this exact structure — no exceptions:**

```markdown
## 🔍 Root Cause
[One sentence: what causes the bug and why]

## 🛠️ Fix
[Minimal diff — show only changed lines with context]

## 🧪 Regression Test  
[Test that fails before fix, passes after]

## ✅ Verification
[Commands run + their output confirming the fix works]

## ⚠️ Risk Assessment
- Affected files: [list]
- Side effects: [none / list]
- Rollback: [exact command to undo]

## 📊 Fix Confidence Score: [X/50]
(Using the Fix Confidence Scorecard from this arsenal)
```

---

### 🔄 STEP 5: INTELLIGENT CONTEXT-AWARE TOOL SELECTION

**The AI auto-selects tools based on detected stack. Never suggest a tool the project doesn't have:**

```markdown
TOOL SELECTION MATRIX (auto-applied based on Step 1 detection):

┌──────────────────┬─────────────────────┬──────────────────────┬─────────────────┐
│ Detected Stack   │ Linter              │ Type Checker         │ Test Runner     │
├──────────────────┼─────────────────────┼──────────────────────┼─────────────────┤
│ Next.js / React  │ biome OR eslint     │ tsc --noEmit         │ vitest OR jest  │
│ Vite / Vanilla   │ biome OR eslint     │ tsc --noEmit         │ vitest          │
│ Vue / Nuxt       │ eslint + vue plugin │ vue-tsc              │ vitest          │
│ Svelte           │ eslint + svelte     │ svelte-check         │ vitest          │
│ Astro            │ eslint              │ astro check          │ vitest          │
│ Express / Hono   │ biome OR eslint     │ tsc --noEmit         │ vitest OR jest  │
│ Python / Django  │ ruff                │ mypy / pyright       │ pytest          │
│ Python / FastAPI │ ruff                │ mypy / pyright       │ pytest          │
│ Go               │ golangci-lint       │ go vet               │ go test         │
│ Rust             │ clippy              │ cargo check          │ cargo test      │
│ Shell            │ shellcheck          │ N/A                  │ bats            │
│ Java             │ spotbugs + pmd      │ javac                │ junit           │
└──────────────────┴─────────────────────┴──────────────────────┴─────────────────┘

SECURITY TOOLS (auto-select based on availability):
  Tier 1 (fast):    semgrep --config=auto . (if installed)
  Tier 2 (thorough): npm audit / pip-audit / govulncheck (per stack)  
  Tier 3 (secrets):  gitleaks detect --source . (if installed)
  Fallback:          grep -rn "password\|secret\|api.key\|token" --include="*.env*" .
```

---

### 🧩 STEP 6: FRAMEWORK-AWARE AUTO-ADJUSTMENTS

**The AI silently applies these adjustments based on detected framework:**

```markdown
NEXT.JS AUTO-ADJUSTMENTS:
  □ Check: Is this a Server Component or Client Component?
  □ Check: Does the file need 'use client' or 'use server'?
  □ Check: Is this App Router (app/) or Pages Router (pages/)?
  □ Auto-verify: next.config.js/ts for relevant settings
  □ Build cmd: npm run build (catches SSR errors dev mode misses)

VITE AUTO-ADJUSTMENTS:
  □ Check: import.meta.env instead of process.env for client code
  □ Check: VITE_ prefix on environment variables
  □ Check: Both vite.config AND tsconfig for path aliases
  □ Build cmd: npm run build && npm run preview (Rollup is stricter than esbuild)

REACT AUTO-ADJUSTMENTS:
  □ Check: StrictMode double-render is NOT a bug (React 18+)
  □ Check: All useEffect dependency arrays are complete
  □ Check: No direct state mutation (use spread/structuredClone)
  □ Check: Key props use stable IDs, never array indices

PYTHON DJANGO AUTO-ADJUSTMENTS:
  □ Check: manage.py commands use correct settings module
  □ Check: Migration state matches models
  □ Check: ALLOWED_HOSTS, CSRF, CORS settings for production

PYTHON FASTAPI AUTO-ADJUSTMENTS:
  □ Check: Pydantic model versions (v1 vs v2 — breaking API changes)
  □ Check: async def vs def for route handlers
  □ Check: Dependency injection patterns

DOCKER AUTO-ADJUSTMENTS:
  □ Check: .dockerignore exists and excludes node_modules, .git, .env
  □ Check: Multi-stage build for production images
  □ Check: Non-root USER directive
  □ Check: HEALTHCHECK instruction present
```

---

### 🏆 STEP 7: QUALITY GATES (Auto-Enforced Before Delivering Any Fix)

```markdown
BEFORE PRESENTING ANY FIX TO THE USER, THE AI MUST VERIFY:

GATE 1 — COMPREHENSION:
  □ I have read the FULL file(s) I'm editing (not just the error line)
  □ I understand what the code does in context (not just the broken part)
  □ I have checked all callers/importers of the code I'm changing

GATE 2 — CORRECTNESS:
  □ My fix addresses the ROOT CAUSE, not just the symptom
  □ My fix is the MINIMUM change needed (no "while I'm here" improvements)  
  □ I have NOT introduced any new imports without verifying they exist
  □ I have NOT used APIs from a different version than what's installed

GATE 3 — SAFETY:
  □ Existing functionality is preserved (I checked adjacent code)
  □ No new TypeScript/Python type errors introduced
  □ No security vulnerabilities introduced (no eval, no SQL concat, no exposed secrets)
  □ Error paths are handled (not just the happy path)

GATE 4 — VERIFICATION:
  □ I have provided the exact commands to verify the fix
  □ I have provided a regression test (or explained why one isn't applicable)
  □ Build command would succeed with my changes
  □ I have provided a rollback plan

IF ANY GATE FAILS → DO NOT PRESENT THE FIX. Go back and fix it first.
```

---

### 📊 COMPLETE AUTO-PILOT DECISION FLOWCHART

```
USER GIVES: Error / Bug / Testing Request
              │
              ▼
    ┌─────────────────────┐
    │  STEP 1: AUTO-DETECT │ ← Scan project files, detect stack
    │  (Silent, instant)   │
    └──────────┬──────────┘
              │
              ▼
    ┌─────────────────────┐
    │  STEP 2: CLASSIFY    │ ← Match error pattern to category
    │  (P0/P1/P2/P3)      │
    └──────────┬──────────┘
              │
     ┌────────┼────────┐
     ▼        ▼        ▼
   P0:      P1:      P2/P3:
   Emergency Build    Full Protocol
   Protocol  Error    Phase 0→5
     │        │        │
     └────────┼────────┘
              │
              ▼
    ┌─────────────────────┐
    │  STEP 3: EVIDENCE    │ ← Read full files, trace data flow
    │  (Read before edit)  │
    └──────────┬──────────┘
              │
              ▼
    ┌─────────────────────┐
    │  STEP 4: DIAGNOSE    │ ← 3 hypotheses, test highest first
    │  (Scientific method) │
    └──────────┬──────────┘
              │
              ▼
    ┌─────────────────────┐
    │  STEP 5: FIX         │ ← Minimal surgical change
    │  (Root cause only)   │
    └──────────┬──────────┘
              │
              ▼
    ┌─────────────────────┐
    │  STEP 6: VERIFY      │ ← Build + lint + test + type-check
    │  (Stack-appropriate) │
    └──────────┬──────────┘
              │
              ▼
    ┌─────────────────────┐
    │  STEP 7: DELIVER     │ ← Structured output format
    │  (One response)      │
    └─────────────────────┘
```

<!-- IDX:ZERO_CONFIG_AUTOPILOT_END -->

---

<!-- IDX:CONSTANT_CORE_START -->
## CONSTANT CORE GUIDELINES (Applies to Every Section)

**Iron Law:** `NO FIXES WITHOUT ROOT CAUSE INVESTIGATION FIRST`.
**80/20 Rule:** Spend 80% of time understanding, 20% fixing. A well-understood bug needs 1–5 lines.

**Golden Rules:**
1. **Fix the bug, not the blame.** Focus on root cause, not who wrote it.
2. **Never change more than necessary.** Minimal, surgical fixes. One logical change per commit.
3. **Understand before modifying.** Read the code, search for context, trace the data flow.
4. **Every fix needs a test.** A bug that cannot be reproduced on demand has not been fixed.
5. **Reproduce → Isolate → Fix → Verify.** Always in this order.
6. **Test behavior, not implementation.**
7. **Type everything.** No implicit `any`.
8. **No secrets in code.** Ever.
9. **Document the "why," not the "what."**
10. **Measure before optimizing.**
11. **Read the FULL file before editing.** Never edit a file you've only partially read — you WILL break unrelated code.
12. **Verify import paths exist.** Never add an import without confirming the module/file path is real in the project.
13. **Check the runtime version.** APIs differ across Node 18 vs 22, Python 3.9 vs 3.12, React 17 vs 18/19.
14. **Preserve existing functionality.** Every "improvement" must prove it doesn't break what already works.

---

### AI CODER SELF-CORRECTION PROTOCOL

**Before writing ANY code, run this internal checklist:**

```markdown
□ STOP: Have I READ the full file(s) I'm about to edit?
□ STOP: Do I know the EXACT versions of all frameworks/libraries in use?
□ STOP: Have I checked if this project uses a CUSTOM pattern that differs from defaults?
□ STOP: Does my fix introduce any NEW dependencies? If yes — is that justified?
□ STOP: Am I about to change a WORKING feature while fixing a different issue?
□ STOP: Have I verified my fix works for BOTH the happy path AND the error path?
□ STOP: Am I making assumptions about the data shape without checking the schema?
□ STOP: Could my change break production while fixing development?
```

**The 5 Deadliest AI Coder Mistakes (memorize these):**

| # | Mistake | Why It Happens | Prevention |
|---|---------|---------------|------------|
| 1 | **Phantom imports** — importing from modules that don't exist | AI hallucinates package APIs | `grep -r "from X import" .` to verify before adding |
| 2 | **Version mismatch** — using APIs from wrong library version | Training data mixes versions | Check `package.json` / `requirements.txt` FIRST |
| 3 | **Silent functionality loss** — "fixing" one thing breaks another | Editing files without full context | Read the ENTIRE file, run ALL tests after |
| 4 | **Syntax corruption** — generating malformed JSON/YAML/TSX | Complex nested structures | Validate syntax with parser before committing |
| 5 | **Config drift** — editing source but not config, or vice versa | Forgetting coupled files | Map ALL files that need coordinated changes |

---

### PRE-FLIGHT SAFETY CHECKS (Run Before Every Task)

```markdown
## Pre-Flight Check: File Integrity
□ Read the full file I'm editing (not just the function)
□ Check for other references to the code I'm changing: `grep -rn "functionName" src/`
□ Identify all callers of the function/component I'm modifying
□ Check if there's a corresponding test file and read it
□ Verify the build system still works: `npm run build` or equivalent

## Pre-Flight Check: Dependency Safety
□ Check exact versions: `cat package.json | jq '.dependencies'`
□ Verify the API I'm using exists in THIS version (not a newer/older one)
□ Check for peer dependency conflicts: `npm ls` or `pipdeptree`
□ Never upgrade a dep as part of a bugfix — that's a separate PR

## Pre-Flight Check: Environment Awareness
□ Am I editing code that runs on the server, client, or both?
□ Is this SSR/SSG? (Next.js, Nuxt) — server-only APIs break in browser
□ Are there environment variables this code depends on?
□ Does this code behave differently in dev vs production mode?

## Pre-Flight Check: Data Shape Verification
□ What is the ACTUAL shape of data at this point? (log it, don't assume)
□ Does the API response match the TypeScript interface?
□ Are there optional fields that could be undefined?
□ Could this data be empty/null in edge cases?
```

---

**Mandatory Online Search Rule (Before Any Task):**
- **Always search online first** for the most updated notes, solutions, and upstream fixes before proposing any code change.
- **Primary search tool:** [SearXNG](https://github.com/searxng/searxng) — a privacy-respecting, self-hosted metasearch engine aggregating 70+ search engines (Google, Bing, DuckDuckGo, Wikipedia, etc.) without tracking or storing queries.
- **When to use it:**
  - Before diagnosing an unfamiliar error or exception
  - Before recommending a library, dependency, or API
  - Before applying a fix to verify it is still current and not deprecated
  - When checking for CVEs, security advisories, or upstream patches
  - **NEW: Before using ANY tool/library API** — verify the syntax hasn't changed
  - **NEW: When a fix "should work" but doesn't** — check for known platform bugs
- **Search protocol:**
  1. Formulate a precise query (include exact error message, library version, and language)
  2. Review at least the top 3 results from authoritative sources (official docs, GitHub issues, Stack Overflow with accepted answers)
  3. Summarize findings in one sentence before proceeding to the task
  4. Cite the most relevant URL(s) in your final output
  5. **NEW:** Cross-reference with the project's ACTUAL installed version, not the latest

**Tool Selection Principles:**
- Never suggest a tool without first stating which protocol phase you're in.
- Every tool reference must include when NOT to use it.
- Production emergencies bypass full protocol — stabilize first, investigate second.
- Always start at the lowest-numbered detection layer that could reveal the issue.
- **NEW: Verify the tool is INSTALLED before suggesting commands** — `command -v <tool>` or `which <tool>`.
- **NEW: Check OS compatibility** — `perf` doesn't exist on macOS, `dtrace` doesn't exist on most Linux distros.

**Forbidden Patterns (Instant Rejection):**

*Error Handling:*
- `catch(e) {}` or `catch(e) { console.log(e) }` — swallowed errors
- `try { ... } catch(e) { return null; }` — silent failure masking
- `.catch(() => {})` on promises — promise error swallowing
- `except Exception: pass` in Python — blanket exception hiding

*Type Safety:*
- `as any` or `@ts-ignore` or `@ts-expect-error` without explanation
- `==` instead of `===` in JavaScript/TypeScript
- `# type: ignore` without specific error code in Python mypy
- Casting without validation: `data as User` without Zod/schema check

*Security:*
- SQL string concatenation or template literals in queries
- `eval()` in any language without explicit security justification
- `dangerouslySetInnerHTML` without DOMPurify sanitization
- Hardcoded secrets, API keys, or passwords in source code
- `chmod 777` on any file

*Data Integrity:*
- Mutable default arguments (Python): `def f(items=[])`
- Array index as React key: `key={index}`
- Mutating function arguments: `options.headers = ...`
- Shared mutable state between requests/components

*Process:*
- Skipping tests for "quick fixes"
- Bundling refactoring with bugfixes in the same change
- Editing files you haven't fully read
- Adding dependencies without checking if the project already has an equivalent

**Quality Gates Before Any Fix:**
1. Linting passes (`ruff`, `biome`, `eslint`)
2. Type checking passes (`mypy`, `tsc --noEmit`)
3. Tests pass (`pytest`, `vitest`)
4. Security scan passes (`semgrep`, `bandit`)
5. **NEW: Build succeeds** (`npm run build`, `python -m py_compile`)
6. **NEW: No new console warnings** in browser/terminal
7. **NEW: Existing functionality verified** — manually test the happy path

**Escalation Triggers — STOP and Ask the Human:**
```markdown
STOP if any of these are true:
□ The fix requires changing more than 3 files
□ The fix requires a database migration
□ The fix touches authentication or authorization logic
□ The fix changes a public API contract
□ You've attempted 3 fixes and none worked (architectural problem)
□ The fix requires upgrading a major dependency version
□ You're not sure if the fix will break production
□ The error message doesn't make sense given the code
```

**Output Format Mandatory for Every Fix:**
1. Root Cause (one sentence)
2. Solution (minimal diff)
3. Tests (fails before, passes after)
4. Risk Assessment
5. Verification Commands
6. **NEW: Affected Files List** — every file that was changed and why
7. **NEW: Rollback Plan** — how to undo this change safely

**Output Format for Tool Recommendations:**
- Tool name + install command
- When to use it
- When NOT to use it
- Quick command example
- Expected output interpretation
- **NEW: OS/Platform compatibility notes**
- **NEW: Version requirements** (minimum version needed)

---

### CROSS-CUTTING TRAP AWARENESS

**These bugs cross ALL categories and phases. Check for them on EVERY task:**

**1. Unicode & Encoding Traps:**
```markdown
□ File encoding: Is it UTF-8? Check with `file -bi <file>`
□ Byte Order Mark (BOM): Can break JSON parsing, bash scripts
□ String length: `"é".length === 2` in JavaScript (surrogate pairs)
□ Path encoding: Non-ASCII filenames break on many tools
□ Database collation: Is it utf8mb4 (MySQL) for full Unicode?
□ API responses: Always specify `Content-Type: application/json; charset=utf-8`
```

**2. Timezone & Date Traps:**
```markdown
□ New Date() gives LOCAL time — always use UTC for storage
□ Month is 0-indexed in JavaScript: `new Date(2024, 0, 1)` = January
□ date-fns vs moment vs Temporal API — know which your project uses
□ Server timezone vs client timezone — log both when debugging
□ Daylight Saving Time transitions cause 23-hour and 25-hour days
□ ISO 8601: `2024-01-15T10:30:00Z` (Z = UTC, +02:00 = offset)
```

**3. Path & Filesystem Traps:**
```markdown
□ Windows uses `\`, Unix uses `/` — use `path.join()` or `os.path.join()`
□ Case sensitivity: macOS/Windows are case-insensitive, Linux is case-sensitive
□ Maximum path length: Windows 260 chars, Linux 4096 chars
□ Symlinks: `fs.readFileSync` follows symlinks, `fs.lstatSync` doesn't
□ Trailing slashes in URLs change routing behavior
□ `.env` files are NOT committed — verify they exist on the target machine
```

**4. Numeric Precision Traps:**
```markdown
□ `0.1 + 0.2 !== 0.3` in JavaScript (IEEE 754 floating point)
□ Use integer cents for money: 1999 = $19.99
□ `parseInt('08')` returns 8 (not octal) but `parseInt('0x10')` returns 16
□ `Number.MAX_SAFE_INTEGER` = 2^53 - 1 — larger IDs overflow
□ Python: `1/2 == 0` in Python 2, `1/2 == 0.5` in Python 3
□ JSON cannot represent BigInt — serialize as string
```

**5. Concurrency & Ordering Traps:**
```markdown
□ Object key order is NOT guaranteed in JavaScript (mostly is, but spec doesn't require)
□ `Promise.all` fails fast — one rejection cancels all (use `Promise.allSettled`)
□ React `setState` is batched — reading state immediately after setting gives old value
□ Database auto-increment IDs have gaps — never assume contiguous
□ Event listener order is not guaranteed across browsers
□ `setTimeout(fn, 0)` does NOT execute immediately — minimum ~4ms
```

**6. Deployment & Infrastructure Traps:**
```markdown
□ Build works locally but fails in CI — check Node/Python version in CI config
□ Environment variables differ between local, staging, and production
□ DNS propagation takes 0-72 hours — new domains may not resolve immediately
□ Docker `COPY . .` includes node_modules if .dockerignore is missing
□ Port conflicts: check `lsof -i :<port>` before starting services
□ SSL/TLS certificate expiry — set calendar reminders
□ CORS headers must be set on the SERVER, not the client
□ Nginx default `client_max_body_size` is 1MB — file uploads fail silently
```
<!-- IDX:CONSTANT_CORE_END -->

---

<!-- IDX:INDEX_START -->
## DETAILED MASTER INDEX

| Category | Sub-Section | When to Use |
|----------|-------------|-------------|
| **⚡ Part 0** | **Zero-Config AI Auto-Pilot Engine** | **ALWAYS — Execute first, automatically** |
| — Auto-Detect | Language, framework, runtime, pkg manager, infra detection | On every new project/error |
| — Auto-Classify | Severity routing (P0–P3), error pattern matching | On every error received |
| — Auto-Execute | Fix pipeline, verification commands, quality gates | On every fix delivered |
| — Auto-Format | Structured output: Root Cause → Fix → Test → Verify | On every response |
| **Constant Core** | Universal rules, forbidden patterns, quality gates | Read first before any task |
| — AI Self-Correction | Internal checklist, 5 deadliest AI mistakes | Before writing ANY code |
| — Pre-Flight Checks | File integrity, dependency safety, environment awareness | Before starting ANY task |
| — Cross-Cutting Traps | Unicode, timezone, path, numeric, concurrency, deployment | Check on EVERY task |
| **Part I** | **Systematic Debugging Protocol** | **Any confirmed bug** |
| — Phase 0 | Triage — Is this actually a bug? + Pitfall Shield | Before investigating |
| — Phase 1 | Root Cause Investigation + Regression Test Pitfalls | Gather evidence |
| — Phase 2 | Isolate & Pattern Analysis + Pitfall Shield | Narrow exact location |
| — Phase 3 | Hypothesis & Verification + Pitfall Shield | Scientific method & 5-hypotheses |
| — Phase 4 | Fix & Validate + Pitfall Shield + Verification Checklist | Surgical fix + proof |
| — Phase 5 | Document & Learn | Post-fix knowledge capture |
| **Part II** | **Error Taxonomies by Type** | **Classified bug categories** |
| — Build | Compilation, linking, dependency errors | Build-time failures |
| — Runtime Crash | Segfaults, exceptions, OOM kills | Application crashes |
| — Logic | Silent wrong output | Wrong results without crash |
| — Async/Race | Timing, promises, concurrency | Intermittent / timing bugs |
| — Memory | Leaks, growth, OOM over time | Memory degradation |
| — Performance | Slowness, timeouts, bottlenecks | Speed / resource issues |
| — Security | Injection, bypass, exposure | Security findings / audits |
| — Heisenbug | Observation-dependent bugs | Bugs that disappear when watched |
| **Part III** | **Domain-Specific Debugging** | **By tech stack / layer** |
| — Frontend | 12 failure modes for web/mobile | React / Vue / Angular bugs |
| — Backend API | Server-side debugging patterns | API / service issues |
| — Database | Query, schema, migration issues | DB performance / correctness |
| — Distributed | Microservices, netsplit, consensus | Multi-service architectures |
| — Mobile | iOS / Android / React Native | Native mobile bugs |
| **Part IV** | **Scenario-Based Tool Matrix** | **By symptom description** |
| — Slow | Slowness diagnosis by domain | Performance complaints |
| — Crash | Crash diagnosis by domain | Application crashes |
| — Wrong Output | Logic / data pipeline issues | Silent logic failures |
| — Environment | "Works on my machine" parity | Environment parity issues |
| — Flaky | Intermittent / non-deterministic | Flaky tests / heisenbugs |
| **Part V** | **Production Emergency Protocols** | **Live incident response** |
| — Linux/Server | 30-second triage commands | Server down / OOM / hung |
| — Network | Traffic capture & routing | Connectivity / DNS / API |
| — Logs | Log analysis recipes | Parsing logs at scale |
| — Containers | Docker / K8s triage | Containerized deployments |
| **Part VI** | **Language-Specific Arsenals** | **Language toolchain** |
| — Python | Python toolkit & patterns | Python code |
| — JS/TS/Node | JavaScript toolkit & patterns | JS/TS code |
| — React/Web | Frontend toolkit & React fixes | React / browser code |
| — C/C++/Rust | Systems toolkit & memory debug | Native code |
| — Java/Go | JVM / Go toolkit & profiling | Java / Go code |
| — Shell | Shell script debugging | Bash / sh scripts |
| **Part VII** | **Advanced Detection Layers** | **Deep / hidden error detection** |
| — Layer 1 | Static analysis (Semgrep / CodeQL / Infer) | Code analysis |
| — Layer 2 | Dynamic analysis (Valgrind / Sanitizers) | Runtime analysis |
| — Layer 3 | Fuzzing (AFL++ / libFuzzer) | Crash discovery |
| — Layer 4 | Symbolic execution (KLEE / angr) | Path exploration |
| — Layer 5 | Taint analysis (Taintgrind) | Injection tracking |
| — Layer 6 | Mutation testing (mutmut / Stryker) | Test quality verification |
| — Layer 7 | Hybrid approaches (Driller) | Advanced combos |
| **Part VIII** | **Scripts & Validation Pipelines** | **Automation** |
| — Scanner | Universal quality scanner (scan.sh) | Pre-push validation |
| — Diagnose | 60-second diagnosis script | Rapid triage |
| — Hot Reload | Watch + auto-fix loop | Development loop |
| — CI Template | GitHub Actions quality gate | CI/CD setup |
| — Validation Python | Python validation one-liner | Python full check |
| — Validation JS/TS | JS/TS validation one-liner | JS/TS full check |
| — Validation Security | Security validation one-liner | Security full check |
| **Part IX** | **AI Prompt Modes** | **Agent behavior presets** |
| — BUGFIX_STRICT | Rigorous bugfixing mode | Any bugfix task |
| — CLEAN_REFACTOR | Safe refactoring mode | Refactoring with tests |
| — TEST_DESIGN_MAX | Maximum coverage mode | Writing comprehensive tests |
| — SECURITY_HARDEN | Security audit mode | Security reviews |
| — PERF_OPTIMIZE | Performance optimization mode | Speed improvements |
| **Part X** | **Agent Integration & Postmortem** | **Workflows & learning** |
| — Handoffs | Debug ↔ Test agent protocols | Multi-agent workflows |
| — Postmortem | Incident learning template | After incident resolution |
| **Part XI** | **Framework & Deployment Error Prevention** | **⚠️ NEW — Error prevention** |
| — React 18/19 | 7 React gotchas (StrictMode, Server Components, hydration) | React development |
| — Next.js 14/15 | 6 Next.js gotchas (App Router, env vars, SSR) | Next.js projects |
| — Vite | 5 Vite gotchas (env vars, ESM, build differences) | Vite projects |
| — TypeScript | 5 TypeScript gotchas (type assertions, strict null) | TypeScript code |
| — Node.js | 5 Node.js gotchas (ESM/CJS, event loop, __dirname) | Node.js backends |
| — Python | 6 Python gotchas (mutable defaults, GIL, closures) | Python code |
| — Docker Anti-Patterns | 6 Docker deployment mistakes | Docker deployments |
| — Nginx Anti-Patterns | 6 Nginx configuration mistakes | Nginx/reverse proxy |
| — SSH & Server | 6 server security anti-patterns | Server ops |
| — CI/CD Anti-Patterns | 5 CI/CD pipeline mistakes | CI/CD pipelines |
| — AI Workflow Guardrails | 7 guardrails for AI coding assistants | **Every AI-assisted session** |
| — Error Symptom Decoder | 35+ symptom → cause lookup tables | **Quick error diagnosis** |
| — Fix Confidence Scorecard | Score fixes before applying them | Before applying any fix |
| — Emergency Recovery | Git, Node, Python, Docker, Server recipes | When everything is broken |
| **Appendix** | **Cheat Sheet + Repo Index** | **Quick reference & sources** |
| — Cheat Sheet | One-page quick reference | Daily reference |
| — Repo Index | All source repositories | Finding original sources |
| **Part XII** | **⚡ AI Instant-Fix Lookup Tables** | **Exact error → exact fix (55+ entries)** |
| — JS/TS Fixes | 20 most common JavaScript/TypeScript errors | Any JS/TS error |
| — React/Next.js Fixes | 10 most common React/Next.js errors | React/Next.js errors |
| — Python Fixes | 10 most common Python errors | Python errors |
| — Docker/Nginx/Server Fixes | 10 infrastructure errors | Deployment errors |
| — Git Fixes | 5 most common Git errors | Git issues |
| **Part XIII** | **🧠 AI Smart Context Gathering** | **What files to read per error type** |
| — By Error Type | 8 error categories with exact file checklists | Before writing ANY fix |
| **Part XIV** | **🔄 AI Auto-Recovery & Self-Correction** | **When fixes fail** |
| — Escalation Ladder | 3-attempt failure protocol | After each failed fix |
| — Failure Patterns | 7 common AI fix failure patterns | Debugging stuck fixes |
| — Self-Diagnostic | Checklist for when AI is stuck | When going in circles |
| **Part XV** | **🆕 Modern Tooling (2025-2026)** | **Up-to-date ecosystem** |
| — Runtimes | Bun, Deno, Node 22+ | New project decisions |
| — Build Tools | Vite, Turbopack, Rspack, esbuild | Build setup |
| — Linting & Testing | Biome, Vitest, Playwright | Tool selection |
<!-- IDX:INDEX_END -->

---

# PART I: SYSTEMATIC DEBUGGING PROTOCOL

<!-- IDX:PHASE_0_START -->
## PHASE 0: TRIAGE — Is This Actually a Bug?

**Purpose:** Prevent wasted effort on misunderstood behavior, missing features, or local environment issues. 15% of reported "bugs" are not bugs.

### The 30-Second Triage Checklist

```markdown
□ Is this expected behavior that the reporter misunderstands?
□ Has this ever worked? (If no → it's a missing feature, not a bug)
□ Is this a local-only issue? (stale cache, wrong branch, uncommitted changes)
□ Can I reproduce it in a clean environment? (incognito, fresh install, new container)
□ Is there a known issue / recent deploy that explains it?
□ Is the report based on outdated documentation or specs?
□ Could this be a data issue (test data vs production data shape)?
```

### Triage Decision Tree

```
Can you reproduce it?
├── NO → Check: cache, env drift, data dependency, timing
│   ├── If clearly env issue → CLOSE / REDIRECT
│   └── If unclear → GATHER more info before investigating
│
├── YES, but only locally → Likely env/config issue
│   └── Diff environments, check .env, Node version, OS differences
│
├── YES, consistently → PROCEED to Phase 1
│
└── YES, but intermittent → Mark as potential race/timing/memory leak
    └── PROCEED to Phase 1 with intermittent-bug protocol
```

### Quick Environment Diff Script

```bash
# Compare working vs broken environments
env | sort > /tmp/env.broken.txt
# Run same on working machine, then:
diff /tmp/env.good.txt /tmp/env.broken.txt

# Check Node/Python versions
node -v && npm -v && python --version

# Check git state
git status && git log --oneline -3
```

**If all answers suggest it IS a real bug → Proceed to Phase 1.**

### ⚠️ PHASE 0 PITFALL SHIELD: Common Triage Mistakes

```markdown
MISTAKE 1: Skipping triage entirely because the error "looks obvious"
  → FIX: Even "obvious" errors have surprising root causes 30% of the time

MISTAKE 2: Testing in a dirty environment (stale node_modules, old build cache)
  → FIX: `rm -rf node_modules .next dist && npm install && npm run build`

MISTAKE 3: Confusing a build error with a runtime error
  → FIX: Check — does it fail at `npm run build` or at `npm run dev` + browser interaction?

MISTAKE 4: Ignoring the FULL error message (only reading the first line)
  → FIX: The ROOT CAUSE is usually in the MIDDLE of the stack trace, not the top

MISTAKE 5: Assuming the bug is in YOUR code when it's in a dependency
  → FIX: Check if the error stacktrace passes through node_modules/

MISTAKE 6: Not checking if the bug was ALREADY REPORTED
  → FIX: Search GitHub Issues for the exact error message before investigating
```


---

<!-- IDX:PHASE_1_START -->
## PHASE 1: ROOT CAUSE INVESTIGATION

**Purpose:** Systematically locate, isolate, and understand bugs before touching any code. Misdiagnosed bugs produce two bugs for every one fixed.

### Step 1.1 — Capture the Evidence

**Error Message Analysis:**
- Read error messages completely — don't skim.
- Note exact line numbers, file paths, error codes.
- Distinguish primary error from cascading secondary errors.
- Save the full stack trace; the root cause frame is usually NOT the top frame.

**Environment & Context Capture:**
```bash
# Capture system state at time of error
uname -a > /tmp/debug_env.txt
date -Iseconds >> /tmp/debug_env.txt
node -v >> /tmp/debug_env.txt 2>/dev/null
python --version >> /tmp/debug_env.txt 2>/dev/null
env | grep -E "NODE_ENV|ENV|STAGE" >> /tmp/debug_env.txt
```

### Step 1.2 — Reproduce Consistently

**Reproduction Checklist:**
```markdown
□ Can you reproduce it consistently?
□ What are the EXACT steps to reproduce?
□ What is the exact input that causes it?
□ What is the expected output?
□ What is the actual output?
□ Is it environment-specific? (dev vs prod, OS, browser, Node version)
□ Is it data-specific? (only certain users, certain payloads)
□ Is it timing-specific? (only under load, only after X minutes)
□ When did it first appear? (check git history)
```

**Write the Regression Test FIRST:**
```typescript
// This becomes your proof that the bug exists AND your safety net after fixing
test('reproduces bug #123: user profile fails for names with apostrophes', () => {
  const input = { name: "O'Brien", email: "test@test.com" };
  expect(() => createUser(input)).not.toThrow();
});
```

**⚠️ REGRESSION TEST PITFALLS:**
```markdown
PITFALL 1: Test passes for wrong reason (testing the mock, not the code)
  → FIX: Verify the test FAILS when you revert the fix

PITFALL 2: Test is too broad — doesn't isolate the specific bug
  → FIX: Test should fail for EXACTLY the reported bug, nothing else

PITFALL 3: Test uses hardcoded paths/ports/IDs that differ in CI
  → FIX: Use relative paths, random ports, generated test IDs

PITFALL 4: Test depends on execution order (runs after another test seeds data)
  → FIX: Each test must set up and tear down its own state
```


**If you CANNOT reproduce consistently:**
- It's likely a race condition → see Async/Race taxonomy section
- It might be a stale cache → force-clear all caches and retest
- It might be environment drift → diff the environments
- Enable verbose logging and capture the failure in production

### Step 1.3 — Trace Data Flow (Backward Tracing)

**The Backward Tracing Technique:**
```
1. Identify the bad value at the point of failure
2. Ask: "Where did this value come from?"
3. Trace up one level in the call stack
4. Repeat until you find where the value was created or corrupted
5. Fix at the source, not at the symptom
```

**Example:**
```typescript
// Failure: user.name is undefined at line 47
// Trace back:
// Line 47: renderUser(user) ← user.name undefined
// Line 32: user = fetchUser(id) ← API returned wrong shape
// Line 15: id = extractId(url) ← id is correct
// Root cause: API contract changed, runtime shape ≠ expected shape
```

### Step 1.4 — Gather Evidence at Boundaries

For multi-component systems, instrument BEFORE guessing:
```bash
# For EACH component boundary:
#   - Log what data enters component
#   - Log what data exits component
#   - Verify environment/config propagation
#   - Check state at each layer

# Example multi-layer system:
echo "=== Layer 1: Workflow secrets ==="
echo "IDENTITY: ${IDENTITY:+SET}${IDENTITY:-UNSET}"

echo "=== Layer 2: Build script env ==="
env | grep IDENTITY || echo "IDENTITY not in environment"

echo "=== Layer 3: Keychain state ==="
security list-keychains
security find-identity -v

echo "=== Layer 4: Actual signing ==="
codesign --sign "$IDENTITY" --verbose=4 "$APP"
```

### Step 1.5 — Git History Investigation

```bash
# Find what changed recently
git log --oneline --since="1 week ago" -- "*.py" "*.ts" "*.tsx"

# Binary search commits to find the breaking change
git bisect start
git bisect bad          # current commit is broken
git bisect good abc123  # this commit was working
# Test middle commit, then:
git bisect good  # or git bisect bad
# Repeat until Git identifies the exact commit
git bisect reset
```
<!-- IDX:PHASE_1_END -->

---

<!-- IDX:PHASE_2_START -->
## PHASE 2: ISOLATE & PATTERN ANALYSIS

**Purpose:** Narrow the problem to the smallest failing unit and identify the pattern that explains the bug.

### Binary Search Isolation Method

This is the most efficient way to find bugs in complex systems:

```
1. Identify the full code path from input → output
2. Find the midpoint of that path
3. Add a checkpoint assertion at the midpoint
4. If assertion fails → bug is in first half → recurse
5. If assertion passes → bug is in second half → recurse
6. Continue until you find the exact line
```

**Example: Data Transformation Pipeline**
```typescript
// Full path: raw API response → parseResponse() → transformData() → formatForUI() → rendered output

const rawData = await fetchRawData();
console.assert(rawData.users.length > 0, 'RAW DATA CHECK');

const parsed = parseResponse(rawData);
console.assert(parsed.every(u => u.id), 'PARSE CHECK');

const transformed = transformData(parsed);
console.assert(transformed.every(u => u.displayName), 'TRANSFORM CHECK');

// Where assertion fails = where bug lives
```

### Isolation by Simplification

```python
# BEFORE (complex, hard to reason about):
data = fetch_from_database(user_id=123, include_relations=True, date_range=(start, end))
result = process(data)  # fails somewhere

# AFTER (isolated, easy to reason about):
minimal_data = {"id": 1, "name": "Test"}  # smallest data that triggers bug
result = process(minimal_data)
# If this works → bug is in the complex data shape
# If this fails → bug is in process() logic itself
```

### Pattern Analysis Checklist

```markdown
□ Find working examples in the same codebase
□ Read reference implementations completely — don't skim
□ List EVERY difference between working and broken
□ Check dependencies, config, environment assumptions
□ Compare against known anti-patterns from the Bug Taxonomy
□ Check if this pattern has failed before (search git history / issue tracker)
```

### The "Last Known Good" Method

```bash
# 1. Find the last commit/deploy where this worked
# 2. Read the diff between "last good" and "first bad"
# 3. The bug is in that diff — guaranteed
# 4. Search space reduced from entire codebase to a few files

git diff abc123..def456 --stat
git diff abc123..def456 -- src/components/UserForm.tsx
```

### The "Rubber Duck" Explanation

Before writing any fix, explain the bug out loud or in writing:
```markdown
1. "The function receives [X] as input"
2. "At step [N], it does [Y]"
3. "But it should do [Z] because [REASON]"
4. "The discrepancy is because [ROOT CAUSE]"
```
If you can't complete step 4, you don't understand the bug yet.

### ⚠️ PHASE 2 PITFALL SHIELD: Isolation Mistakes

```markdown
MISTAKE 1: Isolating at the wrong layer (testing the API when the bug is in the DB query)
  → FIX: Add console.log at EVERY boundary, not just endpoints

MISTAKE 2: "Simplifying" the test by changing the data shape
  → FIX: Use PRODUCTION data (anonymized) for reproduction, not synthetic data

MISTAKE 3: Binary search but forgetting async timing changes
  → FIX: When adding checkpoints to async code, use `await` at each checkpoint

MISTAKE 4: Comparing only code, not configuration
  → FIX: Diff EVERYTHING: `.env`, `tsconfig.json`, `nginx.conf`, Docker compose

MISTAKE 5: Not checking the NETWORK tab when isolating frontend bugs
  → FIX: 50% of "frontend bugs" are actually API response issues — check Network first
```

<!-- IDX:PHASE_2_END -->

---

<!-- IDX:PHASE_3_START -->
## PHASE 3: HYPOTHESIS & VERIFICATION

**Purpose:** Use the scientific method to avoid guess-and-check thrashing. Never fix without a falsifiable hypothesis.

### The 5-Hypothesis Scientific Method

**Step 1 — Generate 5 Distinct Hypotheses**

For each hypothesis, require:
- Mutually exclusive from the others
- References specific evidence in the code or error
- Assigns a prior probability (%) based on symptoms
- States what additional information would confirm or deny it

**Example Hypotheses for a React Stale State Bug:**
```markdown
H1 (70%): useEffect dependency array is missing `userId`, causing stale closure.
  Evidence: Effect uses `userId` but deps are `[]`.
  Confirm: Add `userId` to deps, bug disappears.

H2 (15%): fetchUser promise resolves after component unmounts, setting state on unmounted component.
  Evidence: No cleanup/cancellation in effect.
  Confirm: Add cancellation flag, warning disappears.

H3 (10%): Parent passes new object reference every render, causing infinite re-fetch.
  Evidence: `options` object created inline in parent.
  Confirm: Memoize options in parent, re-fetch stops.

H4 (4%): Race condition between two rapid `userId` changes.
  Evidence: Fast navigation between users.
  Confirm: Add request deduplication, bug stops.

H5 (1%): Global state management (Redux/Zustand) not updating selector.
  Evidence: Component props correct but derived state wrong.
  Confirm: Log selector output, verify mismatch.
```

**Step 2 — Elimination Round**

For each hypothesis, apply these tests:
- Does it explain ALL symptoms, or only some?
- Can it be reproduced in isolation?
- Does removing the suspected code path remove the symptom?
- What does the call stack say about this path?

**Step 3 — Root Cause Verdict**

State the most likely root cause with:
- Confidence score (0–100%)
- Exact mechanism: what triggers it → what breaks → what symptoms result
- Minimal reproduction case (smallest code that shows the bug)

**Step 4 — Adversarial Check**

```markdown
Now argue AGAINST your own diagnosis:
- What would make it wrong?
- What alternative explanation still fits all the facts?
- What evidence would completely invalidate this hypothesis?
```

**Step 5 — Diagnostic Commands**

Provide 5 specific commands, log statements, or debug checks to validate:
```javascript
// 1. Log dependency array completeness
console.log('Effect deps:', [dep1, dep2]);

// 2. Check for stale closure
console.log('Closed over value:', userId);

// 3. Verify cancellation
let cancelled = false;
fetchUser(userId).then(data => { if (!cancelled) setUser(data); });

// 4. Compare working vs broken props
console.log('Props diff:', diff(prevProps, nextProps));

// 5. Force re-render and observe
React DevTools → "Highlight updates"
```

### Hypothesis Testing Rules

```markdown
□ Form ONE hypothesis at a time
□ Make the SMALLEST possible change to test it
□ One variable at a time
□ If hypothesis fails, form a NEW hypothesis — don't stack fixes
□ If you don't know, say "I don't understand X" — don't pretend
```

### ⚠️ PHASE 3 PITFALL SHIELD: Hypothesis Mistakes

```markdown
MISTAKE 1: Anchoring on the first hypothesis and ignoring evidence against it
  → FIX: REQUIRE yourself to list 3+ alternatives before investigating any

MISTAKE 2: Testing multiple hypotheses simultaneously
  → FIX: Change ONE thing, observe, revert if wrong, then try the next

MISTAKE 3: Confirmation bias — "it seems to work" without rigorous tests
  → FIX: Define PASS/FAIL criteria BEFORE testing, not after

MISTAKE 4: Hypothesis is too vague: "something is wrong with state management"
  → FIX: Every hypothesis must name: EXACT variable + EXACT condition + EXACT trigger

MISTAKE 5: Not reverting failed hypothesis changes before testing the next one
  → FIX: Use `git stash` between each hypothesis test
```

<!-- IDX:PHASE_3_END -->

---

<!-- IDX:PHASE_4_START -->
## PHASE 4: FIX & VALIDATE

**Purpose:** Fix the root cause with surgical precision, then prove the fix works.

### Fix Selection Priority

When multiple fixes are possible, choose by this priority:
1. **Eliminate the possibility** — make the bug impossible by design
2. **Fail loudly** — throw with a clear error if invalid state occurs
3. **Degrade gracefully** — fallback to safe default with logging
4. **Guard at boundary** — validate input at entry point
5. **Never:** silently swallow, log-and-continue, or return undefined

### Fix Rules

```markdown
□ Fix the root cause, not the symptom
□ ONE change at a time. No "while I'm here" improvements
□ No bundled refactoring
□ Exact line(s) to change must be identified
□ Diff-style patch preferred for modifications
□ One-line explanation of WHY this fixes the ROOT CAUSE required
```

### Validation Checklist

```markdown
□ Test written that FAILS on old code, PASSES on new code
□ Root cause documented in code comment or commit message
□ No new TypeScript errors introduced
□ No new linter warnings
□ Adjacent code still works
□ Performance not degraded
□ No new security vulnerabilities
□ Edge cases handled (null, empty, boundary)
□ Error messages are clear and actionable
□ Documentation updated if behavior changed
□ Build succeeds in production mode (not just dev)
□ No console.log/debugger statements left in code
□ No commented-out code left behind
□ Import paths verified to exist (no phantom imports)
□ ALL callers of the changed function still work correctly
```


### The 3-Fix Rule

If you have tried 3 fixes and none worked:
```markdown
STOP. This is an architectural problem, not a local bug.
Signs of architectural problem:
- Each fix reveals new shared state/coupling in a different place
- Fixes require "massive refactoring" to implement
- Each fix creates new symptoms elsewhere

Action: Discuss with your human partner before attempting fix #4.
```

### Example: Root Cause vs Symptom Fix

```typescript
// ❌ SYMPTOM FIX: Guards the symptom
function displayUser(user: User | null) {
  if (user && user.profile && user.profile.name) {
    console.log(user.profile.name);
  }
}

// ✅ ROOT CAUSE FIX: Ensures data is never malformed
function getUser(id: string): User | null {
  const user = users.find(u => u.id === id);
  if (!user) return null;
  return {
    ...user,
    profile: user.profile ?? { name: 'Unknown User' },
  };
}
```
<!-- IDX:PHASE_4_END -->

### ⚠️ PHASE 4 PITFALL SHIELD: Fix Implementation Mistakes

```markdown
MISTAKE 1: Fixing the symptom, not the root cause (adding null checks everywhere)
  → FIX: Ask "WHY is this null?" and fix the source, not the guard

MISTAKE 2: The "while I'm here" refactor that introduces new bugs
  → FIX: SEPARATE commits for bugfix and refactoring. NEVER combine them.

MISTAKE 3: Leaving debug code in the fix (console.log, debugger statements)
  → FIX: `grep -rn "console.log\|debugger\|TODO" src/` before committing

MISTAKE 4: Not testing the error path (only testing the happy path)
  → FIX: Every fix must have at least ONE test for what happens when things go WRONG

MISTAKE 5: Fix works in dev but breaks in production build
  → FIX: Always `npm run build && npm run start` (not just `npm run dev`)

MISTAKE 6: Changing function signature without updating all callers
  → FIX: `grep -rn "functionName" src/` to find EVERY call site before changing

MISTAKE 7: Adding a dependency for a 3-line fix
  → FIX: If the fix is <10 lines, write it inline. Don't add lodash for `_.get()`

MISTAKE 8: Not considering backwards compatibility
  → FIX: If this is an API or library, old callers must still work after the change

MISTAKE 9: Fixing in the wrong file (editing compiled output instead of source)
  → FIX: Always edit SOURCE files (.ts, .tsx), never build artifacts (.js in dist/)

MISTAKE 10: Not verifying the fix on a fresh clone
  → FIX: `git stash && npm install && npm run build` to simulate clean checkout
```

### Fix Verification Final Checklist

```markdown
Before declaring a fix complete:
□ The EXACT bug from the report is verified fixed (not just "it seems to work")
□ The fix has been tested with the ORIGINAL reproduction steps
□ No regressions: run the FULL test suite, not just the new test
□ Production build succeeds (not just development mode)
□ The fix is the MINIMUM necessary change
□ The commit message explains the ROOT CAUSE, not just what was changed
□ If deployment is needed: deployment steps are documented
```


---

<!-- IDX:PHASE_5_START -->
## PHASE 5: DOCUMENT & LEARN

**Purpose:** Ensure the same bug never happens twice and build institutional knowledge.

### Root Cause Statement Template

Before closing any bug, write:
```markdown
ROOT CAUSE STATEMENT:
"The bug occurs because [SPECIFIC REASON].
When [INPUT/TRIGGER], the code [WHAT IT DOES WRONG],
but it should [WHAT IT SHOULD DO].
The fix is to [SPECIFIC CHANGE]."
```

**Example:**
```markdown
ROOT CAUSE STATEMENT:
"The bug occurs because `defaultOptions` is a shared module-level object
that gets mutated on every call to makeRequest().
When the function adds the Authorization header, it modifies the shared object,
so subsequent calls inherit the previous call's headers.
The fix is to create a new options object on each call using spread syntax."
```

### Documentation Requirements

```markdown
□ Commit message references the bug and explains the root cause
□ Code comment added where the bug was subtle
□ Regression test added to prevent recurrence
□ If pattern is common, add to team's bug pattern library
□ Update runbooks if operational issue
```

### Pattern Library Entry

```markdown
[BUG-PATTERN-001] Shared Mutable Default Parameter
- Context: JavaScript/TypeScript functions with object default params
- Symptom: Works first call, wrong on subsequent calls
- Root Cause: Object passed by reference and mutated
- Fix: Create new object inside function using spread
- Test: Call function twice, verify independent results
```
<!-- IDX:PHASE_5_END -->

---

# PART II: ERROR TAXONOMIES BY TYPE

<!-- IDX:TAXONOMY_BUILD_START -->
## ERROR TAXONOMY: BUILD ERRORS

**Symptoms:** Compilation fails, linking errors, dependency conflicts, type checker errors.

### Diagnostic Approach

```markdown
□ Read compiler error from top to bottom (first error is usually the real one)
□ Check for cascading errors (fix the first, others may disappear)
□ Verify dependency versions match (lockfile drift)
□ Check for circular imports/dependencies
□ Verify build tool configuration (webpack, vite, tsconfig)
```

### Common Patterns

**Type Mismatch at Build Time:**
```typescript
// Symptom: tsc compiles but runtime crashes (shape mismatch)
// Fix: Runtime validation with Zod
const ApiUserSchema = z.object({
  id: z.string(),
  name: z.string(),
  email: z.string().email(),
});
const user = ApiUserSchema.parse(rawData);
```

**Dependency Hell:**
```bash
# Diagnose version conflicts
npm ls <package-name>
npm why <package-name>
# or
pipdeptree | grep -A5 <package>
```

**Circular Dependencies:**
```bash
# JS/TS
npx madge --circular src/
# Python
pip install pipdeptree && pipdeptree
```

### Prevention
- Preemptive debugging via CI linting and type-checking
- Lockfile enforcement in CI
- Dependency update automation with test gates
<!-- IDX:TAXONOMY_BUILD_END -->

---

<!-- IDX:TAXONOMY_RUNTIME_CRASH_START -->
## ERROR TAXONOMY: RUNTIME CRASHES

**Symptoms:** Segfaults, unhandled exceptions, OOM kills, process exits unexpectedly.

### Null/Undefined Errors

**Symptom:** `TypeError: Cannot read properties of undefined (reading 'name')`

**Root Cause:** Assuming data exists without verifying.

```typescript
// ❌ WRONG: Assumes user always exists
function getUserDisplayName(userId: string): string {
  const user = users.find(u => u.id === userId);
  return user.profile.name; // crashes if user not found OR profile is null
}

// ✅ CORRECT: Guard every assumption
function getUserDisplayName(userId: string): string {
  const user = users.find(u => u.id === userId);
  if (!user) return 'Unknown User';
  if (!user.profile) return user.email ?? 'Unknown User';
  return user.profile.name;
}
```

**Diagnosis Checklist:**
```markdown
□ Where is this object created/set?
□ Is there a code path where it's never set?
□ Does an async operation populate it? Could it be called before completion?
□ Is it deleted/cleared anywhere before this point?
□ Is there a race between creation and access?
```

### Type Coercion Bugs

**Symptom:** Logic behaves unexpectedly with certain values.

```typescript
// ❌ These all evaluate TRUE with ==
null == undefined        // true
0 == ''                  // true  
0 == false               // true
'' == false              // true
'0' == false             // true
[] == false              // true

// DIAGNOSIS: Search codebase for `==` (not `===`)
// Fix: Replace every == with === and explicitly handle edge cases
```

### Unhandled Promise Rejection

```typescript
// ❌ BROKEN: Silent failure — rejection is lost
async function loadDashboard() {
  fetchUserData().then(data => setUser(data));   // rejection not caught
  fetchMetrics().then(data => setMetrics(data)); // rejection not caught
}

// ✅ FIX: Use Promise.allSettled for independent operations
async function loadDashboard() {
  const [userResult, metricsResult] = await Promise.allSettled([
    fetchUserData(), fetchMetrics(),
  ]);
  if (userResult.status === 'fulfilled') setUser(userResult.value);
  else console.error('Failed to load user:', userResult.reason);
}
```
<!-- IDX:TAXONOMY_RUNTIME_CRASH_END -->

---

<!-- IDX:TAXONOMY_LOGIC_START -->
## ERROR TAXONOMY: LOGIC ERRORS

**Symptoms:** Wrong output but no crash. Hard to find because the program "works."

### Off-by-One Errors

**Symptom:** Last element missing, or one extra element, or loop runs one too many times.

```typescript
// ❌ Common off-by-one patterns:
const arr = [1, 2, 3, 4, 5];
for (let i = 0; i < arr.length - 1; i++) { } // missing last element

// ✅ DIAGNOSIS: Write a unit test with known small array
test('pagination returns correct page', () => {
  const items = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
  expect(paginate(items, 1, 3)).toEqual([1, 2, 3]);
  expect(paginate(items, 4, 3)).toEqual([10]);
  expect(paginate(items, 5, 3)).toEqual([]);
});
```

### State Mutation Bugs

**Symptom:** Works on first call, wrong results on second call.

```typescript
// ❌ WRONG: defaultOptions is mutated across calls
const defaultOptions = { timeout: 5000, retries: 3, headers: {} };
function makeRequest(url: string, options = defaultOptions) {
  options.headers['Authorization'] = getToken(); // MUTATES shared object!
  return fetch(url, options);
}

// ✅ CORRECT: Always create new objects
function makeRequest(url: string, overrides: Partial<RequestOptions> = {}) {
  const options: RequestOptions = {
    timeout: 5000,
    retries: 3,
    ...overrides,
    headers: { ...overrides.headers, Authorization: getToken() },
  };
  return fetch(url, options);
}
```

### Logic Error Tracing

**Approach:** Trace each conditional branch with concrete values.

```typescript
// ❌ WRONG: Logic error in discount calculation
function calculateDiscount(price: number, memberType: string): number {
  let discount = 0;
  if (memberType === 'gold') discount = 0.2;
  if (memberType === 'silver') discount = 0.1;
  if (price > 100) discount += 0.05; // BUG: applies to non-members too
  return price * (1 - discount);
}

// DIAGNOSIS: Trace with concrete values
// price=150, memberType='basic'
// discount starts at 0; gold? no; silver? no;
// price > 100? YES → discount = 0.05 ← wrong!

// ✅ CORRECT: Restructure logic to be explicit
function calculateDiscount(price: number, memberType: 'gold' | 'silver' | 'basic'): number {
  const BASE_DISCOUNT = { gold: 0.20, silver: 0.10, basic: 0 };
  const base = BASE_DISCOUNT[memberType] ?? 0;
  const volume = (memberType !== 'basic' && price > 100) ? 0.05 : 0;
  return price * (1 - base - volume);
}
```
<!-- IDX:TAXONOMY_LOGIC_END -->

---

<!-- IDX:TAXONOMY_ASYNC_RACE_START -->
## ERROR TAXONOMY: ASYNC & RACE CONDITIONS

**Symptoms:** Intermittent failures, timing-dependent, "works on my machine," flaky tests.

### Race Condition Checklist

```markdown
□ Is there shared state accessed by concurrent operations?
□ Are promises awaited in the correct order?
□ Could the act of observing/logging change the timing?
□ Does the code assume a specific execution order that isn't guaranteed?
□ What differs between fast and slow environments?
```

### Missing Await

```typescript
// ❌ BROKEN: Returns Promise object instead of value
function getUserName(id: string) {
  const user = fetchUser(id); // missing await — user is a Promise!
  return user.name;           // undefined
}

// ✅ FIX: Always await async operations
async function getUserName(id: string): Promise<string> {
  const user = await fetchUser(id);
  return user.name;
}
```

### Race Condition in State Updates

```typescript
// ❌ BROKEN: If fetchUser is called twice quickly, second response might arrive first
function UserComponent({ userId }: { userId: string }) {
  const [user, setUser] = useState(null);
  useEffect(() => {
    fetchUser(userId).then(setUser); // no cleanup!
  }, [userId]);
}

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

### Python Async Pitfalls

```python
# ❌ Missing await in asyncio
coros = [fetch_data(url) for url in urls]
results = await asyncio.gather(*coros)

# ❌ Shared mutable state in threads
shared_list = []
threads = [threading.Thread(target=lambda: shared_list.append(1)) for _ in range(10)]
# Fix: Use queue.Queue or threading.Lock
```
<!-- IDX:TAXONOMY_ASYNC_RACE_END -->

---

<!-- IDX:TAXONOMY_MEMORY_START -->
## ERROR TAXONOMY: MEMORY LEAKS

**Symptoms:** Process slows over time, memory usage grows steadily, eventual OOM crash.

### Memory Leak Patterns

**JavaScript/Browser:**
- Forgotten event listeners
- Uncleared intervals/timeouts
- Closures retaining large objects
- Detached DOM nodes

**Python:**
- Circular references with `__del__`
- Unclosed file handles / database connections
- Cache dictionaries growing without bounds
- Mutable default arguments accumulating state

**Node.js:**
- Retained closures in callbacks
- Uncached database results
- Event listener accumulation

### Detection Commands

```bash
# Node.js heap snapshot
kill -USR2 <pid>
# Open .heapsnapshot in Chrome DevTools Memory panel

# Python tracemalloc
python -c "import tracemalloc; tracemalloc.start(); tracemalloc.snapshot()"

# C/C++ Valgrind massif
valgrind --tool=massif --massif-out-file=massif.out ./app
ms_print massif.out
```

### React Memory Leak Fix

```typescript
// ❌ Leaks: sets state on unmounted component
useEffect(() => {
  fetchData().then(setData);
}, []);

// ✅ Safe cleanup
useEffect(() => {
  let isMounted = true;
  fetchData().then(data => { if (isMounted) setData(data); });
  return () => { isMounted = false; };
}, []);
```
<!-- IDX:TAXONOMY_MEMORY_END -->

---

<!-- IDX:TAXONOMY_PERFORMANCE_START -->
## ERROR TAXONOMY: PERFORMANCE BOTTLENECKS

**Symptoms:** Slowness, timeouts, high CPU/memory/resource usage.

### Performance Debugging Decision Tree

```
Is it slow for one user? → Performance problem (algorithm, query, blocking)
Is it fast for one user but slow under load? → Scalability problem (architecture)
```

### Common Bottlenecks

**N+1 Query Problem:**
```python
# ❌ N+1: One query per item
for user in users:
    print(user.profile.bio)  # queries profile table for EACH user

# ✅ Fix: Eager loading
users = User.objects.select_related('profile').all()
```

**Blocking Event Loop (Node.js):**
```typescript
// ❌ Blocks event loop
app.get('/data', (req, res) => {
  const data = heavySynchronousComputation(); // DON'T
  res.json(data);
});

// ✅ Offload to worker or make async
app.get('/data', async (req, res) => {
  const data = await runInWorker(heavySynchronousComputation);
  res.json(data);
});
```

**Unbounded Growth:**
```typescript
// ❌ Cache grows forever
const cache = new Map();
function getData(key) {
  if (!cache.has(key)) cache.set(key, fetchData(key));
  return cache.get(key);
}

// ✅ Bounded cache with LRU eviction
const cache = new LRUCache({ max: 1000 });
```

### Profiling Quick Reference

```bash
# Python CPU profiling
py-spy top --pid 1234
py-spy record -o profile.svg --pid 1234

# Native/Linux profiling
perf record -g ./app && perf report

# Browser performance
# F12 → Performance → Record during slow interaction
```
<!-- IDX:TAXONOMY_PERFORMANCE_END -->

---

<!-- IDX:TAXONOMY_SECURITY_START -->
## ERROR TAXONOMY: SECURITY VULNERABILITIES

**Symptoms:** Injection, auth bypass, data exposure, unauthorized access.

### SQL Injection

```typescript
// ❌ CRITICAL: SQL injection
async function getUserByName(name: string) {
  const query = `SELECT * FROM users WHERE name = '${name}'`;
  return db.query(query); // name = "'; DROP TABLE users; --"
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

### XSS (Cross-Site Scripting)

```typescript
// ❌ CRITICAL: Injects raw HTML
function renderUserBio(bio: string) {
  container.innerHTML = bio;
}

// ✅ FIX A: Use textContent for plain text
function renderUserBio(bio: string) {
  container.textContent = bio;
}

// ✅ FIX B: Sanitize if HTML is required
import DOMPurify from 'dompurify';
function renderUserBio(bio: string) {
  container.innerHTML = DOMPurify.sanitize(bio, {
    ALLOWED_TAGS: ['b', 'i', 'em', 'strong', 'a'],
    ALLOWED_ATTR: ['href'],
  });
}
```

### Secrets Exposure

```typescript
// ❌ CRITICAL: Hardcoded secret in source code
const API_KEY = 'sk-live-abc123def456'; // exposed in git history forever

// ✅ FIX: Environment variables + validation + never log
import { z } from 'zod';
const EnvSchema = z.object({
  API_KEY: z.string().min(10),
});
const env = EnvSchema.parse(process.env);
// Never log secrets — log redacted version only
logger.info('API call', { url, apiKeyPrefix: env.API_KEY.slice(0, 4) + '***' });
```

### Security Scan Pipeline

```bash
# Layer 1: Fast pattern matching
semgrep --config=p/default --config=p/owasp-top-ten .

# Layer 2: Deep semantic analysis
codeql database create codeql-db --language=javascript --source-root=.
codeql database analyze codeql-db javascript-security-extended --format=sarif-latest --output=results.sarif

# Layer 3: Python-specific
bandit -r src/ -ll

# Layer 4: Secrets
gitleaks detect --source=. --verbose
```
<!-- IDX:TAXONOMY_SECURITY_END -->

---

<!-- IDX:TAXONOMY_HEISENBUG_START -->
## ERROR TAXONOMY: HEISENBUGS

**Symptoms:** Bug appears only under observation, changes behavior when logged, disappears in debugger.

### Characteristics
- Timing-dependent
- Changes when print statements are added (print delays alter race outcomes)
- Only appears under load or specific hardware
- Disappears in optimized builds but appears in debug builds (or vice versa)

### Heisenbug Hunting Strategy

```markdown
□ Use record/replay (rr) to capture failure deterministically
□ Minimize external dependencies and noise
□ Run in a loop until failure: `while true; do ./test; done`
□ Check for uninitialized memory (MSan, Valgrind)
□ Look for compiler optimization-sensitive code
□ Verify threading assumptions with TSan / helgrind
```

### Record & Replay Example

```bash
# Capture the bug once
rr record ./my_flaky_test

# Replay infinitely — timing is now deterministic
rr replay
# In gdb: use reverse-continue, reverse-step to find divergence point
```

### Common Causes
- Uninitialized variables (MSan / Valgrind)
- Data races (TSan)
- Use of `Date.now()` or `Math.random()` without mocking
- Non-deterministic iteration order over Maps/Sets/objects
- Signal/interrupt handlers
<!-- IDX:TAXONOMY_HEISENBUG_END -->

---

# PART III: DOMAIN-SPECIFIC DEBUGGING

<!-- IDX:FRONTEND_FORENSICS_START -->
## DOMAIN-SPECIFIC: FRONTEND FORENSICS (12 FAILURE MODES)

**Purpose:** Systematic diagnosis for web/mobile frontend bugs when the tech stack is unknown or complex.

### Forensics Protocol

**Phase 1: Environment Fingerprinting**
- Request DevTools → Sources tab screenshot
- Request Console output during error
- View Page Source → scroll to bottom for bundler signatures

**Phase 2: Error Classification**
Determine if it's: Interaction / Rendering / Data Flow / Performance / Browser-Device.

**Phase 3: Targeted Evidence Collection**
Request specific diagnostics based on error type.

**Phase 4: Isolation Testing**
Provide 3-5 tests to narrow the domain.

---

### Failure Mode 1: State Management Failures
- Stale closures capturing old state
- Race conditions in async state updates
- State mutations instead of immutable updates
- Context providers not wrapping components

*Diagnostic:* "Log the state value in component vs global store."

```typescript
// ❌ Stale closure in useEffect
useEffect(() => {
  const timer = setInterval(() => {
    setCount(count + 1); // count is always initial value
  }, 1000);
}, []);

// ✅ Functional update
useEffect(() => {
  const timer = setInterval(() => {
    setCount(prev => prev + 1);
  }, 1000);
  return () => clearInterval(timer);
}, []);
```

### Failure Mode 2: Component Lifecycle Issues
- `useEffect` missing dependencies
- Memory leaks from uncleaned timeouts/subscriptions
- Setting state on unmounted components
- Infinite re-render loops

*Diagnostic:* "Add console.log in render function — does it spam the console?"

### Failure Mode 3: Asynchronous Operations
- Promises not awaited properly
- Loading states not handled
- Error boundaries not catching async errors
- Race conditions between multiple API calls

*Diagnostic:* "Wrap operation in try/catch + loading spinner."

### Failure Mode 4: Network & API Issues
- CORS policy blocking requests
- API endpoints changed/deprecated
- Request timeouts
- Malformed request payloads

*Diagnostic:* "Copy as cURL from Network tab, test in Postman/terminal."

### Failure Mode 5: Responsive & Device Issues
- CSS viewport units causing mobile issues
- Touch events not handled
- Media queries breaking at specific breakpoints
- iOS Safari specific bugs (100vh issues)

*Diagnostic:* "Test in DevTools device simulation + real mobile device."

### Failure Mode 6: CSS & Styling Conflicts
- CSS specificity wars
- CSS-in-JS hydration mismatches
- Third-party CSS overriding styles
- CSS custom properties not supported

*Diagnostic:* "DevTools → Computed → check which styles are being overridden."

### Failure Mode 7: Build & Bundling Problems
- Environment variables not available in browser
- Import paths broken after build
- Code splitting causing loading errors
- Service worker caching old versions

*Diagnostic:* "Check DevTools → Sources for 404s, compare dev vs production."

### Failure Mode 8: Security & Permissions
- Content Security Policy blocking resources
- Cookie SameSite issues
- Local storage quota exceeded
- Browser blocking third-party scripts

*Diagnostic:* "Check DevTools → Security tab and Console for CSP violations."

### Failure Mode 9: Accessibility Barriers
- Focus trapped incorrectly
- Screen readers cannot access content
- Keyboard navigation broken
- Color contrast insufficient

*Diagnostic:* "Tab through the interface, use Lighthouse accessibility audit."

### Failure Mode 10: Browser Compatibility
- Modern JS features not polyfilled
- CSS Grid/Flexbox differences
- Date/Number formatting differences
- Web API not available in older browsers

*Diagnostic:* "Test in target browsers, check caniuse.com for features."

### Failure Mode 11: Performance Bottlenecks
- Heavy components causing jank
- Large bundle sizes
- Unoptimized images
- Excessive re-renders

*Diagnostic:* "DevTools → Performance tab, record during the slow operation."

### Failure Mode 12: Testing & Environment Issues
- Mock data vs real API differences
- Environment-specific configuration
- Different Node.js versions
- Dependency version conflicts

*Diagnostic:* "Compare package.json vs lockfile, check Node version."
<!-- IDX:FRONTEND_FORENSICS_END -->

---

<!-- IDX:BACKEND_API_START -->
## DOMAIN-SPECIFIC: BACKEND API DEBUGGING

**Purpose:** Debugging server-side APIs, services, and business logic.

### Backend Diagnostic Checklist

```markdown
□ Check server logs for stack traces and error codes
□ Verify request reaches the server (network tab / curl / mitmproxy)
□ Validate request payload shape matches expected input
□ Check authentication/authorization middleware
□ Verify database connection and query execution
□ Check for rate limiting or timeout configurations
□ Compare local vs production environment variables
```

### API Debugging Commands

```bash
# Test endpoint directly
curl -v -X POST http://localhost:3000/api/users \
  -H "Content-Type: application/json" \
  -d '{"name":"Test"}'

# Check server logs in real-time
tail -f /var/log/app.log | grep -i error

# Attach debugger to running Node process
ndb -p <pid>

# Attach strace to hanging API worker
strace -p <worker_pid> -e trace=network,read,write
```

### Common Backend Patterns

**Missing Input Validation:**
```typescript
// ❌ Trusts client input
app.post('/users', (req, res) => {
  const user = db.createUser(req.body);
  res.json(user);
});

// ✅ Validates with Zod
const CreateUserSchema = z.object({
  name: z.string().min(1),
  email: z.string().email(),
});
app.post('/users', (req, res) => {
  const input = CreateUserSchema.parse(req.body);
  const user = db.createUser(input);
  res.json(user);
});
```

**Race Condition in Database:**
```typescript
// ❌ Check-then-act race condition
if (await db.userExists(email)) {
  throw new Error('User exists');
}
await db.createUser({ email }); // Another request could slip in here

// ✅ Use unique constraint at database level
// CREATE UNIQUE INDEX idx_users_email ON users(email);
```
<!-- IDX:BACKEND_API_END -->

---

<!-- IDX:DATABASE_DEBUG_START -->
## DOMAIN-SPECIFIC: DATABASE DEBUGGING

**Purpose:** Query performance, schema mismatches, migration issues, and data corruption.

### Database Diagnostic Commands

```bash
# Slow query log (PostgreSQL)
SELECT * FROM pg_stat_statements ORDER BY mean_exec_time DESC LIMIT 10;

# Active connections and locks
SELECT * FROM pg_stat_activity;
SELECT * FROM pg_locks;

# Query plan analysis
EXPLAIN ANALYZE SELECT * FROM users WHERE email = 'test@example.com';

# Index usage
SELECT schemaname, tablename, indexname, idx_scan
FROM pg_stat_user_indexes
ORDER BY idx_scan DESC;
```

### Common Database Bugs

**N+1 Query:**
```python
# ❌ One query per related object
for order in Order.objects.all():
    print(order.customer.name)

# ✅ select_related / prefetch_related
for order in Order.objects.select_related('customer').all():
    print(order.customer.name)
```

**Missing Index:**
```sql
-- Check for sequential scans on large tables
EXPLAIN ANALYZE SELECT * FROM users WHERE email = 'x';
-- If it shows Seq Scan, add index:
CREATE INDEX CONCURRENTLY idx_users_email ON users(email);
```

**Migration Failure:**
```bash
# Check migration status
python manage.py showmigrations
# or
npx prisma migrate status

# Rollback strategy
python manage.py migrate app_name previous_migration
```
<!-- IDX:DATABASE_DEBUG_END -->

---

<!-- IDX:DISTRIBUTED_DEBUG_START -->
## DOMAIN-SPECIFIC: DISTRIBUTED SYSTEMS DEBUGGING

**Purpose:** Debugging microservices, distributed transactions, consensus failures, and network partitions.

### Distributed Debugging Principles

```markdown
□ Follow the request through all services (distributed tracing)
□ Check for timeouts and retry storms
□ Verify service discovery and load balancer health
□ Look for cascading failures and missing circuit breakers
□ Check consistency models (eventual vs strong)
□ Verify message queue depth and consumer lag
```

### Distributed Tracing

```bash
# Find trace ID from logs
rg "trace_id=abc123" logs/

# Zipkin/Jaeger query
curl "http://jaeger:16686/api/traces?service=checkout&traceID=abc123"
```

### Scalability Pattern Checklist (from awesome-scalability)

```markdown
□ Is it a thundering herd? → Add caching layer
□ Is it a cascading failure? → Add circuit breakers
□ Is it a hotspot/shard imbalance? → Rebalance data partitioning
□ Is backpressure missing? → Add queue management and rate limiting
□ Are there N+1 calls between services? → Batch requests or add BFF
□ Is consensus failing? → Check quorum, leader election logs
```

### Circuit Breaker Example

```typescript
// Without circuit breaker: one failing service brings down the caller
const result = await fetchFromUnreliableService(); // hangs indefinitely

// With circuit breaker
import CircuitBreaker from 'opossum';
const breaker = new CircuitBreaker(fetchFromUnreliableService, {
  timeout: 3000,
  errorThresholdPercentage: 50,
  resetTimeout: 30000,
});
const result = await breaker.fire();
```
<!-- IDX:DISTRIBUTED_DEBUG_END -->

---

<!-- IDX:MOBILE_DEBUG_START -->
## DOMAIN-SPECIFIC: MOBILE DEBUGGING

**Purpose:** iOS, Android, and React Native specific debugging.

### Mobile Diagnostic Checklist

```markdown
□ Reproduce on physical device (not just simulator)
□ Check OS-specific permissions (camera, location, notifications)
□ Verify push notification certificates and provisioning profiles
□ Check for memory warnings and app backgrounding behavior
□ Test on different screen sizes and orientations
□ Verify network behavior on cellular vs WiFi
□ Check for JavaScript bridge issues (React Native)
```

### React Native Specifics

```bash
# Shake device → Debug menu
# Enable Chrome debugging: Debug JS Remotely
# Check Metro bundler logs
npx react-native log-android
npx react-native log-ios

# Hermes profiling
# chrome://inspect → Hermes debugger
```

### iOS Debugging

```bash
# Device logs
xcrun simctl spawn booted log stream --level debug

# Crash logs
# Xcode → Window → Devices and Simulators → View Device Logs
```

### Android Debugging

```bash
# Logcat
adb logcat -s "ReactNative:*" "AndroidRuntime:*"

# Network inspection
adb shell settings put global http_proxy <proxy_ip>:<port>
```
<!-- IDX:MOBILE_DEBUG_END -->

---

# PART IV: SCENARIO-BASED TOOL MATRIX

<!-- IDX:SCENARIO_SLOW_START -->
## SCENARIO-BASED TOOL MATRIX: "IT'S SLOW"

### Web Frontend Slowness

**Primary Tools:**
- **Chrome DevTools Performance tab** — Record user interaction, analyze frame times, identify long tasks
- **Lighthouse** — Automated performance, accessibility, SEO audit
- **React DevTools Profiler** — Identify unnecessary re-renders

**Quick Workflow:**
```
1. F12 → Performance → Click Record
2. Perform the slow user action
3. Stop recording
4. Look for: Long Tasks (>50ms), Layout Thrashing, Forced Reflow
5. Check: Main thread blocked? Network waterfall slow? Large images?
```

**When NOT to use:** Don't use Performance tab for server-side slowness — use backend profilers instead.

### Backend API Slowness

**Primary Tools:**
- **mitmproxy** — Inspect payload sizes, unnecessary headers, slow responses
- **ndb** — Profile Node.js backend with Chrome DevTools
- **py-spy** — Sample Python processes without code changes
- **Django Debug Toolbar / APM tools** — Query analysis

**Commands:**
```bash
# Capture API traffic with timing
mitmdump -w capture.mitm

# Python profiling
py-spy top --pid $(pgrep -f "gunicorn")
py-spy record -o profile.svg --pid $(pgrep -f "gunicorn")
```

**Backend Slowness Checklist:**
```markdown
□ N+1 queries? → Check ORM query count
□ Missing database indexes? → EXPLAIN ANALYZE
□ Synchronous blocking calls? → Asyncify or use workers
□ Large payload serialization? → Profile JSON encoding
□ External API calls blocking? → Add timeouts, caching, async
□ Memory pressure causing GC pauses? → Heap analysis
```

### Python-Specific Slowness

**Tools:** `cProfile`, `py-spy`, `line_profiler`, `tracemalloc`

```bash
# Quick cProfile
python -m cProfile -s cumtime script.py

# Line-by-line profiling
kernprof -l -v script.py
# (requires @profile decorator)

# Memory growth tracking
python -c "
import tracemalloc
tracemalloc.start()
# ... run code ...
snapshot = tracemalloc.take_snapshot()
top_stats = snapshot.statistics('lineno')
for stat in top_stats[:10]:
    print(stat)
"
```

### System-Level Slowness

**Tools:** `perf`, `strace`, `iotop`, `htop`, `vmstat`

```bash
# CPU profiling with flame graphs
perf record -g ./app
perf script | stackcollapse-perf.pl | flamegraph.pl > perf.svg

# Identify disk I/O bottleneck
iotop -o -b -n 5

# System-wide resource view
vmstat 1 10
```

### Distributed System Slowness

**Patterns from awesome-scalability:**
- **Thundering herd** → Check cache hit rates (Redis/Memcached metrics)
- **Cascading failure** → Check circuit breaker states, downstream latency
- **Shard imbalance** → Check database query distribution across shards
- **Missing backpressure** → Check queue depths (Kafka lag, RabbitMQ messages)

```bash
# Check Kafka consumer lag
kafka-consumer-groups.sh --bootstrap-server localhost:9092 --describe --group my-group

# Redis slow log
redis-cli SLOWLOG GET 10
```
<!-- IDX:SCENARIO_SLOW_END -->

---

<!-- IDX:SCENARIO_CRASH_START -->
## SCENARIO-BASED TOOL MATRIX: "IT CRASHES"

### Node.js Crashes

**Primary Tools:**
- **ndb** — Improved Node debugging with Chrome DevTools integration
- **Chrome DevTools Memory profiler** — Heap snapshots for OOM
- **Clinic.js** — Node.js performance and memory profiling

**Commands:**
```bash
# Run with ndb
ndb node server.js

# Or debug npm scripts
ndb npm run unit

# Generate heap snapshot on SIGUSR2
node --expose-gc server.js
kill -USR2 <pid>
```

**Node Crash Patterns:**
```markdown
□ Unhandled promise rejection → Add catch blocks, use process.on('unhandledRejection')
□ OOM / heap exhausted → Analyze heap snapshots, check for retained closures
□ Stack overflow → Check for infinite recursion
□ Native module segfault → Use lldb/gdb with core dump
```

### Python Crashes

**Primary Tools:**
- **pdb / ipdb** — Interactive debugging
- **icecream** — Quick state inspection without breakpoints
- **faulthandler** — Print Python traceback on segfault

```python
# Enable faulthandler for production crashes
import faulthandler
faulthandler.enable()

# Quick state inspection
from icecream import ic
ic(user.profile.name)  # prints: ic| user.profile.name: 'Alice'

# Interactive debugging
import pdb; pdb.set_trace()
```

### Native / Binary Crashes

**Primary Tools:**
- **pwndbg** — GDB/LLDB enhancement for binary debugging
- **valgrind memcheck** — Memory error detection
- **AddressSanitizer (ASan)** — Fast memory corruption detection
- **rr** — Record and deterministic replay

```bash
# Debug with pwndbg
gdb -q ./binary
# pwndbg loads automatically
# Commands: context, telescope, vmmap, backtrace

# Record crash for infinite replay
rr record ./binary
rr replay
# In replay: reverse-continue, reverse-step, watchpoints

# Valgrind for memory errors
valgrind --leak-check=full --track-origins=yes ./binary
```

### Cross-Language Crash Strategy

**For any language, use record/replay when available:**
- C/C++: `rr` (Linux)
- Browser: `Replay.io`
- Any: `UndoDB` (commercial)

**Why record/replay for crashes:**
- Crash happens once, replay infinitely
- Timing becomes deterministic
- Can reverse-execute to find root cause
- No observer effect from debugging
<!-- IDX:SCENARIO_CRASH_END -->

---

<!-- IDX:SCENARIO_LOGIC_START -->
## SCENARIO-BASED TOOL MATRIX: "WRONG OUTPUT"

### Python Logic Errors

**Primary Tool:** `icecream` for intermediate value inspection.

```python
from icecream import ic

def calculate_total(items):
    ic(items)  # See exact input
    subtotal = sum(item['price'] * item['qty'] for item in items)
    ic(subtotal)  # See intermediate value
    tax = subtotal * 0.08
    ic(tax)  # See tax calculation
    return subtotal + tax
```

**Alternative:** `python -m pdb script.py` with breakpoints at each calculation step.

### Web Logic Errors

**Primary Tools:**
- **mitmproxy** — Inspect actual JSON being sent/received
- **Chrome DevTools Sources** — Step through JavaScript line by line
- **ndb** — Step through Node backend logic

```bash
# Intercept and modify requests on the fly
mitmweb
# Browse to http://localhost:8081
# Edit request/response in real-time to test hypotheses
```

### Systems Logic Errors

**Primary Tools:**
- **Time-travel debuggers** (`rr`, `UndoDB`) — Find state divergence
- **GDB watchpoints** — Break when variable changes unexpectedly
- **Binary diff tools** — Compare working vs broken binary states

```bash
# GDB watchpoint example
(gdb) watch variable_name
(gdb) continue
# Breaks whenever variable_name changes
```

### Data Pipeline Logic Errors

**Checkpoints at each transformation:**
```typescript
function debugPipeline(input: unknown) {
  console.log(`[PIPELINE] Input:`, JSON.stringify(input, null, 2));
  const step1 = parseInput(input);
  console.log(`[PIPELINE] After parse:`, step1);
  const step2 = validate(step1);
  console.log(`[PIPELINE] After validate:`, step2);
  const step3 = transform(step2);
  console.log(`[PIPELINE] After transform:`, step3);
  return step3;
}
```
<!-- IDX:SCENARIO_LOGIC_END -->

---

<!-- IDX:SCENARIO_ENV_START -->
## SCENARIO-BASED TOOL MATRIX: "WORKS ON MY MACHINE"

### Container Inspection

```bash
# Enter running container
docker exec -it <container> /bin/sh

# Compare container env to local
docker exec <container> env | sort > container_env.txt
env | sort > local_env.txt
diff local_env.txt container_env.txt

# Check file differences
docker diff <container>
```

### Network Differences

```bash
# Capture request from both environments
curl -v -w "\nHTTP_CODE:%{http_code}\nTIME_TOTAL:%{time_total}\n" \
  https://api.example.com/endpoint > local_capture.txt

# Compare responses
diff local_capture.txt prod_capture.txt
```

### Environment Parity Checklist

```markdown
□ OS and kernel version
□ Runtime versions (Node, Python, Java, Go)
□ Dependency versions (compare lockfiles)
□ Environment variables and secrets
□ Database schema and migration state
□ Feature flags and configuration
□ Network access and firewall rules
□ File permissions and ownership
```

### Quick Env Diff Script

```bash
#!/bin/bash
# env-diff.sh — Compare two environments

echo "=== Runtime Versions ==="
node -v; npm -v; python --version; go version

echo "=== Git State ==="
git log --oneline -1
git status --short

echo "=== Key Env Vars ==="
env | grep -E "NODE_ENV|DATABASE_URL|API_KEY|PORT|STAGE" | sort

echo "=== Installed Packages (top-level) ==="
npm list --depth=0 2>/dev/null || pip list --format=freeze | head -20
```
<!-- IDX:SCENARIO_ENV_END -->

---

<!-- IDX:SCENARIO_FLAKY_START -->
## SCENARIO-BASED TOOL MATRIX: INTERMITTENT/FLAKY BUGS

### Flaky Test Stabilization

**Common Causes:**
- Timing dependencies (waiting for API, animation)
- Shared mutable state (database, cache, global vars)
- Non-deterministic order (Set iteration, async race)
- External dependencies (network, third-party APIs)
- Date/time dependencies
- Browser-specific rendering

**Fixes:**
```typescript
// ❌ Flaky: setTimeout
setTimeout(() => {
  expect(screen.getByText('Done')).toBeInTheDocument();
}, 1000);

// ✅ Stable: waitFor with condition
await waitFor(() => {
  expect(screen.getByText('Done')).toBeInTheDocument();
});
```

### Race Condition Tools

```bash
# C/C++ data races
valgrind --tool=helgrind ./app
# or
clang -fsanitize=thread -g -O1 app.c -o app_tsan
./app_tsan

# Go data races
go run -race ./...
```

### Forcing Determinism

```bash
# JavaScript: freeze time
// jest: jest.useFakeTimers()
// vitest: vi.useFakeTimers()

# Python: freeze time
from freezegun import freeze_time
@freeze_time("2024-01-01")
def test_time_dependent_logic():
    ...

# C: deterministic random for tests
// Replace rand() with seeded deterministic generator in test mode
```

### Heisenbug Hunting with rr

```bash
# Run test in a loop until failure
while ! rr record ./flaky_test; do sleep 1; done

# Once captured, replay and analyze
rr replay
(gdb) reverse-continue
(gdb) reverse-step
```
<!-- IDX:SCENARIO_FLAKY_END -->

---

# PART V: PRODUCTION EMERGENCY PROTOCOLS

<!-- IDX:PROD_LINUX_START -->
## PRODUCTION EMERGENCY PROTOCOL: LINUX/SERVER

**Rule:** Stabilize first, investigate second. These commands are for triage, not root cause analysis.

### The 30-Second Triage

```bash
# 1. Kernel errors (hardware, OOM killer)
dmesg | tail -n 20

# 2. Attach to hanging process
strace -p <PID> -e trace=network,read,write

# 3. Who's using the port
lsof -i :<PORT> || ss -tulpn | grep :<PORT>

# 4. Active connections
netstat -tulpn || ss -tulpn

# 5. Resource bottlenecks
htop || top -o %CPU -n 1
iotop -o -b -n 1 || iostat -x 1 1

# 6. Service logs
journalctl -u <service> -f -n 50

# 7. Disk usage (prevent disk-full crashes)
df -h && du -sh /var/log/* 2>/dev/null | sort -rh | head -5
```

### Process Emergency Commands

```bash
# Find processes by name
ps aux | grep <process_name>

# Kill safely (SIGTERM first)
kill -15 <pid>
# Wait 10s, then:
kill -9 <pid>  # SIGKILL as last resort

# Check open files of a process
lsof -p <pid>

# Check process tree
pstree -p <pid>
```

### Memory Emergency

```bash
# Show memory usage by process
ps aux --sort=-%mem | head -10

# Show OOM score (who gets killed first)
cat /proc/<pid>/oom_score

# Drop caches (last resort, causes temporary slowdown)
echo 3 | sudo tee /proc/sys/vm/drop_caches
```

### When NOT to Use These
- Don't `kill -9` databases or transaction-heavy services without understanding in-flight operations
- Don't drop caches on systems with heavy I/O without warning
- Don't run `strace` on high-throughput production processes for extended periods (major slowdown)
<!-- IDX:PROD_LINUX_END -->

---

<!-- IDX:PROD_NETWORK_START -->
## PRODUCTION EMERGENCY PROTOCOL: NETWORK

### Traffic Capture

```bash
# Capture all traffic for later analysis
tcpdump -i any -w capture.pcap -nn -s0

# Capture specific port
tcpdump -i any port 443 -w https.pcap

# Capture specific host
tcpdump -i any host api.example.com -w api.pcap
```

### HTTP Diagnostics

```bash
# Verbose HTTP with timing
curl -v -w "\nDNS:%{time_namelookup}\nConnect:%{time_connect}\nTTFB:%{time_starttransfer}\nTotal:%{time_total}\n" \
  -o /dev/null -s https://api.example.com/health

# Check headers only
curl -I https://api.example.com/health

# Follow redirects
curl -L -v https://bit.ly/xxx
```

### Routing & DNS

```bash
# Trace route with ICMP
traceroute -I api.example.com

# Better: mtr (continuous traceroute)
mtr -r -c 100 api.example.com

# DNS resolution
nslookup api.example.com
dig +trace api.example.com
dig +short api.example.com

# Check DNS propagation
dig @8.8.8.8 api.example.com
```

### Connection State

```bash
# Connection counts by state
ss -ant | awk '{print $1}' | sort | uniq -c

# SYN flood detection
ss -s

# Check firewall rules
iptables -L -n | grep <port>
# or
ufw status
```
<!-- IDX:PROD_NETWORK_END -->

---

<!-- IDX:PROD_LOGS_START -->
## PRODUCTION EMERGENCY PROTOCOL: LOG ANALYSIS

### Quick Log Recipes

```bash
# Top errors
grep -iE "ERROR|WARN|FATAL|EXCEPTION" app.log | head -20

# Error frequency by hour
awk '{print $1 ":" $2}' app.log | cut -d: -f1,2 | sort | uniq -c | sort -rn | head

# Find slow requests
awk '$8 > 5000 {print}' access.log  # responses > 5000ms

# Track a specific user/request
grep "user_id=12345" app.log | tail -50

# Correlation ID tracking across microservices
grep "trace_id=abc123" logs/service-a.log logs/service-b.log logs/service-c.log
```

### Structured Log Parsing

```bash
# JSON logs: extract error count by endpoint
cat app.log | jq -r 'select(.level=="ERROR") | .endpoint' | sort | uniq -c | sort -rn

# Log rate over time
awk '/ERROR/{print $1}' app.log | uniq -c
```

### Log Aggregation One-Liners

```bash
# Unique error messages
grep ERROR app.log | sort | uniq -c | sort -rn | head -20

# Stack trace extraction (multiline)
awk '/Exception/{flag=1; print} /^[[:space:]]/{if(flag) print} /^[^[:space:]]/{if(flag && !/Exception/){flag=0}}' app.log
```
<!-- IDX:PROD_LOGS_END -->

---

<!-- IDX:PROD_CONTAINERS_START -->
## PRODUCTION EMERGENCY PROTOCOL: CONTAINERS & KUBERNETES

### Docker Triage

```bash
# Running containers
docker ps --format "table {{.Names}}\t{{.Status}}\t{{.Ports}}"

# Container logs
docker logs -f <container> --tail 100

# Container resource usage
docker stats --no-stream

# Execute into container
docker exec -it <container> sh

# Inspect container config
docker inspect <container>
```

### Kubernetes Triage

```bash
# Pod status
kubectl get pods --all-namespaces
kubectl describe pod <pod-name> -n <namespace>

# Pod logs
kubectl logs -f <pod-name> --tail=100
kubectl logs -f deployment/<name> --tail=100

# Previous container logs (if crashed/restarted)
kubectl logs <pod-name> --previous

# Events (scheduling failures, image pull errors)
kubectl get events --sort-by='.lastTimestamp' | tail -20

# Resource usage
kubectl top nodes
kubectl top pods

# Execute into pod
kubectl exec -it <pod-name> -- /bin/sh
```

### Container-Specific Issues

```markdown
□ ImagePullBackOff → Check image tag exists, registry auth
□ CrashLoopBackOff → Check logs of previous container, resource limits
□ OOMKilled → Increase memory limit or fix memory leak
□ Evicted → Disk pressure or memory pressure on node
□ Pending → Insufficient resources, taints, affinity rules
```
<!-- IDX:PROD_CONTAINERS_END -->

---

# PART VI: LANGUAGE-SPECIFIC ARSENALS

<!-- IDX:LANG_PYTHON_START -->
## LANGUAGE-SPECIFIC ARSENAL: PYTHON

### Essential Python Toolkit

| Tool | Install | Purpose | Quick Command |
|------|---------|---------|---------------|
| **pytest** | `pip install pytest` | Test runner | `pytest -xvs` |
| **pytest-cov** | `pip install pytest-cov` | Coverage | `pytest --cov=src` |
| **mypy** | `pip install mypy` | Type checking | `mypy src/` |
| **ruff** | `pip install ruff` | Lint + format | `ruff check --fix .` |
| **icecream** | `pip install icecream` | Smart print | `ic(variable)` |
| **pdb / ipdb** | Built-in / `pip install ipdb` | Debugger | `python -m pdb script.py` |
| **py-spy** | `pip install py-spy` | Sampling profiler | `py-spy top --pid 1234` |
| **bandit** | `pip install bandit` | Security linter | `bandit -r src/` |
| **vulture** | `pip install vulture` | Dead code | `vulture src/` |
| **hypothesis** | `pip install hypothesis` | Property tests | `@given(st.text())` |
| **mutmut** | `pip install mutmut` | Mutation testing | `mutmut run` |
| **tracemalloc** | Built-in | Memory tracking | `tracemalloc.start()` |

### Python Debugging Patterns

```python
# pdb essentials
import pdb; pdb.set_trace()
# n = next line
# s = step into
# c = continue
# l = list source
# p variable = print variable

# icecream patterns
from icecream import ic
ic(foo(123))        # prints: ic| foo(123): 456
ic()                # prints: ic| example.py:12 in function_name()

# faulthandler for segfaults
import faulthandler
faulthandler.enable()
```

### Python Mutable Default Argument Bug

```python
# ❌ BROKEN: Default list created ONCE
 def add_item(item: str, items: list = []) -> list:
     items.append(item)
     return items

# ✅ CORRECT: Use None sentinel
 def add_item(item: str, items: list[str] | None = None) -> list[str]:
     if items is None:
         items = []
     items.append(item)
     return items
```

### Python Validation Pipeline

```bash
ruff check . && \
mypy src/ --ignore-missing-imports && \
pytest -x --cov=src --cov-fail-under=80 && \
bandit -r src/ -ll && \
semgrep --config=p/default src/ --error
```
<!-- IDX:LANG_PYTHON_END -->

---

<!-- IDX:LANG_JS_TS_START -->
## LANGUAGE-SPECIFIC ARSENAL: JAVASCRIPT / TYPESCRIPT / NODE

### Essential JS/TS Toolkit

| Tool | Install | Purpose | Quick Command |
|------|---------|---------|---------------|
| **Vitest** | `npm i -D vitest` | Test runner | `npx vitest run` |
| **Jest** | `npm i -D jest` | Test runner (legacy) | `npx jest` |
| **Biome** | `npm i -D @biomejs/biome` | Lint + format | `npx biome check --write .` |
| **tsc** | Built-in with TS | Type check | `npx tsc --noEmit` |
| **ESLint** | `npm i -D eslint` | Linting (advanced plugins) | `npx eslint . --fix` |
| **ndb** | `npm i -g ndb` | Node debugger | `ndb node server.js` |
| **Playwright** | `npm init playwright@latest` | E2E testing | `npx playwright test` |
| **fast-check** | `npm i -D fast-check` | Property tests | Integrates with Vitest |
| **Stryker** | `npm i -D @stryker-mutator/core` | Mutation tests | `npx stryker run` |
| **Clinic.js** | `npm i -D clinic` | Node profiling | `clinic doctor -- node app.js` |

### Node.js Debugging

```bash
# Built-in inspect
node --inspect-brk server.js
# Open chrome://inspect

# ndb (better experience)
ndb server.js

# Heap snapshot
node --expose-gc -e "require('v8').writeHeapSnapshot()"
```

### TypeScript Type Mismatch Prevention

```typescript
// ❌ Dangerous: no runtime validation
async function getUser(id: string): Promise<ApiUser> {
  const res = await fetch(`/api/users/${id}`);
  return res.json() as ApiUser;
}

// ✅ Safe: Zod validation at runtime
import { z } from 'zod';
const ApiUserSchema = z.object({
  id: z.string(),
  name: z.string(),
  email: z.string().email(),
});
async function getUser(id: string) {
  const res = await fetch(`/api/users/${id}`);
  return ApiUserSchema.parse(await res.json());
}
```

### JS/TS Validation Pipeline

```bash
npx biome check . && \
npx tsc --noEmit && \
npx vitest run --coverage && \
npm audit --audit-level=high && \
npx semgrep --config=p/default src/ --error
```
<!-- IDX:LANG_JS_TS_END -->

---

<!-- IDX:LANG_REACT_START -->
## LANGUAGE-SPECIFIC ARSENAL: REACT / FRONTEND

### Essential Frontend Toolkit

| Tool | Install | Purpose | Quick Command |
|------|---------|---------|---------------|
| **Chrome DevTools** | Built-in | DOM/Network/Perf/Memory | F12 |
| **React DevTools** | Browser extension | Component/Hooks inspection | Extensions store |
| **Playwright** | `npm init playwright@latest` | E2E automation | `npx playwright test` |
| **axe-core** | `npm i -D jest-axe` | Accessibility testing | `expect(results).toHaveNoViolations()` |
| **Lighthouse** | Built-in Chrome | Performance audit | DevTools → Lighthouse |

### React DevTools Workflows

```markdown
□ Components tab: Inspect props and state
□ Profiler tab: Record renders, find unnecessary re-renders
□ Hooks inspector: Check dependency arrays and hook values
□ "Highlight updates" option: See which components re-render
```

### Common React Bug Fixes

**Stale Closure in useEffect:**
```typescript
// ❌ Stale count
useEffect(() => {
  const timer = setInterval(() => setCount(count + 1), 1000);
}, []);

// ✅ Functional update
useEffect(() => {
  const timer = setInterval(() => setCount(c => c + 1), 1000);
  return () => clearInterval(timer);
}, []);
```

**Object Identity Causing Infinite Loop:**
```typescript
// ❌ New object every render
useEffect(() => {
  fetchData({ pageSize: 10, filters });
}, [{ pageSize: 10, filters }]); // infinite loop

// ✅ Destructure to primitives
const { search, category } = filters;
useEffect(() => {
  fetchData({ pageSize: 10, filters: { search, category } });
}, [search, category]);
```

**Key Prop Bugs:**
```typescript
// ❌ Using index as key
{todos.map((todo, index) => <TodoItem key={index} todo={todo} />)}

// ✅ Stable unique ID
{todos.map((todo) => <TodoItem key={todo.id} todo={todo} />)}
```
<!-- IDX:LANG_REACT_END -->

---

<!-- IDX:LANG_C_CPP_RUST_START -->
## LANGUAGE-SPECIFIC ARSENAL: C / C++ / RUST

### Essential Systems Toolkit

| Tool | Install | Purpose | Quick Command |
|------|---------|---------|---------------|
| **gdb + pwndbg** | `git clone pwndbg` | Enhanced debugger | `gdb -q ./binary` |
| **lldb + pwndbg** | Built-in macOS | Enhanced debugger | `lldb ./binary` |
| **valgrind** | Package manager | Memory/thread analysis | `valgrind --leak-check=full ./app` |
| **clang ASan** | Clang | Address sanitizer | `clang -fsanitize=address file.c -o file` |
| **clang TSan** | Clang | Thread sanitizer | `clang -fsanitize=thread file.c -o file` |
| **clang MSan** | Clang | Memory sanitizer | `clang -fsanitize=memory file.c -o file` |
| **clang UBSan** | Clang | Undefined behavior | `clang -fsanitize=undefined file.c -o file` |
| **perf** | Built-in Linux | Hardware profiling | `perf record -g ./app` |
| **rr** | Package manager | Record & replay | `rr record ./binary` |
| **AFL++** | Package manager | Fuzzing | `afl-fuzz -i seeds/ -o out/ -- ./target @@` |
| **Infer** | `brew install infer` | Static analysis | `infer run -- make` |
| **cargo** | rustup.rs | Rust build + test | `cargo test` |
| **Clippy** | rustup | Rust linter | `cargo clippy` |

### C/C++ Memory Debugging

```bash
# Valgrind comprehensive check
valgrind --leak-check=full --show-leak-kinds=all \
  --track-origins=yes --error-exitcode=1 ./my_app

# AddressSanitizer (much faster than Valgrind)
clang -fsanitize=address,undefined -fno-sanitize-recover=all \
  -fno-omit-frame-pointer -g -O1 app.c -o app_asan
ASAN_OPTIONS=detect_leaks=1 ./app_asan

# ThreadSanitizer
c clang -fsanitize=thread -g -O1 app.c -o app_tsan
./app_tsan
```

### Rust Debugging

```bash
# Run with backtrace on panic
RUST_BACKTRACE=1 cargo run

# Run tests
 cargo test

# Clippy lints
 cargo clippy -- -D warnings

# Format check
 cargo fmt --check
```

### Systems Debugging Best Practices

```markdown
□ Always compile with -g for debug symbols
□ Use -fno-omit-frame-pointer for accurate stack traces
□ Run ASan/UBSan in CI on every commit
□ Run Valgrind before releases
□ Use rr for intermittent crashes
□ Never ship C/C++ without memory testing
```
<!-- IDX:LANG_C_CPP_RUST_END -->

---

<!-- IDX:LANG_JAVA_GO_START -->
## LANGUAGE-SPECIFIC ARSENAL: JAVA / GO

### Java Essential Toolkit

| Tool | Install | Purpose | Quick Command |
|------|---------|---------|---------------|
| **JUnit 5** | Maven/Gradle | Testing | `mvn test` |
| **SpotBugs** | Maven plugin | Bug finder | `mvn spotbugs:check` |
| **PMD** | Maven plugin | Code quality | `mvn pmd:check` |
| **CodeQL** | GitHub CLI | Security analysis | `codeql database create` |
| **jcmd / jstack** | JDK built-in | Thread dumps | `jstack <pid>` |
| **jmap** | JDK built-in | Heap dumps | `jmap -dump:format=b,file=heap.hprof <pid>` |

### Go Essential Toolkit

| Tool | Install | Purpose | Quick Command |
|------|---------|---------|---------------|
| **go test** | Built-in | Testing | `go test ./...` |
| **go vet** | Built-in | Static analysis | `go vet ./...` |
| **golangci-lint** | `go install` | Comprehensive linting | `golangci-lint run` |
| **govulncheck** | `go install` | Vulnerability scanning | `govulncheck ./...` |
| **dlv** | `go install` | Debugger | `dlv debug` |
| **pprof** | Built-in | Profiling | `go tool pprof` |

### Java Memory Debugging

```bash
# Heap dump
jmap -dump:live,format=b,file=heap.hprof <pid>
# Analyze with Eclipse MAT or VisualVM

# Thread dump
jstack -l <pid > threads.txt

# GC logs
java -Xlog:gc*:file=gc.log:time,uptime,level,tags:filecount=5,filesize=10m -jar app.jar
```

### Go Race Detection

```bash
# Built-in race detector
go run -race ./...
go test -race ./...
```

### Go Profiling

```bash
# CPU profile
go test -cpuprofile=cpu.out -bench=.
go tool pprof cpu.out

# Memory profile
go test -memprofile=mem.out -bench=.
go tool pprof mem.out
```
<!-- IDX:LANG_JAVA_GO_END -->

---

<!-- IDX:LANG_SHELL_START -->
## LANGUAGE-SPECIFIC ARSENAL: SHELL SCRIPTS

### Essential Shell Toolkit

| Tool | Install | Purpose | Quick Command |
|------|---------|---------|---------------|
| **ShellCheck** | `brew/apt install shellcheck` | Static analysis | `shellcheck script.sh` |
| **shfmt** | `brew/apt install shfmt` | Formatter | `shfmt -w script.sh` |
| **bashate** | `pip install bashate` | Style checker | `bashate script.sh` |

### ShellCheck Usage

```bash
# Basic check
shellcheck deploy.sh

# Check all scripts
shellcheck scripts/*.sh

# CI integration (fails on warnings)
shellcheck -f json scripts/*.sh > shellcheck-report.json
```

### Critical Anti-Pattern: The `eval` Problem

**Why it's dangerous:** Code injection, syntax errors with special characters, unpredictable behavior with user input.

```bash
# ❌ CRITICAL: eval with user input
# If user_input="file.txt; rm -rf /", this deletes the system
eval "cat $user_input"

# ✅ SAFE: Use arrays
cmd=(cat "$user_input")
"${cmd[@]}"

# ✅ SAFE: Direct execution
cat "$user_input"
```

### Word Splitting and Globbing

```bash
file="my file.txt"

# ❌ Tries to cat "my" and "file.txt" separately
cat $file

# ✅ Correctly handles spaces and glob characters
cat "$file"
```
**Rule:** Always quote variables unless you specifically want word splitting.

### Command Substitution

```bash
# ❌ Legacy backticks — hard to nest
output=`command`

# ✅ Modern syntax — easy to nest
output=$(command)
output=$(command $(subcommand))
```

### Error Handling Template

```bash
#!/usr/bin/env bash
set -euo pipefail
# -e: Exit on error
# -u: Error on undefined variables
# -o pipefail: Catch errors in pipelines

# Cleanup on exit
cleanup() {
    # Remove temp files, restore state, etc.
    rm -f "$temp_file"
}
trap cleanup EXIT
```

### Reading Files Line by Line

```bash
# ❌ Breaks on spaces
for line in $(cat file); do
    echo "$line"
done

# ✅ Preserves exact lines including spaces
while IFS= read -r line; do
    echo "$line"
done < file
```

### Checking Commands Exist

```bash
if command -v program &> /dev/null; then
    echo "Program exists"
else
    echo "Program not found"
    exit 1
fi
```

### Path Handling

```bash
# Get script directory (works through symlinks)
SCRIPT_DIR="$(cd "$(dirname "${BASH_SOURCE[0]}")" && pwd)"

# Create temp file with guaranteed cleanup
temp_file=$(mktemp)
trap "rm -f $temp_file" EXIT
```

### Color Output Safely

```bash
if [[ -t 1 ]]; then
    RED='\033[0;31m'
    GREEN='\033[0;32m'
    NC='\033[0m'
else
    RED=''
    GREEN=''
    NC=''
fi

echo -e "${RED}Error${NC}: Something failed"
```

### Argument Parsing

**Simple manual parser:**
```bash
while [[ $# -gt 0 ]]; do
    case $1 in
        -f|--file)
            FILE="$2"
            shift 2
            ;;
        -v|--verbose)
            VERBOSE=1
            shift
            ;;
        *)
            POSITIONAL+=("$1")
            shift
            ;;
    esac
done
```

**Advanced with getopts:**
```bash
while getopts "f:v" opt; do
    case $opt in
        f) FILE="$OPTARG" ;;
        v) VERBOSE=1 ;;
        *) exit 1 ;;
    esac
done
```

### URL / Path Encoding

```bash
# Encode for URL
encoded=$(printf '%s' "$string" | jq -sRr @uri)

# Decode URL
decoded=$(printf '%b' "${encoded//%/\\x}")
```

### Shell Testing Checklist

Before marking bash code as complete:
- [ ] Test with spaces in filenames
- [ ] Test with special characters: `& | ; $ ( )`
- [ ] Test with empty input
- [ ] Test with very long input
- [ ] Test error paths
- [ ] Test on both macOS and Linux (if applicable)

### Quick Safety Rules

```markdown
□ Always use `set -euo pipefail`
□ Quote ALL variables: `"$var"`
□ Avoid `eval()` completely — use arrays or direct execution
□ Use `[[ ]]` instead of `[ ]` for Bash conditionals
□ Check command existence: `command -v tool &>/dev/null`
□ Use `mktemp` for temporary files with `trap ... EXIT`
□ Prefer `$(command)` over backticks
□ Use `while IFS= read -r line` instead of `for line in $(cat file)`
```
<!-- IDX:LANG_SHELL_END -->

---

# PART VII: ADVANCED DETECTION LAYERS

<!-- IDX:LAYER_STATIC_START -->
## ADVANCED DETECTION: LAYER 1 — STATIC ANALYSIS

### Semgrep

**What:** Pattern-matching static analyzer (30+ languages).  
**When:** Every commit, pre-commit hooks, security audits.  
**When NOT:** Don't expect deep multi-step data flow analysis (use CodeQL for that).  
**Repo:** https://github.com/returntocorp/semgrep

```bash
# Quick security scan
semgrep --config=p/default --config=p/owasp-top-ten .

# CI mode (strict)
semgrep --config=p/default src/ --error

# Custom rule example
semgrep --config .semgrep/rules.yml .
```

### CodeQL

**What:** Semantic code analysis engine using declarative QL language.  
**When:** Large codebases, security audits, compliance.  
**When NOT:** Overkill for small projects or quick checks (use Semgrep instead).  
**Repo:** https://github.com/github/codeql

```bash
# Create database
codeql database create codeql-db --language=javascript --source-root=.

# Analyze
codeql database analyze codeql-db javascript-security-extended \
  --format=sarif-latest --output=results.sarif
```

### Facebook Infer

**What:** Static analyzer based on separation logic and abstract interpretation.  
**When:** Critical C/C++/Java codebases where correctness is paramount.  
**When NOT:** Not worth setup cost for small or low-stakes projects.  
**Repo:** https://github.com/facebook/infer

```bash
# C/C++ with Make
infer run -- make

# Java with Gradle
infer run -- ./gradlew build

# Incremental CI mode
infer run --incremental -- make
```

### mypy / tsc / clang-tidy

See language-specific sections. These are the highest-ROI static tools.
<!-- IDX:LAYER_STATIC_END -->

---

<!-- IDX:LAYER_DYNAMIC_START -->
## ADVANCED DETECTION: LAYER 2 — DYNAMIC ANALYSIS

### Valgrind Suite

**What:** Instrumentation framework for memory and thread debugging.  
**When:** Every C/C++ program, especially before releases.  
**When NOT:** Too slow (20–50× overhead) for production services or large test suites on every commit (use sanitizers instead).  
**Install:** Package manager (`apt install valgrind`)

```bash
# Memory errors
valgrind --leak-check=full --show-leak-kinds=all \
  --track-origins=yes --error-exitcode=1 ./app

# Thread errors
valgrind --tool=helgrind ./app

# Heap profiling
valgrind --tool=massif --massif-out-file=massif.out ./app
ms_print massif.out
```

### Clang Sanitizers

**What:** Compiler-instrumented runtime checks.  
**When:** C/C++ CI, daily builds, test suites.  
**When NOT:** ASan and TSan cannot be combined in one binary. MSan requires all libraries to be instrumented.  

```bash
# ASan + UBSan combo (best for CI)
clang -fsanitize=address,undefined -fno-sanitize-recover=all \
  -fno-omit-frame-pointer -g -O1 app.c -o app

# Thread sanitizer (separate build)
clang -fsanitize=thread -g -O1 app.c -o app_tsan

# Memory sanitizer (strictest requirements)
clang -fsanitize=memory -fno-omit-frame-pointer -g -O1 app.c -o app_msan
```

### py-spy

**What:** Sampling profiler for Python with zero instrumentation.  
**When:** Python performance issues in production.  
**When NOT:** Not for C extension profiling (use `perf` instead).  
**Repo:** https://github.com/benfred/py-spy

```bash
py-spy top --pid 1234
py-spy record -o profile.svg --pid 1234
py-spy dump --pid 1234
```

### perf

**What:** Linux kernel performance profiling tool.  
**When:** Native code performance, system-wide bottlenecks.  
**When NOT:** Not available on macOS or Windows.  

```bash
perf record -g ./app
perf report
perf top
```
<!-- IDX:LAYER_DYNAMIC_END -->

---

<!-- IDX:LAYER_FUZZING_START -->
## ADVANCED DETECTION: LAYER 3 — FUZZING

### AFL++

**What:** Industrial-grade coverage-guided fuzzer.  
**When:** C/C++ parsers, protocol handlers, file format parsers.  
**When NOT:** Requires source code access and compile-time instrumentation. Not practical for high-level interpreted languages.  
**Repo:** https://github.com/AFLplusplus/AFLplusplus

```bash
# Compile with instrumentation
afl-clang-fast -g -O2 target.c -o target_fuzz

# Run
mkdir seeds/
echo "valid" > seeds/seed1.txt
afl-fuzz -i seeds/ -o findings/ -- ./target_fuzz @@
```

### libFuzzer

**What:** In-process coverage-guided fuzzer for LLVM.  
**When:** C/C++ library functions, maximum speed needed.  
**Repo:** Built into Clang/LLVM

```c
int LLVMFuzzerTestOneInput(const uint8_t *data, size_t size) {
    parse_data(data, size);
    return 0;
}
```

```bash
clang -fsanitize=fuzzer,address -g -O1 fuzz_target.c -o fuzz_target
./fuzz_target -max_total_time=300
```

### Honggfuzz

**What:** Hardware-assisted fuzzer using Intel PT / ARM CoreSight.  
**When:** Binary fuzzing without source code, complex branching logic.  
**Repo:** https://github.com/google/honggfuzz

```bash
honggfuzz -P -- ./target_binary ___FILE___
```
<!-- IDX:LAYER_FUZZING_END -->

---

<!-- IDX:LAYER_SYMBOLIC_START -->
## ADVANCED DETECTION: LAYER 4 — SYMBOLIC EXECUTION

### KLEE

**What:** Symbolic execution engine on LLVM bytecode. Explores all feasible paths mathematically.  
**When:** Small, critical C/C++ functions where exhaustive exploration is feasible.  
**When NOT:** Path explosion makes it infeasible for large programs.  
**Repo:** https://github.com/klee/klee

```bash
# Compile to LLVM bitcode
clang -emit-llvm -g -c -O0 -Xclang -disable-O0-optnone target.c -o target.bc

# Run KLEE
klee --libc=uclibc --posix-runtime target.bc

# Results in klee-last/: .err files, concrete test inputs
```

### angr

**What:** Binary analysis platform combining symbolic execution and control flow recovery.  
**When:** Analyzing third-party binaries without source code, firmware auditing.  
**When NOT:** Very slow on large binaries.  
**Repo:** https://github.com/angr/angr

```python
import angr
project = angr.Project("/path/to/binary", auto_load_libs=False)
simgr = project.factory.simulation_manager(project.factory.entry_state())
simgr.explore(find=lambda s: b"flag{" in s.posix.dumps(1))
if simgr.found:
    print(simgr.found[0].posix.dumps(0))  # Input that triggers path
```
<!-- IDX:LAYER_SYMBOLIC_END -->

---

<!-- IDX:LAYER_TAINT_START -->
## ADVANCED DETECTION: LAYER 5 — TAINT ANALYSIS

### Taintgrind

**What:** Valgrind tool that tracks untrusted data from sources to dangerous sinks.  
**When:** Security-critical C/C++ code handling user input.  
**When NOT:** 50–100× slowdown; only run on targeted components, not full application continuously.  
**Repo:** https://github.com/wmkhoo/taintgrind

```bash
valgrind --tool=taintgrind --taint-source=fd:0 ./my_program < user_input.txt
```

**Taint Sources:** `fd:0` (stdin), network sockets, file reads, environment variables.  
**Taint Sinks:** `system()`, `exec()`, `sqlite3_exec()`, `printf()` (for info leaks).
<!-- IDX:LAYER_TAINT_END -->

---

<!-- IDX:LAYER_MUTATION_START -->
## ADVANCED DETECTION: LAYER 6 — MUTATION TESTING

### mutmut (Python)

**What:** Mutation testing tool for Python.  
**When:** After achieving 80%+ coverage, verify test quality.  
**When NOT:** Too slow for every commit; run weekly or per-release.  
**Repo:** https://github.com/boxed/mutmut

```bash
pip install mutmut
mutmut run --paths-to-mutate=src/
mutmut results
mutmut show 3  # Show details of surviving mutant #3
```

### Stryker (JS/TS)

**What:** Mutation testing framework for JavaScript/TypeScript.  
**When:** Critical frontend logic (validation, state management).  
**Repo:** https://github.com/stryker-mutator/stryker

```bash
npm install -D @stryker-mutator/core @stryker-mutator/jest-runner
npx stryker run
```

**Configuration:**
```json
{
  "thresholds": {
    "high": 80,
    "low": 60,
    "break": 50
  }
}
```

**Mutation Score Interpretation:**
- 0–40%: Tests provide false confidence
- 40–70%: Significant blind spots
- 70–90%: Good quality
- 90–100%: Excellent
<!-- IDX:LAYER_MUTATION_END -->

---

<!-- IDX:LAYER_HYBRID_START -->
## ADVANCED DETECTION: LAYER 7 — HYBRID APPROACHES

### Driller

**What:** Combines AFL++ fuzzing with angr symbolic execution. When AFL++ gets stuck on complex comparisons, Driller uses symbolic execution to compute the exact input to pass the branch.  
**When:** AFL++ plateaus on targets with magic values, checksums, or complex comparisons.  
**Repo:** https://github.com/shellphish/driller

```bash
pip install driller
python -m driller -b target_binary -i seeds/ -o output/
```

### Concolic Execution

**What:** Concrete + symbolic execution. Program runs with real values while tracking symbolic constraints. At branches, the solver can "flip" to explore alternatives.  
**Tools:** Driller, KLEE with concrete seeding.

**Best Practices:**
- Start with pure fuzzing for the first few hours
- Switch to hybrid when coverage plateaus
- Set aggressive time limits
<!-- IDX:LAYER_HYBRID_END -->

---

# PART VIII: READY-TO-RUN SCRIPTS & PIPELINES

<!-- IDX:SCRIPT_SCANNER_START -->
## READY-TO-RUN SCRIPT: UNIVERSAL QUALITY SCANNER

Save as `scan.sh`:

```bash
#!/usr/bin/env bash
# ═══════════════════════════════════════════════════════════════
# UNIVERSAL QUALITY SCANNER
# Combines: Lint → Test → Security → Dependencies → Complexity
# Usage: ./scan.sh [--fix] [--ci] [--lang python|js|all]
# ═══════════════════════════════════════════════════════════════
set -euo pipefail

FIX=false; CI=false; LANG="all"; VERBOSE=false; FAILURES=0
for arg in "$@"; do
  case $arg in
    --fix)    FIX=true ;;
    --ci)     CI=true ;;
    --lang)   shift; LANG="$1" ;;
    --verbose) VERBOSE=true ;;
  esac
done

log()  { echo "[SCAN] $*"; }
pass() { echo "[PASS] $*"; }
fail() { echo "[FAIL] $*"; FAILURES=$((FAILURES + 1)); }

lint_python() {
  log "Python: Linting..."
  if [ "$FIX" = true ]; then
    ruff check --fix . && ruff format . && pass "Python lint+format (fixed)"
  else
    ruff check . && ruff format --check . && pass "Python lint+format"
  fi
}

lint_js() {
  log "JS/TS: Linting..."
  if [ "$FIX" = true ]; then
    npx biome check --write . && pass "JS/TS lint+format (fixed)"
  else
    npx biome check . && pass "JS/TS lint+format"
  fi
}

typecheck_python() { log "Python: Type checking..."; mypy src/ --ignore-missing-imports && pass "Python types"; }
typecheck_ts()     { log "TS: Type checking..."; npx tsc --noEmit && pass "TS types"; }

test_python() { log "Python: Testing..."; pytest tests/ -q --cov=src --cov-report=term-missing --cov-fail-under=80 && pass "Python tests"; }
test_js()     { log "JS/TS: Testing..."; npx vitest run --coverage && pass "JS/TS tests"; }

security_scan() {
  log "Security: SAST..."; semgrep --config=p/default --config=p/owasp-top-ten . && pass "Semgrep"
  log "Security: Secrets..."; gitleaks detect --source=. --no-git && pass "Gitleaks"
  log "Security: Dependencies..."; trivy fs --severity HIGH,CRITICAL . && pass "Trivy"
}

complexity_check() {
  log "Complexity check..."
  HIGH=$(lizard src/ -w -l 15 2>&1 | tail -1 || true)
  if [ -n "$HIGH" ]; then echo "$HIGH" | head -10; fail "Complexity > 15 found"; else pass "Complexity OK"; fi
}

echo "════════════════════════════════════════════"
echo "  UNIVERSAL QUALITY SCANNER"
echo "  Lang: $LANG | Fix: $FIX | CI: $CI"
echo "  Started: $(date -Iseconds)"
echo "════════════════════════════════════════════"

case $LANG in
  python) lint_python; typecheck_python; test_python ;;
  js)     lint_js; typecheck_ts; test_js ;;
  all)    lint_python; lint_js; typecheck_python; typecheck_ts; test_python; test_js ;;
esac

security_scan
complexity_check

echo ""
echo "════════════════════════════════════════════"
if [ $FAILURES -eq 0 ]; then echo "  ALL CHECKS PASSED"; else echo "  $FAILURES CHECK(S) FAILED"; exit 1; fi
echo "  Finished: $(date -Iseconds)"
echo "════════════════════════════════════════════"
```
<!-- IDX:SCRIPT_SCANNER_END -->

---

<!-- IDX:SCRIPT_DIAGNOSE_START -->
## READY-TO-RUN SCRIPT: ZERO-CONFIG AUTO-DIAGNOSIS ENGINE

Save as `autodiagnose.sh` — **Requires NO arguments. Detects everything automatically.**

```bash
#!/usr/bin/env bash
# ═══════════════════════════════════════════════════════════════
# ZERO-CONFIG AUTO-DIAGNOSIS ENGINE v2.0
# Usage: ./autodiagnose.sh [optional: error_message]
# Detects project type, runs appropriate checks, generates report
# ═══════════════════════════════════════════════════════════════
set -euo pipefail

RED='\033[0;31m'; GREEN='\033[0;32m'; YELLOW='\033[1;33m'
CYAN='\033[0;36m'; BOLD='\033[1m'; NC='\033[0m'

ERROR_MSG="${1:-}"
REPORT=""
ISSUES=0

log()  { echo -e "${CYAN}[DIAG]${NC} $*"; }
pass() { echo -e "${GREEN}[PASS]${NC} $*"; }
warn() { echo -e "${YELLOW}[WARN]${NC} $*"; ISSUES=$((ISSUES + 1)); REPORT="$REPORT\n⚠️ $*"; }
fail() { echo -e "${RED}[FAIL]${NC} $*"; ISSUES=$((ISSUES + 1)); REPORT="$REPORT\n❌ $*"; }

echo -e "${BOLD}════════════════════════════════════════════════════════${NC}"
echo -e "${BOLD}  ZERO-CONFIG AUTO-DIAGNOSIS ENGINE v2.0${NC}"
echo -e "${BOLD}  Started: $(date -Iseconds 2>/dev/null || date)${NC}"
echo -e "${BOLD}════════════════════════════════════════════════════════${NC}"

# ─── Phase 1: Auto-Detect Project ───
log "Phase 1: Auto-detecting project type..."

LANG="unknown"; FRAMEWORK="unknown"; PKG_MGR="unknown"; TEST_RUNNER="unknown"

if [ -f "package.json" ]; then
  LANG="javascript/typescript"
  PKG=$(cat package.json 2>/dev/null || echo "{}")
  echo "$PKG" | grep -q '"next"' && FRAMEWORK="nextjs"
  echo "$PKG" | grep -q '"vite"' && FRAMEWORK="vite"
  echo "$PKG" | grep -q '"react"' && [ "$FRAMEWORK" = "unknown" ] && FRAMEWORK="react"
  echo "$PKG" | grep -q '"vue"' && FRAMEWORK="vue"
  echo "$PKG" | grep -q '"express"' && FRAMEWORK="express"
  echo "$PKG" | grep -q '"vitest"' && TEST_RUNNER="vitest"
  echo "$PKG" | grep -q '"jest"' && TEST_RUNNER="jest"
  [ -f "bun.lockb" ] && PKG_MGR="bun"
  [ -f "pnpm-lock.yaml" ] && PKG_MGR="pnpm"
  [ -f "yarn.lock" ] && PKG_MGR="yarn"
  [ -f "package-lock.json" ] && PKG_MGR="npm"
fi

if [ -f "requirements.txt" ] || [ -f "pyproject.toml" ] || [ -f "setup.py" ]; then
  LANG="python"
  [ -f "manage.py" ] && FRAMEWORK="django"
  grep -q "fastapi" requirements.txt 2>/dev/null && FRAMEWORK="fastapi"
  TEST_RUNNER="pytest"
  [ -f "poetry.lock" ] && PKG_MGR="poetry"
  [ -f "uv.lock" ] && PKG_MGR="uv"
fi

[ -f "go.mod" ] && LANG="go" && TEST_RUNNER="go-test"
[ -f "Cargo.toml" ] && LANG="rust" && TEST_RUNNER="cargo-test"

echo -e "  Language:  ${BOLD}$LANG${NC}"
echo -e "  Framework: ${BOLD}$FRAMEWORK${NC}"
echo -e "  Pkg Mgr:   ${BOLD}$PKG_MGR${NC}"
echo -e "  Tests:     ${BOLD}$TEST_RUNNER${NC}"

# ─── Phase 2: Environment Health ───
log "Phase 2: Checking environment health..."

# Runtime versions
command -v node &>/dev/null && pass "Node: $(node -v)" || [ "$LANG" = "javascript/typescript" ] && warn "Node.js not found but JS project detected"
command -v python3 &>/dev/null && pass "Python: $(python3 --version 2>&1)" || [ "$LANG" = "python" ] && warn "Python3 not found but Python project detected"

# Git state
if git rev-parse --git-dir &>/dev/null; then
  DIRTY=$(git status --porcelain 2>/dev/null | wc -l | tr -d ' ')
  [ "$DIRTY" -gt 0 ] && warn "Git: $DIRTY uncommitted changes" || pass "Git: clean working tree"
  pass "Git: last commit: $(git log --oneline -1 2>/dev/null)"
else
  warn "Not a git repository"
fi

# Disk space
DISK_AVAIL=$(df -h . 2>/dev/null | awk 'NR==2{print $4}')
pass "Disk available: $DISK_AVAIL"

# ─── Phase 3: Dependency Health ───
log "Phase 3: Checking dependencies..."

if [ "$LANG" = "javascript/typescript" ]; then
  [ -d "node_modules" ] && pass "node_modules exists" || fail "node_modules MISSING — run: ${PKG_MGR:-npm} install"
  
  # Check for lockfile freshness
  if [ -f "package-lock.json" ] && [ "package.json" -nt "package-lock.json" ]; then
    warn "package.json is newer than lockfile — possible dependency drift"
  fi
  
  # Security audit
  npm audit --audit-level=high 2>/dev/null | grep -q "found 0 vulnerabilities" && pass "npm audit: no high/critical vulnerabilities" || warn "npm audit: vulnerabilities found (run: npm audit)"
fi

if [ "$LANG" = "python" ]; then
  python3 -c "import sys; sys.exit(0 if hasattr(sys, 'real_prefix') or sys.base_prefix != sys.prefix else 1)" 2>/dev/null && pass "Virtual environment active" || warn "No virtual environment detected"
fi

# ─── Phase 4: Code Quality ───
log "Phase 4: Running code quality checks..."

if [ "$LANG" = "javascript/typescript" ]; then
  # TypeScript check
  if [ -f "tsconfig.json" ]; then
    npx tsc --noEmit 2>/dev/null && pass "TypeScript: no type errors" || fail "TypeScript: type errors detected (run: npx tsc --noEmit)"
  fi
  
  # Lint check
  if command -v biome &>/dev/null || [ -f "node_modules/.bin/biome" ]; then
    npx biome check . 2>/dev/null && pass "Biome: lint clean" || warn "Biome: lint issues found"
  elif [ -f ".eslintrc.js" ] || [ -f ".eslintrc.json" ] || [ -f "eslint.config.js" ]; then
    npx eslint . --quiet 2>/dev/null && pass "ESLint: lint clean" || warn "ESLint: lint issues found"
  fi
fi

if [ "$LANG" = "python" ]; then
  command -v ruff &>/dev/null && { ruff check . 2>/dev/null && pass "Ruff: lint clean" || warn "Ruff: issues found"; }
  command -v mypy &>/dev/null && { mypy . --ignore-missing-imports 2>/dev/null && pass "mypy: types clean" || warn "mypy: type errors found"; }
fi

# ─── Phase 5: Build Check ───
log "Phase 5: Verifying build..."

if [ "$LANG" = "javascript/typescript" ]; then
  if grep -q '"build"' package.json 2>/dev/null; then
    npm run build 2>/dev/null && pass "Build: SUCCESS" || fail "Build: FAILED (run: npm run build for details)"
  fi
fi

# ─── Phase 6: Test Health ───
log "Phase 6: Running tests..."

case $TEST_RUNNER in
  vitest) npx vitest run --reporter=verbose 2>/dev/null && pass "Tests: ALL PASSED" || fail "Tests: FAILURES detected" ;;
  jest)   npx jest --forceExit 2>/dev/null && pass "Tests: ALL PASSED" || fail "Tests: FAILURES detected" ;;
  pytest) python3 -m pytest tests/ -x -q 2>/dev/null && pass "Tests: ALL PASSED" || fail "Tests: FAILURES detected" ;;
  go-test) go test ./... 2>/dev/null && pass "Tests: ALL PASSED" || fail "Tests: FAILURES detected" ;;
  cargo-test) cargo test 2>/dev/null && pass "Tests: ALL PASSED" || fail "Tests: FAILURES detected" ;;
  *) warn "No test runner detected — consider adding tests" ;;
esac

# ─── Phase 7: Security Quick Scan ───
log "Phase 7: Quick security scan..."

# Check for hardcoded secrets
SECRETS_FOUND=$(grep -rn --include="*.ts" --include="*.tsx" --include="*.js" --include="*.py" \
  -E "(password|secret|api.key|token)\s*[:=]\s*['\"][^'\"]{8,}" . 2>/dev/null | \
  grep -v node_modules | grep -v ".env" | head -5)
[ -n "$SECRETS_FOUND" ] && fail "Possible hardcoded secrets found:\n$SECRETS_FOUND" || pass "No obvious hardcoded secrets"

# Check .env files aren't tracked
if git rev-parse --git-dir &>/dev/null; then
  ENV_TRACKED=$(git ls-files "*.env" ".env*" 2>/dev/null | head -5)
  [ -n "$ENV_TRACKED" ] && fail "WARNING: .env files tracked in git: $ENV_TRACKED" || pass "No .env files in git"
fi

# ─── Phase 8: Error-Specific Diagnosis ───
if [ -n "$ERROR_MSG" ]; then
  log "Phase 8: Analyzing specific error: '$ERROR_MSG'"
  
  echo ""
  echo "  Searching codebase for error pattern..."
  rg "$ERROR_MSG" -l 2>/dev/null | head -10 || echo "  No matches found in source"
  
  echo ""
  echo "  Recent commits touching related files:"
  rg "$ERROR_MSG" -l 2>/dev/null | head -3 | while read -r f; do
    git log --oneline -3 -- "$f" 2>/dev/null
  done
fi

# ─── Final Report ───
echo ""
echo -e "${BOLD}════════════════════════════════════════════════════════${NC}"
if [ $ISSUES -eq 0 ]; then
  echo -e "${GREEN}${BOLD}  ✅ ALL CHECKS PASSED — Project is healthy${NC}"
else
  echo -e "${RED}${BOLD}  ⚠️  $ISSUES ISSUE(S) DETECTED${NC}"
  echo -e "$REPORT"
fi
echo -e "${BOLD}  Finished: $(date -Iseconds 2>/dev/null || date)${NC}"
echo -e "${BOLD}════════════════════════════════════════════════════════${NC}"

exit $ISSUES
```
<!-- IDX:SCRIPT_DIAGNOSE_END -->

---

<!-- IDX:SCRIPT_HOTRELOAD_START -->
## READY-TO-RUN SCRIPT: HOT-RELOAD FIX LOOP

Save as `hot-reload.sh`:

```bash
#!/usr/bin/env bash
# ═══════════════════════════════════════════════════════════════
# HOT-RELOAD FIX LOOP
# Watches files → Auto-fixes → Browser reloads
# ═══════════════════════════════════════════════════════════════
set -euo pipefail

PROJECT_DIR="${1:-.}"
echo "[HOT-RELOAD] Watching: $PROJECT_DIR"

# Python auto-fix
watchmedo shell-command --patterns="*.py" --recursive \
  --command="ruff check --fix {path} && ruff format {path} && echo '[FIX] Python: {path}'" \
  --wait "$PROJECT_DIR" &

# JS/TS auto-fix
watchmedo shell-command --patterns="*.ts;*.tsx;*.js;*.jsx" --recursive \
  --command="npx biome check --write {path} && echo '[FIX] JS/TS: {path}'" \
  --wait "$PROJECT_DIR" &

# Browser live reload
browser-sync start --proxy "localhost:3000" \
  --files "src/**/*.{ts,tsx,css,html}" --no-notify --reload-delay 300 &

echo "[HOT-RELOAD] All watchers active. Ctrl+C to stop."
wait
```
<!-- IDX:SCRIPT_HOTRELOAD_END -->

---

<!-- IDX:SCRIPT_CI_START -->
## READY-TO-RUN SCRIPT: CI PIPELINE TEMPLATE

Save as `.github/workflows/quality.yml`:

```yaml
name: Quality Gate
on:
  push:
    branches: [main, develop]
  pull_request:
    branches: [main]

jobs:
  lint:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-python@v5
        with: { python-version: "3.12" }
      - uses: actions/setup-node@v4
        with: { node-version: "22" }
      - run: pip install ruff mypy
      - run: npm install -D @biomejs/biome typescript
      - run: ruff check . && ruff format --check .
      - run: mypy src/ --ignore-missing-imports
      - run: npx biome check .
      - run: npx tsc --noEmit

  test:
    runs-on: ubuntu-latest
    needs: lint
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-python@v5
        with: { python-version: "3.12" }
      - run: pip install -r requirements-dev.txt
      - run: pytest tests/ -q --cov=src --cov-report=term-missing --cov-fail-under=80
      - uses: actions/setup-node@v4
        with: { node-version: "22" }
      - run: npm ci
      - run: npx vitest run --coverage

  security:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
        with: { fetch-depth: 0 }
      - uses: returntocorp/semgrep-action@v1
        with: { config: "p/default p/owasp-top-ten" }
      - uses: gitleaks/gitleaks-action@v2
      - uses: aquasecurity/trivy-action@master
        with: { scan-type: "fs", severity: "HIGH,CRITICAL", exit-code: "1" }
```
<!-- IDX:SCRIPT_CI_END -->

---

<!-- IDX:VALIDATION_PYTHON_START -->
### Python Full Validation

```bash
ruff check . && \
mypy src/ --ignore-missing-imports && \
pytest -x --cov=src --cov-fail-under=80 && \
bandit -r src/ -ll && \
semgrep --config=p/default src/ --error && \
vulture src/ && \
lizard src/ -w -l 15
```
<!-- IDX:VALIDATION_PYTHON_END -->

---

<!-- IDX:VALIDATION_JS_TS_START -->
### JS/TS Full Validation

```bash
biome check . && \
npx tsc --noEmit && \
npx vitest run --coverage && \
npm audit --audit-level=high && \
npx semgrep --config=p/default src/ --error
```
<!-- IDX:VALIDATION_JS_TS_END -->

---

<!-- IDX:VALIDATION_SECURITY_START -->
### Security-First Validation

```bash
gitleaks detect --source . --verbose && \
pip-audit --requirement requirements.txt && \
npm audit --audit-level=moderate && \
semgrep --config=p/default --config=p/owasp-top-ten src/ --error && \
[ -f Dockerfile ] && trivy image --severity HIGH,CRITICAL .
```
<!-- IDX:VALIDATION_SECURITY_END -->

---

# PART IX: AI PROMPT MODES

<!-- IDX:PROMPT_BUGFIX_STRICT_START -->
## PROMPT MODE: ZERO_CONFIG_AUTO (★ DEFAULT — Use When No Mode Specified)

**Trigger:** This mode activates AUTOMATICALLY when the user provides ANY error, bug, or testing request WITHOUT specifying a mode. This is the primary mode that makes the arsenal zero-configuration.

**Protocol:**
1. Execute Part 0 Auto-Pilot Engine silently (detect → classify → route)
2. Apply the appropriate taxonomy/protocol based on auto-classification
3. Read ALL relevant files before proposing changes
4. Generate 3 ranked hypotheses with probability scores
5. Implement the minimal surgical fix for the highest-probability hypothesis
6. Write regression test that fails before fix, passes after
7. Run stack-appropriate verification commands
8. Deliver in the mandatory structured format (Root Cause → Fix → Test → Verify → Risk)

**Key Behaviors:**
- NEVER ask "what framework are you using?" — detect it
- NEVER ask "what version?" — read package.json/requirements.txt
- NEVER suggest tools that aren't installed — check first
- ALWAYS provide the complete fix in ONE response
- ALWAYS include rollback instructions
- ALWAYS run the Fix Confidence Scorecard before delivering

**Temperature:** 0.0–0.3 (precision over creativity)

---

## PROMPT MODE: BUGFIX_STRICT

**Trigger:** Prefix request with `BUGFIX_STRICT: [description]`

**Protocol:**
1. Restate bug in one line
2. Propose likely root causes (ranked by probability)
3. Provide minimal reproducible test
4. Implement smallest safe fix
5. Add regression tests
6. Explain WHY fix works and what it does NOT cover
7. Provide risk notes and rollback plan

**Temperature:** 0.0–0.2

**Template:**
```markdown
BUGFIX_STRICT: [exact error message or behavior]

Context: [PROJECT/FILE/FUNCTION]
Symptom: [EXACT ERROR MESSAGE OR BEHAVIOR]
Trigger: [STEPS TO REPRODUCE]
Expected: [WHAT SHOULD HAPPEN]
Actual: [WHAT HAPPENS INSTEAD]

Scope constraint: Only modify [SPECIFIC FUNCTION/FILE].
Output: Root cause → minimal fix → regression test.
```
<!-- IDX:PROMPT_BUGFIX_STRICT_END -->

---

<!-- IDX:PROMPT_CLEAN_REFACTOR_START -->
## PROMPT MODE: CLEAN_REFACTOR

**Trigger:** Prefix request with `CLEAN_REFACTOR: [scope]`

**Protocol:**
1. Identify code smell and target improvement
2. Write characterization tests first
3. Apply smallest possible transformation
4. Run tests after each change
5. Verify behavior unchanged
6. Document what changed and why

**Template:**
```markdown
CLEAN_REFACTOR: [COMPONENT/MODULE]

Target improvement: [SPECIFIC QUALITY — readability, performance, coupling]
Constraints:
- Behavior MUST NOT change (add characterization tests first)
- One transformation per step
- Run tests after each step
- Document what changed and why
```
<!-- IDX:PROMPT_CLEAN_REFACTOR_END -->

---

<!-- IDX:PROMPT_TEST_DESIGN_MAX_START -->
## PROMPT MODE: TEST_DESIGN_MAX

**Trigger:** Prefix request with `TEST_DESIGN_MAX: [target]`

**Output Requirements:**
- Unit tests (logic correctness)
- Integration tests (component interaction)
- End-to-end tests (real user flow)
- Regression tests (exact bug never returns)
- Property-based tests (broad invariants)
- Edge case tests (boundaries, null, empty)
- Error path tests (failure handling)
- Concurrency tests (race conditions where applicable)

**Template:**
```markdown
TEST_DESIGN_MAX: [function/module/API]

Specification: [WHAT SHOULD this code do?]
Framework: [pytest / vitest / jest / etc.]

Requirements:
- Tier 1 Happy Path: minimum 20% of tests
- Tier 2 Boundary & Edge: minimum 40%
- Tier 3 Error & Rejection: minimum 25%
- Tier 4 Contract Tests: minimum 15%
- Coverage target: >80% line coverage, >70% mutation score
```
<!-- IDX:PROMPT_TEST_DESIGN_MAX_END -->

---

<!-- IDX:PROMPT_SECURITY_HARDEN_START -->
## PROMPT MODE: SECURITY_HARDEN

**Trigger:** Prefix request with `SECURITY_HARDEN: [target]`

**Protocol:**
1. Input validation audit
2. Authentication/authorization review
3. Injection vulnerability scan
4. Data exposure check
5. Dependency security audit
6. Rate limiting review
7. Logging audit (no secrets)

**Template:**
```markdown
SECURITY_HARDEN: [target codebase/component]

Run the following checks and report findings with severity:
- Semgrep SAST scan
- Bandit scan (if Python)
- CodeQL deep analysis
- Gitleaks secret detection
- Dependency vulnerability scan (Trivy / npm audit / pip-audit)

For each finding: Severity | Location | Fix | Test.
```
<!-- IDX:PROMPT_SECURITY_HARDEN_END -->

---

<!-- IDX:PROMPT_PERF_OPTIMIZE_START -->
## PROMPT MODE: PERF_OPTIMIZE

**Trigger:** Prefix request with `PERF_OPTIMIZE: [target]`

**Protocol:**
1. Profile and identify bottleneck
2. Measure baseline performance
3. Apply optimization
4. Measure improvement
5. Verify correctness unchanged
6. Document trade-offs

**Template:**
```markdown
PERF_OPTIMIZE: [function/endpoint/component]

Current behavior: [what it does]
Performance complaint: [slow / high CPU / high memory]

Steps:
1. Run profiler (py-spy / perf / Chrome Performance)
2. Identify hot path
3. Propose 3 optimization options with trade-offs
4. Implement best option
5. Show before/after measurements
```
<!-- IDX:PROMPT_PERF_OPTIMIZE_END -->

---

# PART X: AGENT INTEGRATION & POSTMORTEM

<!-- IDX:AGENT_INTEGRATION_START -->
## AGENT INTEGRATION: DEBUG ↔ TEST HANDOFFS

### Handoff: Debugging Agent → Testing Agent

After Phase 4 (Implementation), the fix passes to Testing Agent with:
```markdown
□ Error classification from taxonomy
□ Root cause statement
□ Link to regression test
□ Risk assessment
□ Recommended validation pipeline to run
```

Testing Agent must execute:
- Static analysis: `Semgrep`, `mypy`, `tsc --noEmit`
- Property-based testing: `Hypothesis` / `fast-check`
- Mutation testing: `Stryker` / `mutmut`
- Full regression suite

### Handoff: Testing Agent → Debugging Agent

When tests find bugs, Testing Agent passes:
```markdown
□ Error classification
□ Minimal reproduction case
□ Logs / traces / stack traces
□ Failing test output
□ Environment context
```

Debugging Agent runs the systematic protocol from Phase 0 and returns the fix.

### Unified Workflow Loop

```
1. Bug detected (production alert or test failure)
2. Debugging Agent classifies → runs systematic protocol → implements fix
3. Testing Agent validates → runs regression suite → checks for new bugs
4. If new bugs found, loop back to Debugging Agent with updated context
5. Postmortem documents both debugging methodology and testing gaps
```
<!-- IDX:AGENT_INTEGRATION_END -->

---

<!-- IDX:POSTMORTEM_START -->
## POSTMORTEM TEMPLATE

### Required Sections

**1. Incident Summary**
- What happened
- When it started and ended
- Impact duration and severity
- Affected users/systems

**2. Error Classification**
- Which taxonomy category (Build / Runtime / Logic / Race / Memory / Performance / Security / Heisenbug)
- Why this classification was chosen

**3. Timeline**
- Detection time
- Investigation phases
- Resolution time
- Total time to fix

**4. Root Cause Analysis**
- Following the 5-phase protocol
- Evidence that confirmed the root cause
- Hypotheses that were rejected and why

**5. Tools Used**
- Which tools from the Arsenal were effective
- Which tools were ineffective or not needed
- Any new tools discovered

**6. Missed Signals**
- Could we have caught this preemptively?
- Which monitoring/alerting gaps existed?
- Were there early warnings that were ignored?

**7. Action Items**
- Prevention measures
- Monitoring improvements
- Runbook updates
- Test additions

**8. Pattern Library Entry**
- Add to shared debugging knowledge base
- Include: context, symptom, root cause, fix, test strategy
<!-- IDX:POSTMORTEM_END -->

---

# APPENDIX

<!-- IDX:CHEATSHEET_START -->
## ONE-PAGE CHEAT SHEET

```
┌─────────────────────────────────────────────────────────────────────┐
│                    DEBUGGING TOOL CHEAT SHEET                       │
├─────────────────────────────────────────────────────────────────────┤
│  "Something's wrong"      → Read the error message (always #1)      │
│  Type error?              → mypy / tsc --noEmit                     │
│  Security issue?          → Semgrep → CodeQL → Bandit               │
│  Memory leak?             → Chrome Memory / Valgrind massif         │
│  OOM crash?               → heapdump / Clinic.js / PM2              │
│  Slow function?           → py-spy / perf / callgrind               │
│  Segfault?                → Valgrind memcheck / ASan / pwndbg       │
│  Race condition?          → helgrind / TSan / go run -race          │
│  Shell script bug?        → ShellCheck (always)                     │
│  Dead code?               → Vulture / Lizard                        │
│  Infinite re-render?      → React DevTools Profiler                 │
│  Broken links?            → Playwright + CDP                        │
│  Production crash?        → strace / dtrace / kubectl logs          │
│  Complex C/C++ bug?       → Infer (formal analysis)                 │
│  Web API issue?           → mitmproxy / curl -v                     │
│  DB slow query?           → EXPLAIN ANALYZE / pg_stat_statements    │
│  Distributed failure?     → Jaeger/Zipkin trace IDs                 │
│  "I don't know"           → Chrome DevTools (web) / perf (native)  │
└─────────────────────────────────────────────────────────────────────┘
```
<!-- IDX:CHEATSHEET_END -->

---

<!-- IDX:REPO_INDEX_START -->
## SOURCE REPOSITORY INDEX

| Repo | URL | Primary Value |
|------|-----|---------------|
| obra/superpowers | https://github.com/obra/superpowers/tree/main/skills/systematic-debugging | 4-phase systematic debugging methodology |
| uchicago-cs/debugging-guide | https://github.com/uchicago-cs/debugging-guide | Error taxonomy & reactive/preemptive strategies |
| Google Troubleshooting | https://github.com/sambhipiyush/Troubleshooting-and-Debugging-Techniques-Google | Crash debugging, log analysis, postmortems |
| build-your-own-x | https://github.com/codecrafters-io/build-your-own-x | Deep architectural understanding |
| awesome-scalability | https://github.com/binhnguyennus/awesome-scalability | Distributed systems patterns |
| awesome-debugger | https://github.com/taowen/awesome-debugger | Record/replay time-travel debuggers |
| mitmproxy | https://github.com/mitmproxy/mitmproxy | HTTP/HTTPS intercepting proxy |
| ndb | https://github.com/GoogleChromeLabs/ndb | Node.js Chrome DevTools integration |
| pwndbg | https://github.com/pwndbg/pwndbg | GDB/LLDB reverse engineering enhancements |
| icecream | https://github.com/gruns/icecream | Python smart print debugging |
| yuriskinfo/cheat-sheets | https://github.com/yuriskinfo/cheat-sheets | Linux & network gear diagnostics |
| awesome-cheatsheets | https://github.com/LeCoupa/awesome-cheatsheets | Programming languages quick reference |
| Semgrep | https://github.com/returntocorp/semgrep | Fast static analysis (30+ languages) |
| CodeQL | https://github.com/github/codeql | Deep semantic security analysis |
| Infer | https://github.com/facebook/infer | Separation logic static analyzer |
| AFL++ | https://github.com/AFLplusplus/AFLplusplus | Industrial fuzzer |
| KLEE | https://github.com/klee/klee | Symbolic execution engine |
| angr | https://github.com/angr/angr | Binary analysis platform |
| mutmut | https://github.com/boxed/mutmut | Python mutation testing |
| Stryker | https://github.com/stryker-mutator/stryker | JS/TS mutation testing |
| rr | https://github.com/rr-debugger/rr | Record & replay for Linux |
| py-spy | https://github.com/benfred/py-spy | Python sampling profiler |
| Playwright | https://github.com/microsoft/playwright | Cross-browser E2E testing |
| Vitest | https://github.com/vitest-dev/vitest | Modern JS/TS test runner |
| pytest | https://github.com/pytest-dev/pytest | Python test framework |
<!-- IDX:REPO_INDEX_END -->

---

# PART XI: FRAMEWORK & DEPLOYMENT ERROR PREVENTION ARSENAL

<!-- IDX:FRAMEWORK_GOTCHAS_START -->
## FRAMEWORK-SPECIFIC GOTCHA ENCYCLOPEDIA

**Purpose:** The #1 source of AI coder errors is applying patterns from Framework A to Framework B, or using API syntax from version N-1 on version N. This section catalogs the most common and costly mistakes per framework.

---

### React 18/19 Gotchas

```markdown
GOTCHA 1: StrictMode double-rendering (development only)
  Symptom: useEffect fires twice, API called twice in dev
  NOT A BUG: React 18 strict mode intentionally double-invokes effects
  Fix: Don't disable StrictMode. Instead, make effects idempotent.
  TRAP: AI coders often "fix" this by removing StrictMode — DO NOT.

GOTCHA 2: Automatic batching in React 18
  Change: setState calls are ALWAYS batched (even in setTimeout, promises)
  Old behavior (React 17): Only batched in event handlers
  Fix: Use `flushSync()` only if you NEED synchronous re-render (rare)

GOTCHA 3: useEffect with object/array dependencies
  Symptom: Infinite re-render loop
  Cause: `useEffect(() => { ... }, [{ foo: 'bar' }])` — new object ref every render
  Fix: Destructure to primitives OR use `useMemo` for the dependency

GOTCHA 4: Server Components (React 19 / Next.js 13+)
  Symptom: "useState is not a function" or "useEffect is not a function"
  Cause: Using client-side hooks in a Server Component
  Fix: Add `'use client'` directive at the top of files that use hooks/state
  TRAP: AI coders forget `'use client'` because React 17 didn't need it

GOTCHA 5: Suspense boundaries and error boundaries
  Symptom: Entire page crashes when one component fails
  Cause: Missing error boundary wrapping async components
  Fix: Wrap with `<ErrorBoundary>` and `<Suspense fallback={...}>`

GOTCHA 6: Key prop resets component state
  Symptom: Form data disappears when list re-orders
  Cause: Using array index as key — React reuses wrong component instance
  Fix: Use stable, unique ID from data (never array index)

GOTCHA 7: Hydration mismatch (SSR/SSG)
  Symptom: "Text content did not match" warning
  Cause: Server-rendered HTML differs from client-rendered HTML
  Common causes: Date.now(), Math.random(), browser-only APIs (window, localStorage)
  Fix: Use `useEffect` for browser-only values, or `suppressHydrationWarning`
```

### Next.js 14/15 Gotchas

```markdown
GOTCHA 1: App Router vs Pages Router confusion
  Symptom: Routing doesn't work, layouts don't apply, getServerSideProps undefined
  Cause: Mixing App Router (app/) and Pages Router (pages/) patterns
  Fix: Choose ONE routing paradigm per project. App Router is the future.

GOTCHA 2: Server Actions and 'use server'
  Symptom: Functions not callable from client components
  Cause: Missing `'use server'` directive, or trying to pass non-serializable data
  Fix: Server actions should be in separate files with `'use server'` at top

GOTCHA 3: Dynamic vs Static rendering
  Symptom: Data appears stale, or page shows cached content
  Cause: Next.js defaults to static rendering — data is cached at build time
  Fix: Use `revalidate` option, `cookies()`, `headers()`, or `unstable_noStore()`

GOTCHA 4: Middleware edge runtime limitations
  Symptom: "Module not found" or "This API is not available"
  Cause: Middleware runs in Edge Runtime — no Node.js APIs (fs, child_process)
  Fix: Move Node.js-dependent logic to API routes or server actions

GOTCHA 5: Image optimization
  Symptom: Images 404, or "Invalid src prop" error
  Cause: External images need explicit domain configuration
  Fix: Add domains to `next.config.js` → `images.remotePatterns`

GOTCHA 6: Environment variables
  Symptom: process.env.VAR is undefined in browser
  Cause: Only `NEXT_PUBLIC_` prefixed vars are available in client code
  Fix: Prefix with NEXT_PUBLIC_ for client-side, plain for server-side only
  TRAP: AI coders often forget the prefix and expose server vars or miss client vars
```

### Vite Gotchas

```markdown
GOTCHA 1: Environment variables
  Symptom: import.meta.env.VAR is undefined
  Cause: Vite only exposes vars prefixed with `VITE_`
  Fix: `VITE_API_URL=... ` in `.env` file, access via `import.meta.env.VITE_API_URL`
  TRAP: AI coders use `process.env` (Node.js) instead of `import.meta.env` (Vite)

GOTCHA 2: CommonJS vs ESM
  Symptom: "require is not defined" or "Cannot use import statement"
  Cause: Vite is ESM-only — CommonJS `require()` doesn't work in Vite
  Fix: Use `import` syntax. For CJS deps, Vite auto-converts most of them.

GOTCHA 3: Path aliases
  Symptom: "Module not found" for `@/components/...`
  Cause: Path alias configured in vite.config but NOT in tsconfig.json (or vice versa)
  Fix: Configure in BOTH `vite.config.ts` (resolve.alias) AND `tsconfig.json` (paths)

GOTCHA 4: HMR not working
  Symptom: Changes don't hot-reload, full page refresh needed
  Cause: Component not properly exporting, or file outside Vite root
  Fix: Check component exports are named (not default + renamed), check Vite root

GOTCHA 5: Production build differences
  Symptom: Works in `npm run dev` but breaks in `npm run build && npm run preview`
  Cause: Dev uses esbuild (lenient), production uses Rollup (strict)
  Fix: Always test with `npm run build && npm run preview` before deploying
```

### TypeScript Gotchas

```markdown
GOTCHA 1: Type assertions are lies
  Symptom: Runtime crash despite "no TypeScript errors"
  Cause: `data as User` tells TypeScript to trust you — it does NOT validate
  Fix: Use Zod, io-ts, or valibot for runtime validation at boundaries

GOTCHA 2: Strict null checks
  Symptom: "Object is possibly undefined" — adding `!` everywhere
  Cause: `strictNullChecks` is ON (good!) but code doesn't handle null/undefined
  Fix: Use optional chaining (`?.`) and nullish coalescing (`??`) properly
  TRAP: AI coders add `!` (non-null assertion) to silence errors — NEVER DO THIS

GOTCHA 3: Structural typing surprises
  Symptom: Function accepts unexpected object shapes
  Cause: TypeScript uses structural typing — any object with matching props is valid
  Fix: Use branded types for type-safe IDs: `type UserId = string & { __brand: 'UserId' }`

GOTCHA 4: async functions always return Promise
  Symptom: Type mismatch when assigning async function result
  Cause: `async function f(): User` is wrong — it returns `Promise<User>`
  Fix: Always type async functions as returning Promise<T>

GOTCHA 5: enum vs const enum vs union
  Symptom: Unexpected runtime behavior, bundle size issues
  Cause: Enums generate runtime code, const enums are inlined, unions are type-only
  Fix: Prefer `type Status = 'active' | 'inactive'` over `enum Status { ... }`
```

### Node.js Gotchas

```markdown
GOTCHA 1: ESM vs CJS confusion
  Symptom: "ERR_REQUIRE_ESM" or "Cannot use import statement"
  Cause: Package is ESM-only but project uses CommonJS, or vice versa
  Fix: Set `"type": "module"` in package.json for ESM, or use `.mjs`/`.cjs` extensions

GOTCHA 2: Event loop blocking
  Symptom: Server stops responding, health checks fail
  Cause: Synchronous operation (crypto, JSON.parse of huge payload, fs.readFileSync)
  Fix: Use async alternatives, worker threads for CPU-heavy tasks

GOTCHA 3: Memory leaks from event listeners
  Symptom: "MaxListenersExceededWarning", memory usage grows over time
  Cause: Adding event listeners without removing them (especially in loops)
  Fix: Always `removeEventListener` or use `{ once: true }` option

GOTCHA 4: Unhandled promise rejections crash in Node 15+
  Old behavior: Warning only
  New behavior: Process exits with non-zero code
  Fix: Always `.catch()` promises, add `process.on('unhandledRejection', handler)`

GOTCHA 5: `__dirname` doesn't exist in ESM
  Cause: ESM modules don't have `__dirname` or `__filename`
  Fix: `import.meta.url` + `fileURLToPath()` + `path.dirname()`
  ```js
  import { fileURLToPath } from 'url';
  import { dirname } from 'path';
  const __dirname = dirname(fileURLToPath(import.meta.url));
  ```
```

### Python Gotchas

```markdown
GOTCHA 1: Mutable default arguments (the classic)
  Symptom: Function accumulates state across calls
  Cause: `def f(items=[])` — default list is created ONCE and shared
  Fix: `def f(items=None): items = items or []`

GOTCHA 2: Late binding closures in loops
  Symptom: All lambda functions return the same value
  Cause: `[lambda: i for i in range(5)]` — all closures capture same variable `i`
  Fix: `[lambda i=i: i for i in range(5)]` — capture by value with default arg

GOTCHA 3: Import circular references
  Symptom: ImportError or AttributeError on imported module
  Cause: Module A imports B, B imports A
  Fix: Move shared code to a third module, or use lazy imports inside functions

GOTCHA 4: Dictionary ordering (Python 3.7+)
  Old belief: Dicts are unordered
  Truth: Dicts preserve insertion order since Python 3.7 (CPython 3.6)
  TRAP: Don't RELY on this for algorithms — use OrderedDict if order is semantically important

GOTCHA 5: String formatting f-strings with backslashes
  Symptom: SyntaxError in f-string
  Cause: `f"path {path.replace('\\', '/')}"` — backslashes inside f-string braces
  Fix: Assign to variable first: `cleaned = path.replace('\\', '/'); f"path {cleaned}"`

GOTCHA 6: Global Interpreter Lock (GIL)
  Symptom: Threading doesn't speed up CPU-bound work
  Cause: GIL allows only one thread to execute Python code at a time
  Fix: Use `multiprocessing` for CPU-bound, `asyncio`/`threading` for I/O-bound
```
<!-- IDX:FRAMEWORK_GOTCHAS_END -->

---

<!-- IDX:DEPLOYMENT_ANTIPATTERNS_START -->
## DEPLOYMENT & INFRASTRUCTURE ANTI-PATTERNS

**Purpose:** 60% of production failures are deployment errors, not code bugs. These patterns prevent the most common deployment disasters.

### Docker Anti-Patterns

```markdown
ANTI-PATTERN 1: Running as root in container
  Risk: Container escape gives root access to host
  Fix: Add `USER node` or `USER appuser` in Dockerfile
  Check: `docker exec <c> whoami` should NOT return "root"

ANTI-PATTERN 2: Using `latest` tag
  Risk: Deployments are non-reproducible — "latest" changes under you
  Fix: Pin exact versions: `FROM node:22.11.0-alpine3.20`

ANTI-PATTERN 3: Missing .dockerignore
  Risk: Copies node_modules, .env, .git into image (huge + insecure)
  Fix: Create .dockerignore with: node_modules, .git, .env*, dist, *.log

ANTI-PATTERN 4: Single-stage build
  Risk: Build tools (gcc, devDependencies) in production image
  Fix: Multi-stage build:
  ```dockerfile
  FROM node:22 AS builder
  COPY . .
  RUN npm ci && npm run build
  FROM node:22-alpine
  COPY --from=builder /app/dist ./dist
  ```

ANTI-PATTERN 5: No healthcheck
  Risk: Container appears "running" but application is dead
  Fix: Add `HEALTHCHECK CMD curl -f http://localhost:3000/health || exit 1`

ANTI-PATTERN 6: Storing state in container
  Risk: Container restart loses all data
  Fix: Use volumes for persistent data, external DB for state
```

### Nginx Anti-Patterns

```markdown
ANTI-PATTERN 1: Default client_max_body_size (1MB)
  Symptom: File uploads fail with 413 Entity Too Large
  Fix: `client_max_body_size 50m;` in nginx.conf

ANTI-PATTERN 2: Missing proxy headers
  Symptom: App sees 127.0.0.1 instead of real client IP
  Fix: Add to location block:
    proxy_set_header Host $host;
    proxy_set_header X-Real-IP $remote_addr;
    proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    proxy_set_header X-Forwarded-Proto $scheme;

ANTI-PATTERN 3: No gzip compression
  Symptom: Slow page loads, large transfer sizes
  Fix: `gzip on; gzip_types text/plain application/json application/javascript text/css;`

ANTI-PATTERN 4: SPA routing returns 404
  Symptom: Direct URL access to /about returns 404
  Fix: `try_files $uri $uri/ /index.html;` in the server block

ANTI-PATTERN 5: Missing SSL redirect
  Risk: Users access HTTP version, data sent unencrypted
  Fix: Server block on port 80: `return 301 https://$server_name$request_uri;`

ANTI-PATTERN 6: WebSocket proxy not configured
  Symptom: WebSocket connections fail (socket.io, live reload)
  Fix: Add:
    proxy_http_version 1.1;
    proxy_set_header Upgrade $http_upgrade;
    proxy_set_header Connection "upgrade";
```

### SSH & Server Anti-Patterns

```markdown
ANTI-PATTERN 1: Password authentication enabled
  Risk: Brute-force attacks succeed
  Fix: `PasswordAuthentication no` in /etc/ssh/sshd_config

ANTI-PATTERN 2: Root SSH login enabled
  Risk: Direct root access = game over if compromised
  Fix: `PermitRootLogin no` in /etc/ssh/sshd_config

ANTI-PATTERN 3: No firewall configured
  Risk: All ports exposed to internet
  Fix: `ufw default deny incoming && ufw allow 22 && ufw allow 80 && ufw allow 443 && ufw enable`

ANTI-PATTERN 4: Running services without process manager
  Risk: Service doesn't restart after crash
  Fix: Use systemd, PM2 (Node.js), or supervisor

ANTI-PATTERN 5: No automatic security updates
  Risk: Known vulnerabilities remain unpatched
  Fix: `apt install unattended-upgrades && dpkg-reconfigure -plow unattended-upgrades`

ANTI-PATTERN 6: Log files consuming all disk space
  Risk: Disk full → service crashes
  Fix: Configure logrotate, or use `journald` with `SystemMaxUse=500M`
```

### CI/CD Anti-Patterns

```markdown
ANTI-PATTERN 1: No lockfile in CI
  Risk: CI installs different versions than local
  Fix: `npm ci` (not `npm install`) in CI — uses lockfile exactly

ANTI-PATTERN 2: Tests pass with warnings
  Risk: Warnings become errors in next version
  Fix: Treat warnings as errors: `CI=true npm run build` (React exits on warnings)

ANTI-PATTERN 3: No build cache
  Risk: CI takes 20 min instead of 3 min
  Fix: Cache node_modules, pip cache, build artifacts between runs

ANTI-PATTERN 4: Deploying without health check
  Risk: Broken deployment goes live
  Fix: After deploy: `curl -f https://yoursite.com/health || rollback`

ANTI-PATTERN 5: Secrets in CI logs
  Risk: API keys visible in build output
  Fix: Use masked secrets in CI, `--quiet` flags, never echo $SECRET
```
<!-- IDX:DEPLOYMENT_ANTIPATTERNS_END -->

---

<!-- IDX:AI_WORKFLOW_GUARDRAILS_START -->
## AI CODER WORKFLOW GUARDRAILS

**Purpose:** These guardrails prevent the systematic errors that AI coding assistants make repeatedly. Each guardrail addresses a specific failure mode observed in thousands of AI-assisted coding sessions.

### Guardrail 1: The File Reading Rule

```markdown
RULE: Never edit a file you haven't read completely in this session.

WHY: AI assistants maintain context from conversations, not file state.
The file may have changed since you last read it.

PROTOCOL:
1. Before ANY edit: Read the full file (or at minimum the 200 lines around edit point)
2. After reading: Verify the line numbers you plan to edit are actually what you expect
3. After editing: Verify the edit didn't corrupt adjacent code

COMMON FAILURE: Editing line 45 when the actual content has shifted to line 52
due to previous edits in the same session.
```

### Guardrail 2: The Dependency Verification Rule

```markdown
RULE: Never import a module or use an API without verifying it exists in the project.

PROTOCOL:
1. Before adding `import X from 'Y'`:
   - Check: `ls node_modules/Y` or `pip show Y`
   - Check: `grep -r "\"Y\"" package.json` or `grep "Y" requirements.txt`
2. Before using `X.someMethod()`:
   - Check: Does this method exist in the INSTALLED version?
   - Search: GitHub repo for the installed version's API

COMMON FAILURES:
- Importing `from 'lucide-react'` when project uses `'react-icons'`
- Using `zod.coerce.string()` when installed Zod version is < 3.20
- Importing `{ useRouter } from 'next/navigation'` in Pages Router (wrong module)
```

### Guardrail 3: The Build-Before-Ship Rule

```markdown
RULE: After every edit, verify the project still builds successfully.

PROTOCOL:
1. After code changes: `npm run build` (or `tsc --noEmit` for quick check)
2. After dependency changes: `npm install && npm run build`
3. After config changes: Full restart of dev server + build check

COMMON FAILURES:
- TypeScript errors only appear in `build`, not in `dev` mode
- Next.js pages that work in dev fail to build (dynamic imports, server components)
- Missing environment variables that dev mode silently ignores
```

### Guardrail 4: The State Preservation Rule

```markdown
RULE: When fixing a bug, preserve ALL existing state and functionality.

PROTOCOL:
Before writing a fix, document:
1. What currently works (list 3-5 working features near the bug)
2. What will change (the specific bug being fixed)
3. What MUST NOT change (existing behavior that must be preserved)

COMMON FAILURES:
- Rewriting a component to fix one bug, losing 3 other features
- Replacing a complex function with a "simpler" version that misses edge cases
- Upgrading a library to fix one issue, breaking 5 other things
```

### Guardrail 5: The Multi-File Coordination Rule

```markdown
RULE: When a change requires edits to multiple files, list ALL files FIRST.

PROTOCOL:
1. Before editing: Create a change map:
   - File A: What changes and why
   - File B: What changes and why (coupled to A)
   - File C: What changes and why (coupled to B)
2. Execute changes in dependency order (types → implementation → tests → config)
3. After ALL changes: Verify build + tests

COMMON FAILURES:
- Adding a new component but not adding its route
- Adding a new API endpoint but not updating the client
- Adding a new type but not importing it where it's used
- Updating a component's props but not updating parent components
```

### Guardrail 6: The Syntax Verification Rule

```markdown
RULE: After generating complex syntax (JSX, nested objects, regex), verify it parses.

HIGH-RISK SYNTAX:
- Nested JSX with conditional rendering (ternary + &&)
- Regular expressions with special characters
- JSON with nested arrays of objects
- YAML with indentation-sensitive blocks
- SQL with multiple JOINs and subqueries
- Template literals with embedded expressions

VERIFICATION:
- JSX: `npx tsc --noEmit` or check browser console
- JSON: `cat file.json | jq .` (fails on invalid JSON)
- YAML: `python -c "import yaml; yaml.safe_load(open('file.yml'))"`
- SQL: EXPLAIN the query before running it
```

### Guardrail 7: The Error Message Fidelity Rule

```markdown
RULE: Copy the EXACT error message. Never paraphrase or summarize errors.

WHY:
- "TypeScript error" is useless — "TS2345: Argument of type 'string' is not
  assignable to parameter of type 'number'" tells you exactly what's wrong
- Error codes (TS2345, E0001, ENOENT) are searchable and specific
- Stack traces show the exact call chain — summarizing loses critical context

PROTOCOL:
1. Copy the FULL error output (including stack trace)
2. Identify the PRIMARY error (first error in a cascade)
3. Search for the exact error code + message online
4. Only THEN propose a fix
```
<!-- IDX:AI_WORKFLOW_GUARDRAILS_END -->

---

<!-- IDX:ERROR_SYMPTOM_DECODER_START -->
## ERROR SYMPTOM FAST DECODER

**Purpose:** Given a symptom, immediately know where to look and what to check. This is the "emergency room triage" for coding errors.

### Frontend Symptoms

| Symptom | Most Likely Cause | First Check | Second Check |
|---------|-------------------|-------------|--------------|
| Blank white page | JavaScript crash before render | Browser console (F12) | Check for missing `'use client'` directive |
| "Hydration mismatch" warning | Server/client render difference | Check for `Date.now()`, `Math.random()`, `window` usage | Wrap browser-only code in `useEffect` |
| Infinite loading spinner | API call failing silently | Network tab → check request status | Add error handling to fetch calls |
| Page loads then flashes/blinks | CSS not loaded, or hydration re-render | Check CSS import order | Check for layout shift (CLS) |
| "Module not found" | Wrong import path | Verify file exists at import path | Check tsconfig paths vs vite.config alias |
| Component renders stale data | Stale closure or missing dependency | Check useEffect dependency array | Use functional setState: `setX(prev => ...)` |
| Click handler doesn't fire | Event not attached, or wrong element | Check onClick is on correct element | Check for `pointer-events: none` in CSS |
| Form submit refreshes page | Missing `e.preventDefault()` | Add to form submit handler | Check if form is inside another form |
| Styles not applying | CSS specificity, wrong selector | DevTools → Computed tab | Check for CSS Modules (.module.css) naming |
| Images not loading | Wrong path, CORS, or missing config | Network tab → check 404 | Check Next.js `images.remotePatterns` |

### Backend Symptoms

| Symptom | Most Likely Cause | First Check | Second Check |
|---------|-------------------|-------------|--------------|
| 500 Internal Server Error | Unhandled exception in route | Server logs (journalctl / pm2 logs) | Check for null/undefined access |
| 404 Not Found | Route not registered or wrong method | Check route definition matches URL | Check for trailing slash difference |
| 403 Forbidden | Auth middleware rejecting request | Check Authorization header present | Check token expiry/validity |
| CORS error in browser | Missing CORS headers on server | Add `Access-Control-Allow-Origin` header | Check preflight (OPTIONS) handling |
| Request timeout | Slow DB query or external API | Check DB query performance (EXPLAIN) | Add timeout to external API calls |
| "Connection refused" | Service not running on expected port | `lsof -i :<port>` or `ss -tlnp` | Check if service started successfully |
| Memory usage grows | Memory leak in application | Check for unclosed connections/listeners | Heap snapshot analysis |
| "Too many connections" | Connection pool exhausted | Check DB connection pool settings | Look for connection leaks (not .release()) |

### Build Symptoms

| Symptom | Most Likely Cause | First Check | Second Check |
|---------|-------------------|-------------|--------------|
| "Cannot find module" | Missing dependency or wrong path | `npm ls <package>` | Check package.json has correct name |
| "Type error" in build only | Stricter checks in production build | `npx tsc --noEmit` locally | Check tsconfig.json strictness settings |
| Build succeeds but app crashes | Runtime error not caught by types | Check for `as` type assertions | Add Zod validation at API boundaries |
| "Out of memory" during build | Large project, insufficient heap | `NODE_OPTIONS=--max-old-space-size=4096 npm run build` | Check for circular dependencies |
| Different behavior dev vs prod | Environment-specific code paths | Check `NODE_ENV` usage | Check for dev-only features/mocks |

### Database Symptoms

| Symptom | Most Likely Cause | First Check | Second Check |
|---------|-------------------|-------------|--------------|
| Query returns empty | Wrong WHERE clause or no data | Run query in DB client directly | Check for case sensitivity issues |
| Slow query | Missing index or full table scan | `EXPLAIN ANALYZE` the query | Check for N+1 query pattern |
| "Deadlock detected" | Concurrent transactions locking | Check transaction isolation level | Reduce transaction scope/duration |
| "Unique constraint violation" | Duplicate insert | Check for race condition (TOCTOU) | Use UPSERT/ON CONFLICT instead |
| Data appears corrupted | Encoding issue or bad migration | Check column types and encoding | Review recent migration scripts |
<!-- IDX:ERROR_SYMPTOM_DECODER_END -->

---

<!-- IDX:FIX_CONFIDENCE_SCORECARD_START -->
## FIX CONFIDENCE SCORECARD

**Purpose:** Before applying ANY fix, score it. If the score is below 7, do NOT apply — investigate further.

```markdown
SCORE YOUR FIX (1-10 scale for each):

1. ROOT CAUSE CLARITY: Can you explain the root cause in one sentence?
   1 = "I think it might be..." → 10 = "The exact mechanism is..."

2. REPRODUCTION: Can you make it fail on demand?
   1 = "It happened once" → 10 = "Here's a failing test case"

3. MINIMALITY: Is this the smallest possible change?
   1 = "I rewrote the whole file" → 10 = "Changed one line"

4. SIDE EFFECTS: Are you confident nothing else breaks?
   1 = "I hope not" → 10 = "All tests pass, I checked all callers"

5. REVERSIBILITY: Can this fix be easily reverted?
   1 = "It touches the database schema" → 10 = "Single commit, one file"

TOTAL: ___/50

Scoring guide:
  40-50: Ship it with confidence
  30-39: Ship it but monitor closely
  20-29: Get a second opinion before shipping
  10-19: Stop. You don't understand the problem well enough.
   0-9:  You're guessing. Go back to Phase 1.
```
<!-- IDX:FIX_CONFIDENCE_SCORECARD_END -->

---

<!-- IDX:EMERGENCY_RECOVERY_START -->
## EMERGENCY RECOVERY RECIPES

**Purpose:** When everything is broken and you need to get back to a working state FAST.

### Git Emergency Recovery

```bash
# Undo last commit (keep changes)
git reset --soft HEAD~1

# Undo last commit (discard changes)
git reset --hard HEAD~1

# Undo ALL uncommitted changes (nuclear option)
git checkout -- . && git clean -fd

# Find a specific lost commit
git reflog | head -20
git checkout <hash>

# Stash everything (including untracked files)
git stash --include-untracked

# Cherry-pick a fix from another branch
git cherry-pick <commit-hash>

# Bisect to find breaking commit
git bisect start
git bisect bad HEAD
git bisect good <known-good-commit>
# Test each commit, mark good/bad, git finds the culprit
```

### Node.js Emergency Recovery

```bash
# Nuclear clean + reinstall
rm -rf node_modules .next dist .cache package-lock.json
npm install
npm run build

# If npm install fails with ERESOLVE
npm install --legacy-peer-deps

# If TypeScript shows phantom errors
rm -rf node_modules/.cache tsconfig.tsbuildinfo
npx tsc --noEmit

# If dev server won't start
lsof -i :3000 | awk 'NR>1 {print $2}' | xargs kill -9
npm run dev
```

### Python Emergency Recovery

```bash
# Nuclear clean + reinstall
rm -rf __pycache__ .mypy_cache .pytest_cache .ruff_cache
pip install -r requirements.txt --force-reinstall

# If import errors after changes
python -c "import py_compile; py_compile.compile('problematic_file.py')"

# If virtual environment is corrupted
rm -rf venv
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

### Docker Emergency Recovery

```bash
# Stop all containers
docker stop $(docker ps -q)

# Remove all stopped containers
docker container prune -f

# Remove all images (nuclear)
docker system prune -af --volumes

# Rebuild without cache
docker build --no-cache -t myapp .

# Check why container keeps restarting
docker logs <container> --tail 50
docker inspect <container> | jq '.[0].State'
```

### Server Emergency Recovery

```bash
# Check disk space
df -h

# Free up space quickly
sudo apt clean
sudo journalctl --vacuum-size=100M
find /var/log -name "*.gz" -delete
find /tmp -type f -mtime +7 -delete

# Check and restart services
systemctl status nginx
systemctl restart nginx
systemctl status <your-app>
systemctl restart <your-app>

# Check what's using all the memory
ps aux --sort=-%mem | head -10

# Check what's using all the CPU
ps aux --sort=-%cpu | head -10
```
<!-- IDX:EMERGENCY_RECOVERY_END -->

---

# PART XII: AI INSTANT-FIX LOOKUP TABLES

<!-- IDX:INSTANT_FIX_START -->
## ⚡ INSTANT-FIX LOOKUP: EXACT ERROR → EXACT FIX

**Purpose:** When AI encounters these EXACT errors, it can apply the fix IMMEDIATELY without running the full diagnosis protocol. These are the 50+ most common errors with deterministic, proven solutions.

**Usage Rule:** If the error matches EXACTLY, apply the fix directly. If it's similar but not exact, use the full protocol.

---

### JavaScript / TypeScript Instant Fixes

| # | Exact Error | Root Cause | Instant Fix |
|---|-------------|-----------|-------------|
| 1 | `Cannot find module 'X' or its corresponding type declarations` | Package not installed or types missing | `npm install X` or `npm install -D @types/X` |
| 2 | `Module '"X"' has no exported member 'Y'` | Wrong version of package or wrong import | Check installed version: `npm ls X`, then check docs for correct export name |
| 3 | `'X' refers to a value, but is being used as a type here` | Using runtime value where TypeScript type expected | Use `typeof X` for the type, or import the type separately: `import type { X }` |
| 4 | `Type 'string' is not assignable to type '"a" \| "b"'` | Literal type mismatch | Add `as const` to the value, or widen the type parameter |
| 5 | `Property 'X' does not exist on type '{}'` | Object type not properly defined | Define an interface/type, or use Zod schema with `z.infer<typeof schema>` |
| 6 | `Cannot use import statement outside a module` | ESM/CJS mismatch | Add `"type": "module"` in package.json, or rename file to `.mjs` |
| 7 | `ERR_REQUIRE_ESM` | Trying to `require()` an ESM-only package | Switch to `import()` (dynamic) or convert project to ESM |
| 8 | `ReferenceError: document is not defined` | Using browser API in server/Node context | Wrap in `if (typeof window !== 'undefined')` or move to `useEffect` |
| 9 | `ReferenceError: window is not defined` | Same as above — SSR environment | Same fix: guard with `typeof window` check or `useEffect` |
| 10 | `SyntaxError: Unexpected token '<'` | Server returning HTML instead of JS/JSON | Check API endpoint URL, verify server is running, check MIME types |
| 11 | `TypeError: X is not a function` | Calling non-function (undefined, wrong import) | Verify import is correct, check `typeof X` before calling |
| 12 | `TypeError: Cannot read properties of undefined (reading 'X')` | Accessing property on undefined/null | Add optional chaining: `obj?.X`, or add null check before access |
| 13 | `TypeError: Cannot read properties of null (reading 'X')` | Element not found in DOM or null API response | Check DOM element exists, add null check for API response |
| 14 | `Unhandled Runtime Error: Hydration failed` | Server/client HTML mismatch | Remove `Date.now()`, `Math.random()` from render; use `useEffect` for dynamic values |
| 15 | `Warning: Each child in a list should have a unique "key" prop` | Missing or non-unique key in .map() | Add `key={item.id}` (never use array index) |
| 16 | `Error: Rendered fewer hooks than expected` | Conditional hook call or early return before hooks | Move all hooks ABOVE any conditional returns |
| 17 | `CORS: No 'Access-Control-Allow-Origin' header` | Server missing CORS headers | Add CORS middleware on SERVER side, not client |
| 18 | `429 Too Many Requests` | Rate limiting | Add retry with exponential backoff, or increase rate limit on server |
| 19 | `ENOSPC: System limit for number of file watchers reached` | Linux inotify limit too low | `echo fs.inotify.max_user_watches=524288 \| sudo tee -a /etc/sysctl.conf && sudo sysctl -p` |
| 20 | `EADDRINUSE: address already in use :::3000` | Port already occupied | `lsof -i :3000 \| awk 'NR>1{print $2}' \| xargs kill -9` then restart |

### React / Next.js Instant Fixes

| # | Exact Error | Root Cause | Instant Fix |
|---|-------------|-----------|-------------|
| 21 | `Error: useState is not a function` | Using hooks in Server Component | Add `'use client'` at top of file |
| 22 | `Error: useEffect is not a function` | Same — hooks in Server Component | Add `'use client'` at top of file |
| 23 | `Error: Event handlers cannot be passed to Client Component props` | Passing onClick etc. to Server Component | Add `'use client'` to the component receiving the handler |
| 24 | `Error: Unsupported Server Component type: undefined` | Default export missing or wrong import | Verify component has `export default function` or `export default` |
| 25 | `Warning: Text content did not match` | Hydration mismatch | Wrap dynamic content in `useEffect`, avoid `new Date()` in render |
| 26 | `Error: Invalid src prop on next/image` | External image domain not configured | Add domain to `next.config.js`: `images: { remotePatterns: [{ hostname: '...' }] }` |
| 27 | `Error: NEXT_REDIRECT` or redirect() errors | Using redirect() in wrong context | Use `redirect()` in Server Components/actions only, use `useRouter().push()` in client |
| 28 | `Maximum update depth exceeded` | Infinite re-render loop | Check `useEffect` deps for object references, use primitives or `useMemo` |
| 29 | `Can't perform a React state update on unmounted component` | Setting state after unmount | Add cleanup: `useEffect(() => { let active = true; ...; return () => { active = false; } })` |
| 30 | `Invalid hook call. Hooks can only be called inside...` | Hook outside component, or duplicate React | Check: not calling hooks in regular functions; run `npm ls react` for duplicates |

### Python Instant Fixes

| # | Exact Error | Root Cause | Instant Fix |
|---|-------------|-----------|-------------|
| 31 | `ModuleNotFoundError: No module named 'X'` | Package not installed in active env | `pip install X` or check virtualenv is activated |
| 32 | `ImportError: cannot import name 'X' from 'Y'` | Wrong version or circular import | Check version: `pip show Y`, check for circular imports |
| 33 | `IndentationError: unexpected indent` | Mixed tabs/spaces or wrong indentation | Fix indentation; configure editor for spaces-only |
| 34 | `TypeError: 'NoneType' object is not subscriptable` | Accessing index/key on None return | Add `if result is not None:` check before access |
| 35 | `AttributeError: 'NoneType' object has no attribute 'X'` | Calling method on None | Add null check or trace where None originates |
| 36 | `RecursionError: maximum recursion depth exceeded` | Infinite recursion | Add base case, or use `sys.setrecursionlimit()` if legitimate deep recursion |
| 37 | `UnicodeDecodeError: 'utf-8' codec can't decode byte` | File not UTF-8 encoded | Open with `encoding='latin-1'` or detect: `chardet.detect(raw_bytes)` |
| 38 | `PermissionError: [Errno 13] Permission denied` | File/directory permission issue | Check permissions: `ls -la`, fix: `chmod 644 file` or run with correct user |
| 39 | `ConnectionRefusedError: [Errno 111]` | Service not running on target port | Start the service, verify host/port config |
| 40 | `JSONDecodeError: Expecting value` | Empty or non-JSON response | Check response status first: `if response.ok:`, log `response.text` before parsing |

### Docker / Nginx / Server Instant Fixes

| # | Exact Error | Root Cause | Instant Fix |
|---|-------------|-----------|-------------|
| 41 | `nginx: [emerg] bind() to 0.0.0.0:80 failed (98: Address already in use)` | Port 80 occupied | `sudo lsof -i :80` → kill process, or change nginx port |
| 42 | `413 Request Entity Too Large` | Nginx body size limit | Add `client_max_body_size 50m;` in nginx.conf server/location block |
| 43 | `502 Bad Gateway` | Upstream server not responding | Check if backend is running: `systemctl status <app>`, check proxy_pass URL |
| 44 | `docker: Error response: port is already allocated` | Host port in use | Change host port in docker-compose, or kill process using it |
| 45 | `Error: EACCES: permission denied, mkdir '/app/node_modules'` | Docker running as wrong user | Add `RUN chown -R node:node /app` before `USER node` in Dockerfile |
| 46 | `OOMKilled` (Docker/K8s) | Container exceeded memory limit | Increase memory limit, or fix memory leak in application |
| 47 | `SSL_ERROR_RX_RECORD_TOO_LONG` | HTTPS request hitting HTTP port | Check nginx listens on 443 with `ssl` directive, verify cert paths |
| 48 | `ERR_TOO_MANY_REDIRECTS` | Redirect loop (HTTP↔HTTPS) | Check nginx redirect rules, ensure only ONE redirect from 80→443 |
| 49 | `Permission denied (publickey)` on SSH | SSH key not configured | Check `~/.ssh/authorized_keys` on server, verify key with `ssh -vvv user@host` |
| 50 | `systemd: Failed to start` | Service config error or dependency issue | `journalctl -u <service> -n 50 --no-pager` to see exact error |

### Git Instant Fixes

| # | Exact Error | Root Cause | Instant Fix |
|---|-------------|-----------|-------------|
| 51 | `fatal: not a git repository` | Not in a git-tracked directory | `git init` or `cd` to correct directory |
| 52 | `error: failed to push some refs` | Remote has commits you don't | `git pull --rebase origin main` then `git push` |
| 53 | `CONFLICT (content): Merge conflict in X` | Two branches edited same lines | Open file, resolve `<<<<<<<` markers, then `git add X && git rebase --continue` |
| 54 | `fatal: refusing to merge unrelated histories` | Two repos with different roots | `git pull origin main --allow-unrelated-histories` |
| 55 | `error: Your local changes would be overwritten` | Uncommitted changes conflict | `git stash && git pull && git stash pop` |

<!-- IDX:INSTANT_FIX_END -->

---

# PART XIII: AI SMART CONTEXT GATHERING

<!-- IDX:SMART_CONTEXT_START -->
## 🧠 SMART CONTEXT GATHERING: What to Read Before Fixing

**Purpose:** The #1 reason AI fixes fail is incomplete context. This section tells the AI EXACTLY which files to read for each error category — eliminating guesswork entirely.

**Rule:** Before writing ANY fix, read every file in the relevant checklist below. No exceptions.

---

### Context Gathering by Error Type

```markdown
═══════════════════════════════════════════════════════════════
ERROR TYPE: BUILD / COMPILE FAILURE
═══════════════════════════════════════════════════════════════
MUST READ:
  □ The file that failed to compile (FULL file, not just error line)
  □ tsconfig.json / jsconfig.json (compiler options matter)
  □ package.json (dependency versions)
  □ vite.config.ts / next.config.js / webpack.config.js (bundler config)
  □ .env and .env.local (environment variables)

MUST CHECK:
  □ node_modules exists and lockfile is fresh
  □ TypeScript version matches config expectations
  □ All import paths resolve to real files

═══════════════════════════════════════════════════════════════
ERROR TYPE: RUNTIME CRASH / EXCEPTION
═══════════════════════════════════════════════════════════════
MUST READ:
  □ The file + function in the FIRST frame of the stack trace
  □ The file + function in the LAST frame before node_modules
  □ All files that CALL the crashing function (grep for function name)
  □ The data source: API route, database query, or state initialization

MUST CHECK:
  □ What is the ACTUAL shape of data at crash point? (log it)
  □ Is there a code path where the variable could be undefined/null?
  □ Did an API contract or database schema change recently?

═══════════════════════════════════════════════════════════════
ERROR TYPE: STYLING / CSS / LAYOUT BUG
═══════════════════════════════════════════════════════════════
MUST READ:
  □ The component file containing the broken element
  □ ALL CSS files imported by that component (including global CSS)
  □ Parent component (layout issues often come from parent)
  □ tailwind.config.js / postcss.config.js if using Tailwind

MUST CHECK:
  □ Browser DevTools → Computed tab → which styles are applied/overridden
  □ CSS specificity conflicts (ID > class > element)
  □ z-index stacking context
  □ Responsive breakpoints

═══════════════════════════════════════════════════════════════
ERROR TYPE: API / NETWORK / CORS
═══════════════════════════════════════════════════════════════
MUST READ:
  □ The API route handler (server-side)
  □ The fetch/axios call (client-side)
  □ Middleware files (auth, CORS, rate limiting)
  □ Reverse proxy config (nginx.conf, Caddyfile)
  □ .env files for API_URL, BASE_URL variables

MUST CHECK:
  □ Network tab: exact request URL, headers, status code, response body
  □ Does the server return proper Content-Type?
  □ Are cookies/auth tokens being sent? (credentials: 'include')
  □ Is the URL correct for the current environment (dev vs prod)?

═══════════════════════════════════════════════════════════════
ERROR TYPE: STATE MANAGEMENT / DATA FLOW
═══════════════════════════════════════════════════════════════
MUST READ:
  □ The component with wrong state
  □ The state store/context provider (Redux slice, Zustand store, Context)
  □ All components that WRITE to this state
  □ All components that READ this state

MUST CHECK:
  □ Is state being mutated directly? (must use immutable updates)
  □ Is the dependency array in useEffect complete?
  □ Is there a race condition between state updates?
  □ React DevTools → Components → inspect state values

═══════════════════════════════════════════════════════════════
ERROR TYPE: DATABASE / QUERY
═══════════════════════════════════════════════════════════════
MUST READ:
  □ The ORM model / Prisma schema / SQLAlchemy model
  □ The query/resolver/service that runs the failing query
  □ Recent migration files
  □ Database connection config (pool size, timeout)

MUST CHECK:
  □ Run the raw SQL in a DB client to verify the query itself
  □ EXPLAIN ANALYZE for performance issues
  □ Check migration status matches current schema
  □ Verify indexes exist for WHERE/JOIN columns

═══════════════════════════════════════════════════════════════
ERROR TYPE: DEPLOYMENT / INFRASTRUCTURE
═══════════════════════════════════════════════════════════════
MUST READ:
  □ Dockerfile and docker-compose.yml
  □ nginx.conf / Caddyfile (reverse proxy)
  □ CI/CD config (.github/workflows/, .gitlab-ci.yml)
  □ Environment-specific .env files
  □ systemd service file (if applicable)

MUST CHECK:
  □ `docker logs <container> --tail 50` for container errors
  □ `journalctl -u <service> -n 50` for systemd service errors
  □ `nginx -t` for config syntax
  □ `df -h` for disk space
  □ `free -m` for memory
  □ DNS resolution from server: `dig <domain>`

═══════════════════════════════════════════════════════════════
ERROR TYPE: AUTHENTICATION / AUTHORIZATION
═══════════════════════════════════════════════════════════════
MUST READ:
  □ Auth middleware / guard files
  □ JWT/session configuration
  □ Login/signup route handlers
  □ Frontend auth context/provider
  □ Protected route wrapper

MUST CHECK:
  □ Token format and expiry (decode JWT at jwt.io)
  □ Cookie settings (SameSite, Secure, HttpOnly, Domain, Path)
  □ CORS configuration (credentials must be true for cookies)
  □ Auth header format: "Bearer <token>" (common: missing "Bearer " prefix)

═══════════════════════════════════════════════════════════════
ERROR TYPE: PERFORMANCE / SLOW
═══════════════════════════════════════════════════════════════
MUST READ:
  □ The slow endpoint/component
  □ Database queries called by that endpoint (check for N+1)
  □ External API calls (check for sequential when could be parallel)
  □ Caching configuration

MUST CHECK:
  □ Chrome DevTools Performance tab (frontend)
  □ Database EXPLAIN ANALYZE (backend)
  □ Network waterfall for sequential calls
  □ Bundle size: `npx next build` or `npx vite build` shows chunk sizes
```

<!-- IDX:SMART_CONTEXT_END -->

---

# PART XIV: AI AUTO-RECOVERY & SELF-CORRECTION

<!-- IDX:AI_AUTO_RECOVERY_START -->
## 🔄 AI AUTO-RECOVERY PROTOCOL

**Purpose:** When an AI fix doesn't work, it MUST NOT keep trying the same approach. This section provides a deterministic recovery algorithm.

---

### The Fix Failure Escalation Ladder

```
FIX ATTEMPT #1 FAILED
    │
    ▼
┌────────────────────────────────────────────────────┐
│  STOP. Ask: "Did I misidentify the root cause?"    │
│  Action: Re-read the FULL file + stack trace       │
│  Action: Generate 3 NEW hypotheses (different      │
│          from the first one)                       │
│  Action: Test the #2 hypothesis                    │
└──────────────────┬─────────────────────────────────┘
                   │
FIX ATTEMPT #2 FAILED
    │
    ▼
┌────────────────────────────────────────────────────┐
│  STOP. Ask: "Am I looking at the right file?"      │
│  Action: Search the ENTIRE codebase for the error  │
│          pattern: grep -rn "error_text" .           │
│  Action: Check if the error is from a DEPENDENCY   │
│          (stack trace through node_modules?)        │
│  Action: Check if a CONFIG file is the real cause  │
│          (.env, tsconfig, nginx, docker)            │
└──────────────────┬─────────────────────────────────┘
                   │
FIX ATTEMPT #3 FAILED
    │
    ▼
┌────────────────────────────────────────────────────┐
│  STOP. This is likely an ARCHITECTURAL problem.     │
│                                                    │
│  Action: TELL THE USER honestly:                   │
│  "I've attempted 3 fixes and none resolved the     │
│   issue. This appears to be an architectural       │
│   problem that requires a broader investigation.   │
│   Here's what I've tried and ruled out:            │
│   1. [attempt 1] — failed because [reason]         │
│   2. [attempt 2] — failed because [reason]         │
│   3. [attempt 3] — failed because [reason]         │
│                                                    │
│   Recommended next steps:                          │
│   - [specific investigation suggestion]            │
│   - [potential architectural change needed]"       │
└────────────────────────────────────────────────────┘
```

---

### Common AI Fix Failures and Their Real Causes

```markdown
FAILURE PATTERN 1: "I fixed the type error but now there's a runtime crash"
  REAL CAUSE: The type error was a symptom. You silenced it with `as any` or 
              a type assertion without fixing the underlying data shape.
  RECOVERY: Remove the type assertion. Trace WHERE the data comes from. 
            Fix the data source, not the type annotation.

FAILURE PATTERN 2: "The fix works in dev but fails in build/production"
  REAL CAUSE: Dev mode is lenient (no tree shaking, no dead code elimination,
              no SSR, hot module replacement masks errors).
  RECOVERY: ALWAYS verify with `npm run build`. Check for:
            - Server-only code in client components
            - Dynamic imports with wrong paths
            - Environment variables missing NEXT_PUBLIC_ prefix

FAILURE PATTERN 3: "I fixed one component but broke three others"
  REAL CAUSE: You changed a shared function, type, or state without checking
              all consumers.
  RECOVERY: Before changing ANY shared code:
            grep -rn "functionName" src/ | wc -l
            If result > 5, this is high-risk. Map ALL callers first.

FAILURE PATTERN 4: "The error disappeared but the feature still doesn't work"
  REAL CAUSE: You fixed a secondary error while the primary cause is elsewhere.
              The error was masking the real problem (e.g., silent API failure).
  RECOVERY: Test the ACTUAL USER FLOW, not just "no error in console."
            Does the feature work end-to-end? Does the data appear correctly?

FAILURE PATTERN 5: "My fix introduced a new import that doesn't exist"
  REAL CAUSE: AI hallucinated a package or API that doesn't exist in this project.
  RECOVERY: BEFORE adding any import:
            ls node_modules/<package> 2>/dev/null || echo "NOT INSTALLED"
            grep '"<package>"' package.json || echo "NOT IN PACKAGE.JSON"

FAILURE PATTERN 6: "The tests pass but the bug is still visible in the browser"
  REAL CAUSE: Tests mock too much and don't test the real integration. The test
              validates the mock, not the actual behavior.
  RECOVERY: Write an E2E test (Playwright/Cypress) that interacts with the
            real UI. Or manually verify in the browser.

FAILURE PATTERN 7: "I keep going in circles — each fix reveals a new error"
  REAL CAUSE: You're fixing symptoms of a deeper issue. Common when:
              - Database schema doesn't match ORM models
              - API contract changed but types weren't updated
              - Two systems have diverged (frontend expects X, backend sends Y)
  RECOVERY: STOP fixing individual errors. Instead:
            1. Log the ACTUAL data at each boundary
            2. Compare what's sent vs what's received
            3. Fix the CONTRACT, then all symptoms resolve
```

---

### AI Self-Diagnostic Checklist (Run When Stuck)

```markdown
When your fix doesn't work, run through these questions:

□ READING: Did I read the FULL file, or just the error line?
  → If not: Read it now. The context around the error usually reveals the cause.

□ VERSION: Am I using the right API for the INSTALLED version?
  → Check: cat package.json | grep "<library>" — then verify the API docs for THAT version

□ SCOPE: Is the bug in MY code, or in a dependency?
  → Check: Does the stack trace pass through node_modules/?
  → If yes: Check GitHub issues for that package with the exact error message

□ ENVIRONMENT: Could this be an environment issue, not a code issue?
  → Check: Does it work in a fresh `rm -rf node_modules && npm install`?
  → Check: Are all .env variables set correctly?

□ DATA: Am I assuming the data shape is correct?
  → Check: console.log(JSON.stringify(data, null, 2)) at the failure point
  → Does the ACTUAL shape match what the code expects?

□ TIMING: Could this be a race condition?
  → Check: Does the error appear intermittently?
  → Check: Are there multiple async operations that might complete in different orders?

□ CACHE: Could this be a stale cache?
  → Fix: rm -rf .next dist node_modules/.cache .cache
  → Restart dev server fresh

□ HONESTY: Am I actually stuck and should I tell the user?
  → After 3 failed attempts: YES. Explain what you tried and suggest next steps.
```

<!-- IDX:AI_AUTO_RECOVERY_END -->

---

# PART XV: MODERN TOOLING QUICK REFERENCE (2025-2026)

<!-- IDX:MODERN_TOOLS_START -->
## 🆕 MODERN TOOLING UPDATES

**Purpose:** The ecosystem evolves rapidly. This section covers tools and patterns that became standard in 2025-2026, which older AI training data may not include.

### Runtime Alternatives

| Runtime | Key Difference | When to Use |
|---------|---------------|-------------|
| **Bun** | All-in-one: runtime + bundler + test runner + pkg manager | Fast iteration, new projects, replaces Node + npm + Jest |
| **Deno** | Secure by default, built-in TypeScript, web-standard APIs | Security-critical projects, edge deployments |
| **Node.js 22+** | Native TypeScript support (`--experimental-strip-types`), stable ESM | Existing Node projects, enterprise |

### Build Tool Evolution

```markdown
Webpack    → LEGACY (still works, but slow for new projects)
Vite       → STANDARD (fast dev server, Rollup for production)
Turbopack  → NEXT.JS DEFAULT (Rust-based, integrated with Next.js)
Rspack     → ALTERNATIVE (Webpack-compatible but Rust-based, 5-10x faster)
esbuild    → LIBRARY BUNDLING (fastest for simple builds)
Bun build  → ALTERNATIVE (built into Bun runtime)
```

### Linting & Formatting (2025 Standard)

```markdown
ESLint + Prettier → LEGACY COMBO (still works but slower)
Biome            → MODERN STANDARD (lint + format in one tool, Rust-based, 30x faster)
oxlint           → EMERGING (Rust-based, even faster than Biome for linting only)
dprint           → ALTERNATIVE formatter (Rust-based, plugin system)

Recommendation: New projects → Biome. Existing projects → keep current setup.
```

### Type Checking

```markdown
tsc              → STANDARD (TypeScript compiler, authoritative)
@ts-check in JS  → LIGHTWEIGHT (type checking in .js files via JSDoc)

Python:
mypy             → STANDARD (gradual typing, strict mode recommended)
pyright          → FASTER ALTERNATIVE (Microsoft, used by Pylance in VS Code)
pytype           → GOOGLE ALTERNATIVE (more inference, fewer annotations needed)
```

### Testing (2025 Standard)

```markdown
JavaScript:
  Vitest          → STANDARD (Vite-native, Jest-compatible API, fast)
  Playwright      → E2E STANDARD (cross-browser, auto-waiting, best API)
  
Python:
  pytest          → STANDARD (fixtures, parametrize, plugins)
  
Property-Based:
  fast-check (JS) → Standard for invariant testing
  Hypothesis (Py) → Standard for Python property testing

Snapshot Testing: Use SPARINGLY — only for complex serialized output, not UI.
```

### Package Managers (Speed Comparison)

```markdown
npm     → SLOWEST but most compatible (use npm ci in CI)
yarn    → FASTER, workspaces support
pnpm    → FASTEST (strict, disk-efficient, recommended for monorepos)
bun     → FASTEST INSTALL (native binary, not all npm packages compatible)

Python:
pip     → STANDARD (use with venv)
uv      → FASTEST (Rust-based pip replacement, 10-100x faster)
poetry  → STANDARD for project management (lock files, publishing)
```

### Security Scanning

```markdown
Tier 1 (Every Commit):
  semgrep --config=auto .         → Fast pattern matching (30+ languages)
  npm audit / pip-audit / govulncheck → Dependency vulnerabilities

Tier 2 (Weekly/Release):
  gitleaks detect --source .      → Secret detection in git history
  trivy fs --severity HIGH,CRITICAL . → Comprehensive vulnerability scan
  snyk test                       → Commercial-grade dep scanning

Tier 3 (Quarterly/Audit):
  CodeQL                          → Deep semantic analysis
  Bandit (Python)                 → Python-specific security lints
  Bearer                          → Data flow analysis for sensitive data
```

### AI-Specific Tools for Code Quality

```markdown
IMPORTANT: These supplement, not replace, traditional tools:

cursor/continue/cline → AI coding assistants (context-aware)
aider                → Terminal-based AI pair programmer
codegen.sh           → AI code generation with repo context
mentat               → AI code editor with full-repo understanding

Rule: AI tools generate code; traditional tools (linters, type checkers, 
tests) VERIFY it. Never ship AI-generated code without running the 
verification pipeline.
```

<!-- IDX:MODERN_TOOLS_END -->
