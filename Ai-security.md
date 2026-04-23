# AI WEB APP SECURITY — AUTONOMOUS OPERATING FRAMEWORK v3.0

> **Zero-Config · Self-Executing · AI-Native · Anti-Hallucination Enforced · Version-Pinned**

---

<!-- IDX:ZERO_CONFIG_SECURITY_AUTOPILOT_START -->
## ⚡ PART 0: ZERO-CONFIG AI AUTO-PILOT ENGINE

> **THIS SECTION IS THE MASTER KEY.** When an AI assistant loads this file, it MUST execute the Auto-Pilot Protocol below FIRST. No manual configuration. No "paste as system message." No questions. Just detect → scan → verify → harden → report.

---

### 🔑 THE AUTO-PILOT PRIME DIRECTIVE

```
WHEN YOU RECEIVE ANY SECURITY-RELATED TASK:

1. DO NOT ask the user to paste prompts or configure tools
2. DO NOT ask for clarification unless the target is genuinely ambiguous
3. INSTEAD: Run the Task Classification Protocol below SILENTLY
4. THEN: Execute the correct security pipeline AUTOMATICALLY
5. VERIFY: Prove every finding with the VERIFICATION BLOCK (Part 2.4) — NEVER hallucinate
6. SCORE: Apply the Confidence Scoring formula (Part 2.3) to every finding
7. DELIVER: Findings + fixes + evidence + confidence score — in ONE response
```

---

### 🧠 STEP 1: AUTO-CLASSIFY SECURITY TASK TYPE (Run Silently)

```
INPUT: User request / target / task
                    │
    ┌───────────────┼───────────────────────────────────┐
    │               │                                   │
    ▼               ▼                                   ▼
QUICK AUDIT     FULL SECURITY SCAN        INCIDENT RESPONSE
(headers/TLS)   (SAST+SCA+DAST+Secrets)   (active threat)
    │               │                                   │
    ▼               ▼                                   ▼
Single target   Multi-tool pipeline →     Emergency lockdown →
scan → report   cross-validate →          Phase A→E protocol →
                remediate + harden        rotate → report
```

**Auto-Classification Rules (AI executes silently):**

```markdown
IF task is "check security of URL" OR "scan headers" OR "check TLS"
  → CLASSIFY: QUICK_AUDIT → Headers + TLS + basic nuclei scan

IF task is "full audit" OR "security scan" OR repo/path provided
  → CLASSIFY: FULL_SCAN → Complete pipeline (SCA→SAST→Secrets→DAST→IaC)

IF task involves "we've been hacked" OR "breach" OR "active attack"
  → CLASSIFY: INCIDENT_RESPONSE → Phase A→E emergency lockdown (Part 4.2)

IF task involves "harden" OR "secure this code" OR "fix vulnerabilities"
  → CLASSIFY: HARDENING → Targeted remediation + NEVER/ALWAYS fixes (Part 3.1)

IF task involves "CI/CD security" OR "pipeline" OR "DevSecOps"
  → CLASSIFY: DEVSECOPS → Generate CI/CD security workflows (Part 5)

IF task involves LLM/AI app security OR "prompt injection"
  → CLASSIFY: AI_SECURITY → LLM-specific audit (Part 4.3 + OWASP LLM Top 10)

IF task involves "code review" OR "is this secure"
  → CLASSIFY: CODE_REVIEW → Manual SAST + NEVER/ALWAYS pattern check (Part 3.1)

DEFAULT → FULL_SCAN with cross-validation
```

---

### 🎯 STEP 2: AUTO-EXECUTE SECURITY PIPELINE

```
┌──────────────────────────────────────────────────────────────────┐
│              AI AUTO-SECURITY PIPELINE                           │
│                                                                  │
│  1. CLASSIFY  → Determine audit depth needed (Step 1)            │
│  2. DETECT    → Auto-detect tech stack from project files        │
│  3. PREPARE   → Check/install tools, create report directory     │
│  4. SCAN      → Execute tools in correct order with safe flags   │
│  5. VERIFY    → Run verification block per tool (Part 2.4)       │
│  6. VALIDATE  → Cross-reference findings, score confidence       │
│  7. REMEDIATE → Generate NEVER/ALWAYS fixes for verified finds   │
│  8. DELIVER   → Report + evidence + confidence scores            │
│                                                                  │
│  ⏱️ Target: Complete autonomously, no back-and-forth             │
└──────────────────────────────────────────────────────────────────┘
```

---

### 🛡️ STEP 3: STACK DETECTION (Always Run First)

```markdown
AUTO-DETECT BY INSPECTING THESE FILES:
  package.json / package-lock.json → Node.js (check for express, next, react)
  requirements.txt / pyproject.toml / Pipfile → Python (check for django, flask, fastapi)
  pom.xml / build.gradle → Java (check for spring-boot)
  go.mod → Go
  composer.json → PHP (check for laravel)
  Cargo.toml → Rust
  Gemfile → Ruby (check for rails)
  Dockerfile / docker-compose.yml → Container info → enable container scanning
  .github/workflows/ → Existing CI/CD → scan for secret exposure
  .env or .env.example → FLAG IMMEDIATELY as potential secret leak (HIGH RISK)
  terraform/ or *.tf files → enable IaC scanning (Checkov)

ALSO DETECT FROM HTTP HEADERS (if URL target):
  X-Powered-By, Server, Set-Cookie patterns, CSP headers
  PHPSESSID cookie → PHP | JSESSIONID cookie → Java | JWT in Authorization → JWT auth

IDENTIFY:
  □ Primary language + version
  □ Framework + version
  □ Dependency manager
  □ Auth model (JWT, session, OAuth, API key)
  □ Server/runtime type
  □ Exposed public endpoints
  □ Container/IaC presence

IF AMBIGUOUS → Fall back to polyglot-safe universal tools:
  Semgrep (--config auto), Trivy (fs), GitLeaks

OUTPUT: Print RECON SUMMARY block before any tool runs:
  Language: [detected] | Framework: [detected] | Auth: [detected]
  Containers: yes/no | IaC: yes/no | .env files: yes/no (HIGH RISK if yes)
```

