# ULTIMATE AI SEARCH, RESEARCH & VERIFICATION ARSENAL v3.0

> **Zero-Config AI Operating System for Deep Research, Real-Time Verification, Trusted-Source Discovery & Visual Validation**

---

<!-- IDX:ZERO_CONFIG_AUTOPILOT_START -->
## ⚡ PART 0: ZERO-CONFIG AI AUTO-PILOT ENGINE

> **THIS SECTION IS THE MASTER KEY.** When an AI coding assistant loads this file, it MUST execute the Auto-Pilot Protocol below FIRST. No manual configuration needed. No questions to ask. Just detect → research → verify → deliver.

---

### 🔑 THE AUTO-PILOT PRIME DIRECTIVE

```
WHEN YOU RECEIVE ANY TASK REQUIRING SEARCH, RESEARCH, OR VERIFICATION:

1. DO NOT ask the user what tools/APIs to use
2. DO NOT ask for clarification unless the request is genuinely ambiguous
3. INSTEAD: Run the Task Classification Protocol below SILENTLY
4. THEN: Execute the correct research path AUTOMATICALLY
5. VERIFY: Cross-reference findings against trusted sources
6. DELIVER: Answer + sources + confidence score — in ONE response
```

---

### 🧠 STEP 1: AUTO-CLASSIFY TASK TYPE (Run Silently)

```
INPUT: User request / question / task
                    │
    ┌───────────────┼───────────────────────────────────┐
    │               │                                   │
    ▼               ▼                                   ▼
QUICK LOOKUP    DEEP RESEARCH           VERIFICATION / DEBUGGING
(1 search)      (multi-source)          (cross-reference + test)
    │               │                                   │
    ▼               ▼                                   ▼
Single web      Multi-query             Search + read code +
search →        research chain →        run tests + visual
extract →       synthesize →            check + verify fix
deliver         cite sources            works correctly
```

**Auto-Classification Rules (AI executes silently):**

```markdown
IF task is "what is X" OR "how to X" OR simple factual question
  → CLASSIFY: QUICK_LOOKUP → Single targeted search

IF task involves "best practice" OR "architecture" OR "compare options"
  → CLASSIFY: DEEP_RESEARCH → Multi-source research chain

IF task involves debugging OR "why doesn't X work" OR error messages
  → CLASSIFY: VERIFY_DEBUG → Search + code analysis + visual verification

IF task involves "is this correct" OR "review" OR "validate"
  → CLASSIFY: VERIFICATION → Cross-reference against trusted sources

IF task involves building/coding a complex feature
  → CLASSIFY: IMPLEMENTATION_RESEARCH → Search for patterns + verify approach

IF task involves security OR vulnerability OR CVE
  → CLASSIFY: SECURITY_RESEARCH → Trusted security sources only

DEFAULT → DEEP_RESEARCH with verification
```

---

### 🎯 STEP 2: AUTO-EXECUTE RESEARCH PIPELINE

```
┌──────────────────────────────────────────────────────────────────┐
│                   AI AUTO-RESEARCH PIPELINE                      │
│                                                                  │
│  1. CLASSIFY  → Determine research depth needed (Step 1)         │
│  2. SEARCH    → Query using optimal search strategy              │
│  3. FILTER    → Prioritize trusted/authoritative sources         │
│  4. EXTRACT   → Pull relevant information from top results       │
│  5. VERIFY    → Cross-reference across multiple sources          │
│  6. VALIDATE  → Test/visualize when applicable                   │
│  7. DELIVER   → Present findings with sources + confidence       │
│                                                                  │
│  ⏱️ Target: Complete in ONE response, no back-and-forth          │
└──────────────────────────────────────────────────────────────────┘
```

---

### 🔍 STEP 3: SEARCH STRATEGY SELECTION

**The AI auto-selects the optimal search approach based on task type:**

```markdown
QUICK_LOOKUP:
  1. Single precise search query with exact error/term
  2. Read top 3 results
  3. Extract answer + cite source

DEEP_RESEARCH:
  1. Break topic into 2-4 sub-queries
  2. Search each independently
  3. Cross-reference findings
  4. Synthesize into coherent answer
  5. Cite all sources with relevance ranking

VERIFY_DEBUG:
  1. Search exact error message (in quotes)
  2. Search error + framework + version
  3. Check GitHub Issues for the specific library
  4. Check official docs for correct API usage
  5. Read the actual code files involved
  6. Run verification commands
  7. Visually confirm fix works (browser/preview)

IMPLEMENTATION_RESEARCH:
  1. Search for established patterns/solutions
  2. Check official documentation first
  3. Find real-world examples (GitHub, blogs)
  4. Verify approach works with project's stack version
  5. Implement with inline verification

SECURITY_RESEARCH:
  1. Check NVD/CVE databases
  2. Check GitHub Security Advisories
  3. Check official vendor advisories
  4. Cross-reference with exploit databases
  5. Verify patches exist and are applicable
```

---

### 🛡️ STEP 4: TRUSTED SOURCE HIERARCHY

**Always prioritize sources in this order:**

```markdown
TIER 1 — AUTHORITATIVE (Highest Trust):
  • Official documentation (docs.python.org, developer.mozilla.org, react.dev)
  • Official GitHub repos (issues, discussions, changelogs)
  • RFC documents, language specs
  • Vendor security advisories (NVD, GitHub Advisory)

TIER 2 — HIGH QUALITY:
  • Stack Overflow (accepted answers with high votes, check date)
  • Major tech blogs (engineering.fb.com, blog.golang.org)
  • Well-known authors/maintainers
  • Wikipedia for concepts/theory

TIER 3 — USEFUL BUT VERIFY:
  • Medium/Dev.to articles (check date, verify code works)
  • Tutorial sites (cross-reference with official docs)
  • Forum posts (check if solution was confirmed)

TIER 4 — LOW TRUST (Use Only as Hints):
  • AI-generated content on other sites
  • Undated articles
  • Sites with excessive ads/SEO optimization
  • Answers without upvotes or confirmations

REJECTION CRITERIA — Never Trust:
  • Solutions older than 2 years without checking if still valid
  • Code snippets without context or explanation
  • "Just do X" answers without explaining WHY
  • Solutions that disable security features (CORS, SSL verification)
```

---

### 📊 STEP 5: OUTPUT FORMAT (Mandatory)

```markdown
## 🔍 Research Finding
[Clear answer to the question/task]

## 📚 Sources
1. [Source name](URL) — Tier X — [why this source is relevant]
2. [Source name](URL) — Tier X — [key finding from this source]

## ✅ Verification
[How the finding was verified — tests run, code checked, visually confirmed]

## 🎯 Confidence Score: [X/10]
- 10: Multiple Tier 1 sources agree, verified with tests
- 7-9: Strong evidence from reliable sources
- 4-6: Partial evidence, some assumptions made
- 1-3: Best guess, limited sources available

## ⚠️ Caveats
[Any limitations, version-specific notes, or edge cases]
```

<!-- IDX:ZERO_CONFIG_AUTOPILOT_END -->

---

## PART 1: CORE SEARCH PRINCIPLES

### 1.1 The Search-First Protocol

**Before writing ANY code or making ANY recommendation:**

```markdown
MANDATORY SEARCH TRIGGERS:
□ Unfamiliar error message → Search exact error in quotes
□ Using a library API → Verify syntax for INSTALLED version
□ Recommending a tool → Confirm it's maintained and compatible
□ Security-related code → Check for known vulnerabilities
□ Complex algorithm → Find established implementations
□ "Should work but doesn't" → Search for known platform bugs
□ Performance optimization → Find benchmarked approaches
□ Deployment configuration → Verify against current docs
```

### 1.2 Query Formulation Best Practices

```markdown
EFFECTIVE QUERIES:
✅ "TypeError: Cannot read properties of undefined" react 18 useEffect
✅ next.js 14 app router server component fetch cache
✅ python fastapi pydantic v2 migration breaking changes 2024
✅ site:github.com/vercel/next.js "hydration mismatch" fix

INEFFECTIVE QUERIES:
❌ "my code doesn't work" (too vague)
❌ "react error" (too broad)
❌ "best framework 2024" (opinion-based, no single answer)
❌ Long paragraphs as search queries (noise reduces relevance)

QUERY REFINEMENT RULES:
1. Start specific → broaden only if no results
2. Include version numbers when relevant
3. Use exact error messages in quotes
4. Add "site:" to target specific domains
5. Add year/version to filter stale results
6. Use "-" to exclude irrelevant results
```