<!-- IDX:ZERO_CONFIG_SECURITY_AUTOPILOT_END -->

---

## PART 1: TOOL ORCHESTRATION ENGINE

### 1.1 Tool Selection Matrix (Pinned Minimum Versions)

```markdown
⚠️ VERSION RULE: Always use pinned versions. NEVER use :latest or @latest tags.
   Newer stable versions are acceptable. Older versions may have different APIs.

SAST (Static Analysis):
  Tool          Min Version  Stack       Safe Install
  semgrep       1.45.0       Universal   pip install semgrep==1.45.0
  bandit        1.7.7        Python      pip install bandit==1.7.7
  eslint-sec    8.x          Node.js     npm install --save-dev eslint@8 eslint-plugin-security
  find-sec-bugs 1.13.0       Java        via SpotBugs 4.7.3 + fsb plugin jar
  brakeman      6.1.2        Rails       gem install brakeman -v 6.1.2
  gosec         2.18.0       Go          go install github.com/securego/gosec/v2/cmd/gosec@v2.18.0

  Run flags (use exactly):
  semgrep: semgrep --config auto --metrics off --json -o ./security-reports/semgrep.json .
  bandit:  bandit -r . -f json -o ./security-reports/bandit.json --severity-level medium
  gosec:   gosec -fmt=json -out=./security-reports/gosec.json -severity medium ./...

SCA (Dependency Scanning):
  Tool              Min Version  Safe Install
  trivy             0.50.0       docker pull aquasec/trivy:0.50.0
  owasp-dep-check   9.0.9        docker pull owasp/dependency-check:9.0.9

  Run flags:
  trivy: docker run --rm -v "$(pwd):/workspace" aquasec/trivy:0.50.0 \
           fs /workspace --scanners vuln,secret --format json \
           -o /workspace/security-reports/trivy.json

Secrets Detection:
  Tool        Min Version  Safe Install
  gitleaks    8.18.0       docker pull zricethezav/gitleaks:v8.18.0
  trufflehog  3.67.0       docker pull trufflesecurity/trufflehog:3.67.0

  Run flags:
  gitleaks: docker run --rm -v "$(pwd):/path" zricethezav/gitleaks:v8.18.0 \
              detect --source /path --report-format json \
              --report-path /path/security-reports/gitleaks.json
  trufflehog: docker run --rm -v "$(pwd):/repo" trufflesecurity/trufflehog:3.67.0 \
                filesystem /repo --json > ./security-reports/trufflehog.json

DAST (Dynamic — only if live URL target provided):
  Tool        Min Version  Safe Install
  nuclei      3.1.5        docker pull projectdiscovery/nuclei:v3.1.5
  zaproxy     2.14.0       docker pull ghcr.io/zaproxy/zaproxy:2.14.0

  Run flags (PASSIVE ONLY — active attack mode requires explicit user consent):
  nuclei: docker run --rm projectdiscovery/nuclei:v3.1.5 \
            -u [TARGET] -t http/ -severity critical,high,medium \
            -rate-limit 10 -timeout 20 -jsonl -o ./security-reports/nuclei.json
  zap:    docker run --rm -v "$(pwd)/security-reports:/zap/wrk" \
            ghcr.io/zaproxy/zaproxy:2.14.0 \
            zap-baseline.py -t [TARGET] -J /zap/wrk/zap.json

TLS/Headers (URL targets only):
  Tool        Min Version  Safe Install
  testssl     3.2          git clone --branch 3.2 https://github.com/drwetter/testssl.sh
  httpx       1.3.7        docker pull projectdiscovery/httpx:v1.3.7

  Run flags:
  testssl: ./testssl.sh --jsonfile ./security-reports/testssl.json [TARGET]
  headers: curl -sI [TARGET] | tee ./security-reports/headers.txt

IaC/Containers (if Dockerfile or .tf files detected):
  Tool        Min Version  Safe Install
  checkov     3.2.0        docker pull bridgecrew/checkov:3.2.0
  trivy       0.50.0       (reuse SCA image, add --config flag)

  Run flags:
  checkov: docker run --rm -v "$(pwd):/tf" bridgecrew/checkov:3.2.0 \
             -d /tf --output json --output-file-path /tf/security-reports/
```

### 1.2 Execution Rules (Non-Negotiable)

```markdown
AUTOMATION RULES:

✅ AUTO-INSTALL: command -v [tool] || which [tool] to check.
   If missing → install via brew/pip/npm/go install (pinned version).
   If conflicts → Docker fallback with read-only volume mount:
     docker run --rm --read-only --cap-drop ALL \
       --security-opt no-new-privileges \
       -v "$(pwd):/workspace:ro" [image]:[pinned-version]

✅ AUTO-DIRECTORY: mkdir -p ./security-reports before any scan.

✅ SAFE FLAGS (apply to EVERY tool):
   --timeout 120 (or tool equivalent)
   Rate limit: max 10 requests/second for DAST tools
   No destructive payloads — passive/safe scanning ONLY
   ⛔ Active attack tools (SQLMap, nmap --script vuln, ZAP active scan)
      require EXPLICIT "yes, run active scans" message from user

✅ PIPELINE ORDER: SCA → SAST → Secrets → DAST → Headers/TLS → IaC

✅ GRACEFUL DEGRADATION: If one tool fails, log error, continue pipeline.
   Never halt the full pipeline for a single tool failure.

✅ VERSION PINS: Never use :latest or @latest tags in generated scripts.
   Always resolve to a specific pinned version number.

✅ NO PLACEHOLDERS: Never output <YOUR_PATH>, <TARGET>, <API_KEY>.
   Always resolve to actual detected values.

✅ NO MANUAL STEPS: Never say "install Java first" or "download this file."
   Handle all prerequisites inside the script automatically.
```

### 1.3 Script Generation

```markdown
GENERATE ONE UNIFIED SCRIPT: auto-security-audit.sh

REQUIREMENTS:
  1. Fully commented — explain each section
  2. Creates ./security-reports/ directory
  3. Checks for each tool (pinned version), installs if missing
  4. Generates inline configs via heredoc when needed
  5. Runs all applicable tools sequentially
  6. Aggregates results into SECURITY_SUMMARY.json with structure:
     { "target": "...", "scan_date": "ISO8601", "tool_versions": {...},
       "totals": {"critical": N, "high": N, "medium": N, "low": N},
       "findings": [...] }
  7. Must pass: shellcheck auto-security-audit.sh (run this, show output)
  8. Must be executable: chmod +x auto-security-audit.sh

ALSO GENERATE: .github/workflows/auto-security.yml (see Part 5)
```

---

## PART 2: CROSS-VALIDATION & ANTI-HALLUCINATION

### 2.1 Finding Validation Protocol

```markdown
FOR EVERY FINDING, APPLY ALL CHECKS BEFORE REPORTING:

1. CROSS-REFERENCE: Finding must be confirmed by ≥2 tools
   OR match an official CVE/CWE/OSV entry (see Part 8 for trusted sources).

2. EXPLOITABILITY CHECK:
   □ Is the vulnerable code reachable from a public endpoint?
   □ Is it behind authentication?
   □ Is it in a dependency or in custom application code?
   □ Is the vulnerable function actually called?

3. FALSE POSITIVE FILTER:
   □ Check tool baselines for known false positive patterns
   □ Read the actual code at the flagged location
   □ Verify the finding makes sense in context
   □ If >500 raw findings: deduplicate by (tool, rule_id, file_path),
     keep highest-severity instance per group. Report dedup ratio.

4. SEVERITY ASSIGNMENT (use CVSS v3.1):
   □ Base score from CVSS calculator
   □ Adjust for exploit maturity (is there a public exploit?)
   □ Adjust for business impact context

5. APPLY CONFIDENCE SCORING (Part 2.3) → assign status tag
```

### 2.2 Anti-Hallucination Rules

```markdown
HARD RULES — VIOLATING ANY IS A PIPELINE FAILURE:

❌ NEVER fabricate CVE numbers — only cite CVEs confirmed via Part 8 Tier 1/2 sources
❌ NEVER invent tool output — only report what tools actually returned
❌ NEVER fake code fixes — only provide fixes you can verify against language spec
❌ NEVER claim a scan ran if tool verification block (Part 2.4) shows FAILED/SKIPPED
❌ NEVER report findings without evidence (tool output or code reference)
❌ NEVER advance a finding to VERIFIED if its tool has status FAILED in Part 2.4
❌ NEVER mix OWASP categories from different years (use 2021 A01–A10 only)

PROOF REQUIREMENTS:
  □ Show actual command executed (no placeholders)
  □ Show actual output (truncate if >50 lines, mark with [...])
  □ Link finding to specific file:line when possible
  □ Cite CVE/CWE database entries by actual ID
  □ If confidence <40/100 → tag FALSE_POSITIVE, omit from report
```

### 2.3 Confidence Scoring (0–100 Additive Formula)

```markdown
SCORE EACH FINDING by adding these components:

SOURCE CONFIRMATION:
  Finding confirmed by ≥2 independent tools         +30
  Finding confirmed by 1 tool only                  +10
  Pattern match only, no tool confirmation            +0

CVE/CWE DATABASE MATCH:
  Matched to official CVE in NVD or OSV             +25
  Matched to CWE ID only (no specific CVE)          +10
  No database match found                             +0

EXPLOITABILITY CONTEXT:
  Code reachable from public endpoint               +20
  Code is behind authentication                     +10
  Code in library not called by app                  +5
  Code path cannot be determined                     +0

REMEDIATION CLARITY:
  Exact file:line and fix available                 +15
  File identified, line not confirmed                +8
  Category only, no specific location                +0

FALSE POSITIVE CHECK:
  Passes baseline FP filter for this rule ID        +10
  Rule has known high FP rate (check tool docs)     -15

TOTAL SCORE → STATUS TAG:
  85–100  →  VERIFIED          (include in report)
  65–84   →  LIKELY_TRUE       (include in report)
  40–64   →  NEEDS_REVIEW      (include only if Critical severity)
  0–39    →  FALSE_POSITIVE    (omit — count only in summary)

MINIMUM REPORTING THRESHOLD: Only report findings scoring ≥40/100.

OUTPUT FORMAT per finding:
  Confidence: [score]/100
  Breakdown: source(+N) cve(+N) exploit(+N) clarity(+N) fp(+N or -N)
  Status: VERIFIED / LIKELY_TRUE / NEEDS_REVIEW / FALSE_POSITIVE
```

### 2.4 Per-Tool Verification Blocks (Visual Proof Protocol)