### 1.3 Cross-Reference Verification Protocol

```markdown
BEFORE ACCEPTING ANY SEARCH RESULT AS TRUTH:

□ Does this apply to the EXACT version we're using?
□ Is the answer from a Tier 1-2 source?
□ Has anyone confirmed this solution works? (check comments/replies)
□ Does this conflict with official documentation?
□ Is this answer recent enough to be relevant?
□ Does the proposed solution have security implications?

IF TWO SOURCES CONFLICT:
  1. Trust official docs over community posts
  2. Trust newer answers over older ones (check both)
  3. Trust answers with verification steps over "just do X"
  4. When in doubt, TEST the solution before recommending
```

---

## PART 2: REAL-TIME VERIFICATION & VISUAL VALIDATION

### 2.1 Visual Verification Protocol

**For web apps and UI work, the AI MUST visually verify changes:**

```markdown
VISUAL VERIFICATION STEPS:
1. Open the app in browser after making changes
2. Check the specific page/component that was modified
3. Verify layout renders correctly (no broken elements)
4. Check responsive behavior if applicable
5. Test interactive elements (clicks, forms, navigation)
6. Check browser console for errors/warnings
7. Screenshot or describe the visual state

WHEN TO VISUALLY VERIFY:
□ After ANY CSS/styling change
□ After ANY component structural change
□ After fixing a UI bug
□ After adding new UI features
□ After changing data that feeds into the UI
□ When user reports "it looks wrong"
```

### 2.2 Real-Time Issue Detection

**While working on ANY task, continuously monitor for:**

```markdown
REAL-TIME DETECTION CHECKLIST:
□ Terminal output — watch for warnings, deprecation notices
□ Build output — catch errors before they reach production
□ Browser console — JavaScript errors, network failures, CORS
□ Type checker output — new type errors from changes
□ Linter output — style violations, potential bugs
□ Test output — failing tests from changes
□ Network tab — failed API calls, wrong status codes

AUTO-DETECTION COMMANDS (run proactively):
  JS/TS: npx tsc --noEmit 2>&1 | head -20
  Python: python -m py_compile <changed_file>
  Build:  npm run build 2>&1 | tail -30
  Lint:   npx biome check <file> || npx eslint <file>
  Test:   npm test -- --related <file> 2>&1 | tail -20
```

### 2.3 Deep Analysis Protocol for Complex Tasks

```markdown
WHEN A TASK REQUIRES DEEP ANALYSIS:

PHASE 1 — UNDERSTAND THE FULL CONTEXT:
  1. Read ALL relevant files completely (not just the error line)
  2. Map the data flow: input → processing → output
  3. Identify all dependencies and side effects
  4. Check git history for recent changes: git log --oneline -10

PHASE 2 — RESEARCH THOROUGHLY:
  1. Search for the SPECIFIC error/issue with version context
  2. Check official docs for the features being used
  3. Look for GitHub issues matching the symptoms
  4. Find working examples of similar implementations
  5. Check for known breaking changes in recent updates

PHASE 3 — IMPLEMENT WITH VERIFICATION:
  1. Make the smallest possible change first
  2. Run type checker immediately after change
  3. Run affected tests immediately
  4. Build the project to catch compilation issues
  5. Visually verify if it's a UI change
  6. Check for regressions in adjacent functionality

PHASE 4 — VALIDATE DELIVERY:
  1. Confirm all original tests still pass
  2. Confirm the specific issue is resolved
  3. Confirm no new warnings/errors introduced
  4. Provide rollback instructions
```

---

## PART 3: SEARCH-POWERED DEBUGGING

### 3.1 Error-Driven Search Protocol