```markdown
AFTER EACH TOOL RUNS, produce this verification block BEFORE reporting findings.
This proves execution was real. Never skip this step.

─────────────────────────────────────────────────
TOOL VERIFY: [tool name] [version]
Command run:  [exact command with all flags — no placeholders]
Exit code:    [actual numeric exit code: 0, 1, 2...]
Duration:     [elapsed seconds]
Output size:  [bytes or line count in output file]
Sample line:  [first non-empty line of real stdout/stderr, max 120 chars]
Status:       EXECUTED | SKIPPED (reason: ...) | FAILED (error: ...)
─────────────────────────────────────────────────

VERIFICATION RULES:
  ✗ Exit code 0 + zero bytes output → Status = FAILED (tool scanned nothing)
  ✗ Tool status FAILED → its findings are DISCARDED, not reported
  ✗ No sample line available → findings tagged NEEDS_REVIEW, never VERIFIED
  ✗ Docker pull fails → log SKIPPED, attempt native install, new verify block

VISUAL PROGRESS LOG (print to console during execution):
  [STAGE 1/6]  SCA      → trivy:0.50.0         RUNNING...
  [STAGE 1/6]  SCA      → trivy:0.50.0         DONE (exit 0, 4.2s, 18 findings)
  [STAGE 2/6]  SAST     → semgrep:1.45.0       RUNNING...
  [STAGE 2/6]  SAST     → semgrep:1.45.0       DONE (exit 0, 12.1s, 43 findings → 7 after dedup)
  (etc. — print this log before the findings table)
```

---

## PART 3: REMEDIATION & HARDENING

### 3.1 Secure Code Fixes — NEVER/ALWAYS Patterns (Per Stack)

```markdown
PYTHON / DJANGO / FLASK / FASTAPI (Python 3.10+ / Django 4.x):

  SQL Injection:
    NEVER:  cursor.execute("SELECT * FROM users WHERE id=" + user_id)
    ALWAYS: cursor.execute("SELECT * FROM users WHERE id = %s", (user_id,))
    ALWAYS: User.objects.filter(id=user_id)  # Django ORM preferred

  Password Hashing:
    NEVER:  hashlib.md5(password.encode()).hexdigest()
    NEVER:  hashlib.sha256(password.encode()).hexdigest()
    ALWAYS: import bcrypt; bcrypt.hashpw(password.encode(), bcrypt.gensalt(rounds=12))
    ALWAYS: from django.contrib.auth.hashers import make_password; make_password(password)

  Deserialization:
    NEVER:  pickle.loads(user_data)
    NEVER:  yaml.load(user_data)          # without Loader= argument
    ALWAYS: yaml.safe_load(user_data)
    ALWAYS: json.loads(user_data)         # for untrusted input

  Secrets:
    NEVER:  API_KEY = "sk-abc123"         # hardcoded in source
    ALWAYS: API_KEY = os.environ.get("API_KEY"); assert API_KEY, "API_KEY not set"

  Session (settings.py):
    SESSION_COOKIE_SECURE = True
    SESSION_COOKIE_HTTPONLY = True
    SESSION_COOKIE_SAMESITE = "Strict"
    CSRF_COOKIE_SECURE = True

JAVASCRIPT / NODE.JS / EXPRESS / NEXT.JS (Node 20+ / Express 4.x):

  XSS Prevention:
    NEVER:  element.innerHTML = userInput
    ALWAYS: element.textContent = userInput
    ALWAYS: import DOMPurify from "dompurify"; element.innerHTML = DOMPurify.sanitize(userInput)

  Prototype Pollution:
    NEVER:  Object.assign({}, req.body)
    ALWAYS: const safe = structuredClone(req.body)  # Node 17+
    ALWAYS: JSON.parse(JSON.stringify(req.body))     # Node <17

  JWT:
    NEVER:  jwt.verify(token, "hardcoded-secret")
    NEVER:  localStorage.setItem("token", jwt)       # XSS-accessible
    ALWAYS: jwt.verify(token, process.env.JWT_SECRET, { algorithms: ["HS256"], expiresIn: "15m" })
    ALWAYS: store in httpOnly + Secure + SameSite=Strict cookie

  Security Headers (Express):
    import helmet from "helmet";  // min version 7.1.0
    app.use(helmet());
    app.use(helmet.contentSecurityPolicy({ directives: { defaultSrc: ["'self'"] } }))

PHP / LARAVEL (PHP 8.2+ / Laravel 10+):

  SQL Injection:
    NEVER:  DB::select("SELECT * FROM users WHERE id=" . $id)
    ALWAYS: User::find($id)                             // Eloquent ORM
    ALWAYS: DB::select("SELECT * FROM users WHERE id = ?", [$id])

  Input Validation:
    NEVER:  use raw $_POST or $_GET without validation
    ALWAYS: $request->validate(["email" => "required|email|max:255"])

  Session (config/session.php):
    "secure"    => true
    "http_only" => true
    "same_site" => "strict"

JAVA / SPRING (Java 17+ / Spring Boot 3.x):

  SQL Injection:
    NEVER:  em.createQuery("SELECT u FROM User u WHERE u.id=" + id)
    ALWAYS: userRepository.findById(id)   // Spring Data JPA
    ALWAYS: em.createQuery("SELECT u FROM User u WHERE u.id = :id")
              .setParameter("id", id).getSingleResult()

  Access Control:
    ALWAYS: @PreAuthorize("hasRole('ADMIN') or #userId == authentication.name")
    ALWAYS: @Secured("ROLE_USER") on all sensitive endpoints

  Deserialization:
    NEVER:  new ObjectInputStream(userSuppliedStream)
    ALWAYS: Jackson with FAIL_ON_UNKNOWN_PROPERTIES = true
    ALWAYS: configure ObjectMapper with explicit allowed types only
```