```markdown
WHEN YOU ENCOUNTER AN ERROR:

STEP 1 — Extract the searchable error signature:
  • Copy the EXACT error message (not paraphrased)
  • Note the error TYPE (TypeError, SyntaxError, ENOENT, etc.)
  • Note the file and line number
  • Note the stack trace's origin point

STEP 2 — Formulate 3 search queries (execute all):
  Query A: "<exact error message>" <framework> <version>
  Query B: <error type> <framework> <specific function/method>
  Query C: site:github.com/<library-org> "<error keywords>"

STEP 3 — Analyze search results:
  • Check if this is a KNOWN BUG with a fix/workaround
  • Check if this is a VERSION-SPECIFIC issue
  • Check if this is a CONFIGURATION issue
  • Check if official docs address this scenario

STEP 4 — Apply and verify:
  • Implement the most upvoted/confirmed solution
  • If multiple solutions exist, prefer official docs
  • Run verification commands after applying fix
  • If fix doesn't work, try next solution (max 3 attempts)
  • After 3 failed attempts: STOP and reassess the root cause
```

### 3.2 Common Error → Search Pattern Map

| Error Pattern | Search Query Template | Where to Look First |
|--------------|----------------------|-------------------|
| `Cannot find module 'X'` | `"Cannot find module X" <pkg-manager> <framework>` | package.json, node_modules |
| `TypeError: X is not a function` | `"X is not a function" <library> <version>` | Library changelog, API docs |
| `CORS error` | `CORS <backend-framework> <frontend-framework>` | Backend config, proxy setup |
| `Hydration mismatch` | `hydration mismatch <framework> <component-type>` | Server vs client rendering |
| `OOM / heap out of memory` | `heap out of memory <framework> <context>` | Memory profiling, data size |
| `ECONNREFUSED` | `ECONNREFUSED <port> <service>` | Service status, port binding |
| `Permission denied` | `EACCES permission denied <path> <OS>` | File permissions, user context |
| `Timeout` | `timeout <operation> <framework> <version>` | Network config, async handling |
| Python `ImportError` | `ImportError <module> python <version>` | requirements.txt, venv |
| Python `AttributeError` | `AttributeError <object> <attribute> <library>` | Library version, API changes |

### 3.3 Version-Aware Research

```markdown
CRITICAL: Always check the INSTALLED version before searching

FOR JAVASCRIPT/TYPESCRIPT:
  cat package.json | grep -E '"<library>"'
  npm ls <library>
  node -e "console.log(require('<library>/package.json').version)"

FOR PYTHON:
  pip show <library> | grep Version
  python -c "import <library>; print(<library>.__version__)"

THEN SEARCH WITH VERSION:
  ✅ "react-query v5 useQuery syntax"
  ✅ "pydantic v2 model_validate"
  ❌ "react-query useQuery" (might get v3/v4 syntax)
  ❌ "pydantic BaseModel" (might get v1 syntax)

VERSION MISMATCH IS THE #1 CAUSE OF "SOLUTION DOESN'T WORK":
  → The search result shows syntax for version X
  → Your project has version Y installed
  → The code compiles/runs but behaves wrong or crashes
```

---

## PART 4: SPECIALIZED RESEARCH PROTOCOLS

### 4.1 Security Research Protocol

```markdown
FOR ANY SECURITY-RELATED TASK:

1. CHECK VULNERABILITY DATABASES:
   • NVD: https://nvd.nist.gov/vuln/search
   • GitHub Advisory: https://github.com/advisories
   • Snyk: https://security.snyk.io/
   • npm audit / pip-audit / govulncheck

2. CHECK DEPENDENCY SECURITY:
   npm audit (JS/TS projects)
   pip-audit (Python projects)
   cargo audit (Rust projects)
   govulncheck ./... (Go projects)

3. VERIFY FIXES FROM SEARCH:
   □ Does the fix come from the library maintainer?
   □ Is there a CVE number associated?
   □ Is the patched version specified?
   □ Does the fix introduce breaking changes?

4. NEVER TRUST THESE "FIXES":
   ❌ "Just disable SSL verification"
   ❌ "Set CORS to allow all origins"
   ❌ "chmod 777 the directory"
   ❌ "Disable authentication for testing"
   ❌ "Use eval() to parse the input"
```

### 4.2 Performance Research Protocol