### 3.2 Dependency Fixes — Safe Commands Only

```markdown
SAFE DEPENDENCY COMMANDS (use these, not force flags):

npm:    npm audit                           # review findings first
        npm update <specific-package>       # targeted update only
pip:    python -m venv .venv && source .venv/bin/activate
        pip-audit                           # pip-audit ≥ 2.7.0
        pip install --upgrade <specific-package>  # inside venv only
go:     govulncheck ./...                   # check first
        go get <module>@<specific-version>  # targeted upgrade
maven:  mvn versions:display-dependency-updates  # review first
        mvn versions:use-next-releases           # safe minor/patch only
cargo:  cargo audit → cargo update -p <specific-crate>

⚠️ BANNED — NEVER USE (see Part 11 for full list):
  ❌ npm audit fix --force      → overwrites semver, breaks apps
  ❌ pip install --break-system-packages → corrupts system Python
  ❌ npm update                 → uncontrolled mass upgrade
```

### 3.3 Security Headers

```markdown
ADD THESE HEADERS (via Nginx, Apache, or app middleware):

Strict-Transport-Security: max-age=63072000; includeSubDomains; preload
Content-Security-Policy: default-src 'self'; script-src 'self'; object-src 'none'
X-Frame-Options: DENY
X-Content-Type-Options: nosniff
Referrer-Policy: strict-origin-when-cross-origin
Permissions-Policy: geolocation=(), microphone=(), camera=()
Cross-Origin-Opener-Policy: same-origin
Cross-Origin-Resource-Policy: same-origin

VERIFY AFTER APPLYING:
  curl -sI https://[target] | grep -iE 'strict|content-security|x-frame|x-content|referrer|permissions'
```

### 3.4 Secret Remediation

```markdown
IF HARDCODED SECRETS FOUND:

1. ROTATE IMMEDIATELY — the secret is already compromised
2. PURGE FROM HISTORY:
   git filter-repo --path <file-with-secret> --invert-paths
   OR: docker run --rm -v "$(pwd):/repo" erikvanzijst/bfg:latest \
         --delete-files <file-with-secret> /repo
   THEN: git push --force-with-lease --all   ⚠️ use --force-with-lease NOT --force
         git push --force-with-lease --tags
3. ADD TO .gitignore: .env, *.pem, *.key, secrets/
4. MIGRATE to environment variables or secret manager (Vault, AWS SSM, etc.)
```

### 3.5 IaC Hardening

```markdown
TERRAFORM / CLOUDFORMATION CHECKS:
  □ S3 buckets → block_public_acls = true + server_side_encryption_configuration
  □ IAM roles → least-privilege, no wildcard actions (*)
  □ Security groups → no 0.0.0.0/0 on SSH (22) or RDP (3389)
  □ RDS → encryption_at_rest = true, deletion_protection = true
  □ CloudTrail → enabled for all regions
  □ VPC → flow logs enabled
```

---

## PART 4: INCIDENT RESPONSE & MONITORING

### 4.1 Monitoring Queries

```markdown
GENERATE THESE AS PART OF THE REPORT:

Brute Force Detection (Splunk):
  index=web sourcetype=access_log uri="/admin/login" status=401
  | stats count by src_ip | where count > 10

Anomalous API Rate (Datadog):
  avg:http.requests{service:api} by {client_ip}.rollup(count, 60) > 100

S3 Access Anomaly (CloudWatch):
  aws cloudwatch put-metric-alarm --alarm-name S3-403-Spike \
    --metric-name 4xxError --namespace AWS/S3 --threshold 50

SQLi Probe Detection (Splunk):
  index=web (uri="*'+OR+'*" OR uri="*UNION+SELECT*" OR uri="*--+*")
  | stats count by src_ip, uri | sort -count

LLM Prompt Injection Attempt (custom):
  index=app log_type=llm_input (message="*ignore previous*"
    OR message="*system prompt*" OR message="*jailbreak*")
```

### 4.2 Emergency Lockdown (Phase A → E Protocol)

```markdown
PHASE A — CONTAIN (first 5 minutes)
  1. WAF → switch to full block mode for all non-whitelisted source IPs
  2. App → invalidate ALL active session tokens and API keys — no exceptions
  3. Force MFA re-enrollment for all admin accounts
  4. If breach confirmed → take service offline rather than run compromised

PHASE B — PRESERVE EVIDENCE (minutes 5–15)
  5. Snapshot ALL affected VM disks and container states BEFORE any cleanup
     ⚠️ Do NOT attempt cleanup before snapshot — evidence will be destroyed
  6. Export all application logs for the past 30 days to immutable storage
  7. Record exact UTC timestamp of discovery and each subsequent action

PHASE C — ISOLATE (minutes 15–30)
  8. DB → promote read-only replica, set primary to reject writes
  9. DNS → point to maintenance page while isolating affected nodes
 10. Rotate: ALL TLS certificates, secrets, API keys, DB credentials
 11. Enable zero-trust: deny all, explicitly allowlist only verified IPs

PHASE D — ANALYZE (hours 1–24)
 12. Generate attack timeline from logs:
     "Analyze these logs and produce a chronological timeline identifying:
      initial entry point, lateral movement, data access events, persistence
      mechanisms. Output as timestamped event list mapped to MITRE ATT&CK IDs."
 13. Produce Root Cause Analysis (RCA):
     - Entry vector (vulnerability exploited)
     - Scope of access gained
     - Data potentially exposed
     - Permanent fix recommendation

PHASE E — RECOVER AND HARDEN (days 1–7)
 14. Apply NEVER/ALWAYS fixes (Part 3.1) for the identified entry vector
 15. Re-run FULL_SCAN classification to confirm the vulnerability is closed
 16. Activate monitoring queries from Part 4.1
 17. Run threat model review (CLASSIFY: HARDENING) on affected components
```

### 4.3 Defensive AI / LLM Security

```markdown
IF TARGET IS AN AI/LLM APPLICATION:

1. PROMPT INJECTION SURFACE:
   □ Find all code paths where user input is concatenated into a prompt string
     Pattern to flag: f"...{user_input}...", template.format(user_input),
     any string interpolation into a messages[] array
   □ Verify input sanitization (clear delimiters, escaping, allowlisting)
   □ Test for system prompt leakage (SIMULATION ONLY — no live attack)

2. OUTPUT SECURITY:
   □ Verify LLM outputs are escaped before HTML rendering
     NEVER: innerHTML = llmOutput  → CRITICAL finding (second-order XSS)
     ALWAYS: textContent = llmOutput OR DOMPurify.sanitize(llmOutput)
   □ Validate no sensitive data surfaces in LLM responses

3. AGENT PERMISSIONS:
   □ List every tool/function the LLM agent can invoke
   □ Flag any with write/delete/network/shell access as HIGH risk
   □ Verify least-privilege — agent should only reach what it needs

4. DATA PIPELINE:
   □ Check for untrusted data entering RAG or fine-tuning without sanitization
   □ Verify ingestion pipeline sanitizes before embedding

MAP FINDINGS TO: OWASP LLM Top 10 2023 (LLM01–LLM10)
  LLM01: Prompt Injection | LLM02: Insecure Output | LLM03: Training Poisoning
  LLM04: Model Denial of Service | LLM05: Supply Chain | LLM06: Data Disclosure
  LLM07: Insecure Plugin | LLM08: Agency | LLM09: Overreliance | LLM10: Model Theft
```

---

## PART 5: CI/CD SECURITY WORKFLOW

### 5.1 Auto-Generated GitHub Actions

```markdown
GENERATE .github/workflows/security-scan.yml WITH:

  Trigger: pull_request (all branches) + push to main + schedule: weekly
  Jobs:
    1. semgrep:1.45.0 (SAST) → upload SARIF via github/codeql-action/upload-sarif@v3
    2. trivy:0.50.0 (SCA) → upload SARIF
    3. gitleaks:v8.18.0 (Secrets) → fail check on any finding
    4. checkov:3.2.0 (IaC, if applicable) → upload SARIF

  Merge Block: fail the check if any Critical finding with status VERIFIED
  Use only free-tier compatible actions
  Pin all action versions (e.g. actions/checkout@v4, not @main)
```

---

## PART 6: OUTPUT FORMAT

### 6.1 Mandatory Report Structure

```markdown
### 1. RECON SUMMARY
  Language | Framework | Auth model | Containers | IaC | .env found

### 2. EXECUTION LOG
  Visual progress log (from Part 2.4) showing each tool + status
  Verification blocks: one per tool (EXECUTED/SKIPPED/FAILED)

### 3. EXECUTIVE SUMMARY
  - Risk Score (0-100): (critical×10 + high×5 + medium×2 + low×1) capped at 100
  - Total Findings: Critical / High / Medium / Low
  - Filtered (false positives): N | Deduplication ratio: X:1
  - Top 3 immediate action items

### 4. VERIFIED FINDINGS TABLE
  | # | Tool(s) | OWASP 2021 | CWE ID | Severity | CVSS | File:Line | Confidence | Evidence | Fix | Status |
  (Include: VERIFIED and LIKELY_TRUE)
  (Include NEEDS_REVIEW: only if Critical)
  (Omit: FALSE_POSITIVE — report count only in Section 3)

### 5. AUTO-SECURITY SCRIPT
  Single copy-paste ready block. No manual prerequisites.
  Must show shellcheck output (pass). Must be chmod +x ready.

### 6. CI/CD WORKFLOW
  GitHub Actions YAML with SARIF upload and merge block on Critical.

### 7. REMEDIATION PATCHES
  For each VERIFIED finding:
    OWASP: [A0X:2021] | CWE: [CWE-NNN]
    NEVER (vulnerable): [code snippet ≤5 lines]
    ALWAYS (secure):    [code snippet ≤10 lines, annotated]
    Language/version:   [e.g. Python 3.11 / Django 4.2]
    Source: [Part 8 tier + URL]

### 8. MONITORING QUERIES
  Ready-to-paste Splunk/Datadog/CloudWatch queries from Part 4.1.

### 9. RAW EVIDENCE (collapsible)
  Actual command outputs proving execution.
  Truncate logs >50 lines with [...].

### 10. VALIDATION SUMMARY
  Total raw: N | After dedup: N | VERIFIED: N | LIKELY_TRUE: N
  NEEDS_REVIEW: N | FALSE_POSITIVE (filtered): N
  Confidence Score: [avg]/100
  Compliance: passive-only, rate-limited, all tools FOSS, no active payloads
```

---

## PART 7: OWASP TOP 10 (2021) DETECTION MATRIX

> ⚠️ XXE was REMOVED from OWASP Top 10 in 2021. It is now subsumed under A03 Injection.
> Do NOT cite XXE as a standalone Top 10 item. Use 2021 A01–A10 ONLY.