```markdown
FOR PERFORMANCE INVESTIGATION:

1. MEASURE FIRST (never optimize without data):
   • Browser: Lighthouse audit, DevTools Performance tab
   • Node.js: node --prof, clinic.js
   • Python: cProfile, py-spy
   • General: time command, benchmark scripts

2. SEARCH FOR KNOWN OPTIMIZATIONS:
   Query: "<framework> performance optimization <specific-area>"
   Query: "<slow-operation> alternative <language>"
   Query: "benchmark <approach-A> vs <approach-B> <language>"

3. VERIFY OPTIMIZATION ACTUALLY HELPS:
   □ Measure BEFORE applying optimization
   □ Apply ONE optimization at a time
   □ Measure AFTER — confirm improvement
   □ Check for correctness regressions
   □ Document the improvement percentage
```

### 4.3 Architecture & Best Practice Research

```markdown
FOR ARCHITECTURE DECISIONS:

1. SEARCH PATTERN:
   "<pattern-name> <framework> <use-case> best practice"
   "how to structure <feature> in <framework> <version>"
   site:github.com "<framework> example" <pattern>

2. EVALUATE FOUND PATTERNS:
   □ Is this pattern recommended by the framework authors?
   □ Is this pattern used in production by reputable companies?
   □ Does this pattern scale for our use case?
   □ Does this pattern have known downsides?
   □ Is there a simpler alternative that works?

3. PREFER:
   ✅ Official framework recommendations
   ✅ Patterns with test coverage examples
   ✅ Patterns used in the framework's own examples
   ❌ Over-engineered patterns for simple problems
   ❌ Patterns from outdated blog posts
   ❌ Patterns that require many new dependencies
```

---

## PART 5: AI OPERATIONAL PROTOCOLS

### 5.1 The Expert Research Mindset

```markdown
WHEN RESEARCHING, THE AI MUST:

1. ACT LIKE A SENIOR ENGINEER doing due diligence:
   • Don't accept the first answer found
   • Cross-reference multiple sources
   • Check dates and versions
   • Test solutions before recommending

2. BE SKEPTICAL OF:
   • Solutions that seem too simple for complex problems
   • Solutions that require disabling safety features
   • Solutions from a single unverified source
   • Solutions that "work" but aren't explained

3. ALWAYS PROVIDE:
   • The source of the information
   • The confidence level in the answer
   • Any caveats or version-specific notes
   • Alternative approaches when available
```

### 5.2 Handling Uncertainty

```markdown
WHEN SEARCH RESULTS ARE INSUFFICIENT:

LEVEL 1 — Partial Information:
  "Based on [source], the likely answer is X, but I could not
   verify this against official documentation. Confidence: 5/10."

LEVEL 2 — Conflicting Information:
  "Source A says X, but Source B says Y. The most reliable source
   (official docs) suggests X. I recommend testing both approaches."

LEVEL 3 — No Reliable Information:
  "I could not find a verified solution for this specific scenario.
   Here are the closest matches I found:
   1. [approach] from [source] — may apply with modifications
   2. [approach] from [source] — different context but similar
   Recommendation: Test approach 1 first, then 2."

LEVEL 4 — Genuinely Unknown:
  "This appears to be an undocumented edge case. I recommend:
   1. Filing a GitHub issue with the library maintainer
   2. Testing the behavior directly with a minimal reproducer
   3. Checking the library source code for the relevant function"
```

### 5.3 Continuous Learning Protocol

```markdown
AFTER EVERY RESEARCH TASK:

1. NOTE what worked:
   • Which search queries were effective
   • Which sources were most helpful
   • What verification steps confirmed the answer

2. NOTE what failed:
   • Search queries that returned irrelevant results
   • Sources that had outdated information
   • Solutions that didn't work and why

3. APPLY learnings to future tasks:
   • Refine query patterns
   • Update trusted source rankings
   • Remember version-specific gotchas
```

---

## PART 6: INTEGRATED VERIFICATION WORKFLOWS

### 6.1 Web App Verification Workflow

```markdown
AFTER MAKING CHANGES TO A WEB APPLICATION:

1. BUILD VERIFICATION:
   npm run build  (or equivalent)
   → Check for compilation errors
   → Check for type errors
   → Check for missing imports

2. VISUAL VERIFICATION:
   Open browser to the affected page
   → Does it render correctly?
   → Are there console errors?
   → Do interactive elements work?
   → Does it look right on different viewport sizes?

3. FUNCTIONAL VERIFICATION:
   Test the specific feature/fix
   → Does the original issue still exist? (should be fixed)
   → Do related features still work? (should not be broken)
   → Edge cases: empty data, large data, error states

4. PERFORMANCE VERIFICATION:
   → Page loads within acceptable time
   → No excessive network requests
   → No memory leaks in dev tools
```