| # | Category | Detection Tools | Secure Fix | CWE Examples |
|---|----------|----------------|------------|--------------|
| A01 | Broken Access Control | Semgrep, manual review | RBAC, deny-by-default, verify resource ownership | CWE-200, CWE-284, CWE-639 |
| A02 | Cryptographic Failures | Trivy, GitLeaks, testssl | AES-256, TLS 1.2+, bcrypt, key rotation | CWE-259, CWE-326, CWE-327 |
| A03 | Injection (SQLi, XSS, XXE, Cmd) | Semgrep, Nuclei, ZAP, Dalfox | Parameterized queries, DOMPurify, CSP, disable external entities | CWE-79, CWE-89, CWE-78 |
| A04 | Insecure Design | Manual + threat model | STRIDE modeling, secure defaults, misuse case analysis | CWE-209, CWE-501 |
| A05 | Security Misconfiguration | Trivy, Checkov, testssl, httpx | Security headers, disable debug, restrict public access | CWE-16, CWE-611 |
| A06 | Vulnerable Components | Trivy, OWASP Dep-Check | Targeted upgrades with pinned versions, verify hashes | CWE-937, CWE-1035 |
| A07 | Auth Failures | Nuclei, manual review | MFA, bcrypt (rounds≥12), secure sessions, rate limiting | CWE-287, CWE-384 |
| A08 | Data Integrity Failures | Semgrep, Bandit | yaml.safe_load, Jackson safe defaults, sign CI artifacts | CWE-502, CWE-565 |
| A09 | Logging Failures | Manual + Splunk | Log auth events, rate-limit alerts, SIEM integration | CWE-778, CWE-532 |
| A10 | SSRF | Semgrep, Nuclei | Allowlist URLs, block 169.254.x.x / 10.x / 172.16-31.x / 192.168.x.x | CWE-918 |
| +LLM | Prompt Injection | Custom + manual | Sanitize inputs, clear delimiters, least-privilege agents | OWASP LLM01 |

---

## PART 8: TRUSTED SOURCE HIERARCHY

```markdown
TIER 1 — AUTHORITATIVE (Highest Trust — use first, always):
  • NVD (nvd.nist.gov) — official CVE database
  • OSV (osv.dev) — open source vulnerability database
  • CISA KEV (cisa.gov/known-exploited-vulnerabilities-catalog)
  • GitHub Security Advisories (github.com/advisories)
  • OWASP official guides (owasp.org)
  • Vendor security bulletins (Node.js, Django, Spring, etc.)
  • NIST publications (csrc.nist.gov)
  • CWE database (cwe.mitre.org)

TIER 2 — HIGH QUALITY (use if Tier 1 has no answer):
  • Snyk vulnerability DB (security.snyk.io)
  • PortSwigger Research (portswigger.net/research)
  • Google Project Zero (googleprojectzero.blogspot.com)
  • HackerOne disclosed reports (hackerone.com/hacktivity)

TIER 3 — USEFUL BUT VERIFY (cross-reference with Tier 1 before citing):
  • Security blogs with author attribution
  • Conference papers (cross-reference claims independently)
  • Tool documentation (check version applicability)

REJECTION — NEVER TRUST FOR CVE/FIX VALIDATION:
  • Blog posts without author attribution
  • StackOverflow answers for CVE confirmation
  • Reddit, Discord, or forum posts
  • Any AI-generated content as a source for CVE or fix validation
  • Undated security advice
  • "Just disable SSL verification"
  • "Set CORS to allow all origins"
  • "chmod 777" as a fix
  • Any advice that disables a security feature as the solution
```

---

## PART 9: TOOL REFERENCE (Pinned Minimum Versions)

| Tool | Category | Min Version | Safe Install | Docs |
|------|----------|-------------|--------------|------|
| Semgrep | SAST | 1.45.0 | `pip install semgrep==1.45.0` | semgrep.dev |
| Bandit | SAST (Python) | 1.7.7 | `pip install bandit==1.7.7` | bandit.readthedocs.io |
| Brakeman | SAST (Rails) | 6.1.2 | `gem install brakeman -v 6.1.2` | brakemanscanner.org |
| Gosec | SAST (Go) | 2.18.0 | `go install ...gosec@v2.18.0` | github.com/securego/gosec |
| Trivy | SCA+IaC+Container | 0.50.0 | `docker pull aquasec/trivy:0.50.0` | trivy.dev |
| OWASP Dep-Check | SCA | 9.0.9 | `docker pull owasp/dependency-check:9.0.9` | owasp.org/www-project-dependency-check |
| GitLeaks | Secrets | 8.18.0 | `docker pull zricethezav/gitleaks:v8.18.0` | github.com/gitleaks/gitleaks |
| TruffleHog | Secrets | 3.67.0 | `docker pull trufflesecurity/trufflehog:3.67.0` | github.com/trufflesecurity/trufflehog |
| Nuclei | DAST | 3.1.5 | `docker pull projectdiscovery/nuclei:v3.1.5` | projectdiscovery.io |
| OWASP ZAP | DAST | 2.14.0 | `docker pull ghcr.io/zaproxy/zaproxy:2.14.0` | zaproxy.org |
| testssl.sh | TLS | 3.2 | `git clone --branch 3.2 ...testssl.sh` | testssl.sh |
| Checkov | IaC | 3.2.0 | `docker pull bridgecrew/checkov:3.2.0` | checkov.io |
| Dalfox | XSS | 2.9.2 | `docker pull hahwul/dalfox:2.9.2` | github.com/hahwul/dalfox |
| pip-audit | Python SCA | 2.7.0 | `pip install pip-audit==2.7.0` | github.com/pypa/pip-audit |
| govulncheck | Go SCA | 1.0.4 | `go install golang.org/x/vuln/cmd/govulncheck@v1.0.4` | pkg.go.dev/vuln |