### 6.2 API/Backend Verification Workflow

```markdown
AFTER MAKING CHANGES TO AN API:

1. BUILD: python -m py_compile <file> OR tsc --noEmit
2. TEST: Run affected test suite
3. MANUAL: curl or test the endpoint directly
4. CHECK: Response format matches expected schema
5. VERIFY: Error handling works for invalid inputs
6. CONFIRM: Authentication/authorization still works
```

### 6.3 Configuration Verification Workflow

```markdown
AFTER CHANGING CONFIGURATION:

1. VALIDATE syntax: nginx -t, docker compose config, etc.
2. CHECK environment variables are set
3. VERIFY service can start with new config
4. TEST connectivity to dependent services
5. CONFIRM no secrets are exposed in logs/output
```

---

## PART 7: QUALITY GATES

### 7.1 Pre-Delivery Quality Gates

```markdown
BEFORE PRESENTING ANY RESEARCH FINDING OR FIX:

GATE 1 — SOURCE QUALITY:
  □ At least one Tier 1-2 source supports the finding
  □ No sole reliance on Tier 4 sources
  □ Sources are dated within the relevant timeframe

GATE 2 — VERSION ACCURACY:
  □ The solution applies to the project's actual versions
  □ API syntax has been verified against installed version
  □ No deprecated features are recommended

GATE 3 — COMPLETENESS:
  □ The answer fully addresses the user's question
  □ Edge cases and caveats are mentioned
  □ Alternative approaches noted when relevant

GATE 4 — VERIFICATION:
  □ Solution has been tested or is testable
  □ Verification steps are provided
  □ Rollback plan exists for code changes

GATE 5 — SAFETY:
  □ No security features disabled
  □ No secrets exposed
  □ No destructive commands without warning

IF ANY GATE FAILS → Fix the issue before presenting.
```

### 7.2 Confidence Scoring Rubric

```markdown
10/10 — VERIFIED FACT
  Multiple Tier 1 sources agree + tested + visually confirmed

8-9/10 — HIGH CONFIDENCE
  Official docs confirm + community consensus + tested

6-7/10 — MODERATE CONFIDENCE
  Good sources but not fully tested, or minor version uncertainty

4-5/10 — LOW CONFIDENCE
  Limited sources, some assumptions made, needs user verification

1-3/10 — BEST GUESS
  Minimal evidence, extrapolated from similar cases

0/10 — UNKNOWN
  Insufficient information to provide a reliable answer
```

---

## PART 8: SEARCH INTEGRATION WITH CODING WORKFLOW

### 8.1 When to Search During Coding

```markdown
AUTOMATIC SEARCH TRIGGERS (no user prompt needed):

□ Encountering an unfamiliar error → search immediately
□ About to use a library API for the first time → verify syntax
□ User's error persists after first fix attempt → search deeper
□ Implementing a security-sensitive feature → check best practices
□ Performance concern raised → search for benchmarks
□ Working with a framework you haven't used recently → check for updates
□ A dependency has a major version difference → check migration guide
```

### 8.2 Search-Enhanced Fix Pattern

```markdown
FOR EVERY BUG FIX:

1. READ the code fully (no searching yet)
2. FORM initial hypothesis based on code reading
3. SEARCH to verify hypothesis:
   • Is this a known bug?
   • Is the API being used correctly for this version?
   • Are there documented edge cases?
4. IMPLEMENT fix based on evidence (not guessing)
5. VERIFY fix works (build + test + visual if UI)
6. SEARCH for potential side effects of the fix
7. DELIVER with sources and confidence score
```

### 8.3 Proactive Research Before Complex Tasks

```markdown
BEFORE STARTING A COMPLEX IMPLEMENTATION:

1. SEARCH for existing solutions/patterns:
   "<what-to-build> <framework> example"
   "<what-to-build> <framework> best practice"

2. REVIEW 2-3 real-world implementations:
   • How do they structure the code?
   • What edge cases do they handle?
   • What libraries do they use?

3. CHECK for common pitfalls:
   "<what-to-build> <framework> gotchas"
   "<what-to-build> <framework> mistakes to avoid"

4. THEN implement with informed decisions
```

---

## PART 9: FORBIDDEN PATTERNS & ANTI-PATTERNS

### 9.1 Search Anti-Patterns

```markdown
NEVER DO THESE:

❌ Copy-paste code from search results without understanding it
❌ Trust a single Stack Overflow answer without checking the date
❌ Recommend a library without checking if it's maintained
❌ Use search results for version X when project uses version Y
❌ Skip searching because "I know the answer" — verify anyway
❌ Search once and give up — refine query and try again
❌ Trust solutions that disable security features
❌ Recommend "just upgrade to latest" as a fix for bugs
```

### 9.2 Research Anti-Patterns

```markdown
NEVER DO THESE:

❌ Present AI-hallucinated information as fact
❌ Mix information from different versions/frameworks
❌ Ignore deprecation warnings found during research
❌ Skip cross-referencing when sources disagree
❌ Present opinions as facts
❌ Omit caveats or limitations of a solution
❌ Recommend solutions you haven't verified
```

---

## PART 10: EMERGENCY PROTOCOLS

### 10.1 Production Emergency Research

```markdown
WHEN PRODUCTION IS DOWN:

PRIORITY: Stabilize first, investigate second.

1. QUICK SEARCH (30 seconds max):
   "<exact error>" site:github.com/<framework>
   "<exact error>" fix workaround

2. IF known issue found → Apply documented fix immediately
3. IF unknown issue → Stabilize with rollback, then research

4. POST-INCIDENT: Deep research into root cause
   • Search for similar incidents
   • Check for upstream bugs
   • Document findings for future reference
```

### 10.2 "Nothing Works" Protocol

```markdown
WHEN MULTIPLE FIX ATTEMPTS FAIL:

1. STOP fixing. Start investigating from scratch.
2. Question your assumptions:
   • Is the error actually where you think it is?
   • Are you reading the error message correctly?
   • Is the version really what you think?
3. Search with completely different query angles
4. Look at the problem from the user's perspective
5. Check if the issue is environmental (OS, permissions, network)
6. Consider: is the original assumption about root cause wrong?
7. If still stuck after 3 approaches: Tell the user honestly
```

---

## APPENDIX A: QUICK REFERENCE — Search Query Templates

```markdown
ERROR DIAGNOSIS:
  "<exact error message>" <framework> <version>
  <error-type> <library> <function-name> <version>
  site:github.com/<org>/<repo> "<error keywords>"
  site:stackoverflow.com "<error>" [<framework>]

API VERIFICATION:
  <library> <function-name> API <version> documentation
  site:<official-docs-url> <function-name>
  <library> changelog <version> breaking changes

BEST PRACTICES:
  <topic> best practice <framework> <year>
  <topic> <framework> official recommendation
  <topic> production <framework> example

SECURITY:
  CVE <library> <version>
  <library> security advisory <year>
  site:github.com/advisories <library>

PERFORMANCE:
  <operation> performance <framework> optimization
  <approach-A> vs <approach-B> benchmark <language>
  <framework> profiling <specific-area>
```

## APPENDIX B: TRUSTED DOMAIN QUICK LIST

```markdown
ALWAYS CHECK FIRST:
  developer.mozilla.org (MDN) — Web APIs, CSS, HTML, JS
  docs.python.org — Python standard library
  react.dev — React official docs
  nextjs.org/docs — Next.js official docs
  vitejs.dev — Vite official docs
  typescriptlang.org — TypeScript docs
  nodejs.org/api — Node.js API docs
  github.com/<library> — Source code & issues
  stackoverflow.com — Community solutions (check date + votes)

SECURITY:
  nvd.nist.gov — CVE database
  github.com/advisories — GitHub Security Advisories
  security.snyk.io — Snyk vulnerability database
  cve.mitre.org — CVE identifiers

COMPATIBILITY:
  caniuse.com — Browser feature support
  pypi.org — Python package info
  npmjs.com — npm package info
```

---

*Architecture: Zero-Config AI Search & Research Operating System.*
*Methodology: Trusted-Source Hierarchy, Visual Verification, Real-Time Issue Detection, Confidence-Scored Delivery.*
*Version: 3.0 — Optimized for AI assistants to use directly without configuration.*