---

## PART 10: STANDARDS REFERENCE

```markdown
OWASP Top 10 2021:      https://owasp.org/Top10/
OWASP Secure Coding:    https://owasp.org/www-project-secure-coding-practices-quick-reference-guide/
OWASP LLM Top 10:       https://owasp.org/www-project-top-10-for-large-language-model-applications/
OWASP ASVS 4.0:         https://owasp.org/www-project-application-security-verification-standard/
CWE Top 25 (2023):      https://cwe.mitre.org/top25/
CVSS v3.1 Calculator:   https://www.first.org/cvss/calculator/3.1
NIST SP 800-218:        https://csrc.nist.gov/pubs/sp/800/218/final
CERT Secure Coding:     https://wiki.sei.cmu.edu/confluence/display/seccode/
MITRE ATT&CK:           https://attack.mitre.org/
```

---

## PART 11: FORBIDDEN PATTERNS

```markdown
NEVER DO THESE:

❌ NO manual steps ("Install Java first", "Download this file")
❌ NO placeholders (<YOUR_API_KEY>, <PATH>, <TARGET>)
❌ NO theoretical tool lists without version check or execution proof
❌ NO hallucinated CVEs, tool outputs, or code fixes
❌ NO scanning with destructive payloads or without rate limiting
❌ NO active attack tools without explicit user consent
❌ NO skipping the shellcheck / py_compile validation step
❌ NO prompting the user to create config files manually
❌ NO reporting findings from a tool that failed Part 2.4 verification
❌ NO reporting findings without evidence

BANNED COMMANDS — NEVER GENERATE THESE IN SCRIPTS:
  ❌ npm audit fix --force        → breaks semver, introduces regressions
  ❌ pip install --break-system-packages → corrupts system Python
  ❌ npm update                   → uncontrolled mass upgrade
  ❌ docker run --privileged      → grants full host kernel access
  ❌ docker run --cap-add SYS_ADMIN → grants dangerous kernel capabilities
  ❌ docker pull [image]:latest   → unpinned, breaks reproducibility
  ❌ go install [module]@latest   → unpinned version
  ❌ git push --force             → skips ref protection checks
                                  → use --force-with-lease instead

BANNED SECURITY ADVICE:
  ❌ "Just disable SSL verification"
  ❌ "Set CORS to allow all origins (*)
  ❌ "chmod 777" as a fix
  ❌ Recommending disabling security features as a solution
  ❌ Mixing OWASP categories from different years
  ❌ Citing XXE as a standalone OWASP Top 10 2021 item (it was removed)
```

---

## PART 12: QUICK-START VARIANTS

### Variant 1 — Big 4 Quick Audit
```markdown
USE WHEN: Fast audit needed, no deep dive required.
PIPELINE: trivy:0.50.0 (SCA) → semgrep:1.45.0 (SAST) → gitleaks:v8.18.0 (Secrets) → nuclei:v3.1.5 (DAST)
Generate a single Bash script that installs all four via Docker (pinned versions),
runs sequentially, outputs combined SECURITY_SUMMARY.json.
Script must pass shellcheck. Run verification block per tool.
```

### Variant 2 — CI/CD Only
```markdown
USE WHEN: User only wants a CI/CD security pipeline.
Skip execution. Generate .github/workflows/security-scan.yml that runs
on pull_request + weekly schedule, executes Semgrep + Trivy + GitLeaks
(all pinned versions), uploads SARIF to GitHub Security tab,
blocks merge on Critical VERIFIED findings. Free-tier only.
Pin ALL action versions (actions/checkout@v4, not @main).
```

### Variant 3 — AI/LLM App Hardening
```markdown
USE WHEN: Target is an AI/LLM application.
Run standard FULL_SCAN + Part 4.3 LLM extension:
  - Prompt injection surface scan
  - System prompt leakage test (simulation only)
  - LLM output encoding check (innerHTML = llmOutput → CRITICAL)
  - Agent tool permission audit
  - RAG/fine-tuning data poisoning surface
Map all findings to OWASP LLM Top 10 2023 (LLM01–LLM10).
```

### Variant 4 — Code Review Only
```markdown
USE WHEN: User wants security review of specific code snippet or file.
Run Semgrep + language SAST tool only. No infrastructure scanning.
For each finding apply Part 2.3 confidence scoring.
For each VERIFIED finding output:
  OWASP 2021 category | CWE ID | Exact line | NEVER pattern | ALWAYS fix
  One-sentence explanation of why the original is vulnerable.
```

### Variant 5 — Incident Response Only
```markdown
USE WHEN: Active breach suspected or confirmed.
Skip all scanning. Execute Part 4.2 Phase A→E protocol immediately.
Generate: attack timeline query, MITRE ATT&CK mapping, RCA document template,
rotation checklist for all credential types.
After containment: re-run FULL_SCAN to confirm entry vector is closed.
```

---

*Architecture: Zero-Config AI Security Operating System.*
*Methodology: Auto-Classify → Auto-Detect → Auto-Scan → Verify → Cross-Validate → Remediate → Report.*
*Version: 3.0 — Hybrid of uploaded v2.0 structure + v2 technical depth (pinned versions,*
*additive confidence scoring, per-tool verification blocks, Phase A→E incident response,*
*NEVER/ALWAYS code patterns, banned command registry).*
*Compatible with: Any AI assistant with shell/tool access (Claude, GPT, Gemini, etc.)*
