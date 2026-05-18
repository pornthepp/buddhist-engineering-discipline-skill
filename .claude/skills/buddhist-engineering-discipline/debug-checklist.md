# Debug Checklist

Use this file only for code, SQL, API, config, build, report, or runtime errors.

The goal is not to make the symptom disappear.  
The goal is to understand the cause and remove it safely.

---

# 1. Capture the exact symptom

Before fixing, identify:

- Exact error message
- Exact file/module/procedure/package/component involved
- Exact input or request that triggers the issue
- Expected behavior
- Actual behavior
- Recent changes
- Environment differences

For SQL or PL/SQL:
- SQL text or procedure call
- bind values
- table/view/package names
- error stack
- data condition that triggers the issue

For Java/Spring Boot:
- endpoint
- request body/query params
- stack trace
- service/repository involved
- config profile
- database/file/network dependency

For frontend:
- route/page/component
- console error
- network response
- state/input
- template binding or lifecycle step

---

# 2. Trace upstream

Do not patch only where the error appears.

Trace:

```text
input -> validation -> transformation -> business logic -> dependency -> output
```

Ask:

- Where was the bad value introduced?
- Was the input wrong?
- Was validation missing?
- Was data transformed incorrectly?
- Was config/environment different?
- Was a dependency unavailable?
- Was the business rule misunderstood?
- Did stale state or cached data cause this?

---

# 3. Separate symptom from root cause

Examples:

| Symptom | Possible root cause |
|---|---|
| NullPointerException | missing validation, wrong mapping, unexpected DB null, incomplete payload |
| ORA-06550 | invalid PL/SQL call syntax, wrong parameter type, missing grant, package compile error |
| ORA-01403 | data not found because query assumption is wrong |
| 404 API | wrong route, context path, method, proxy, deployment path |
| Jasper resource not found | missing staged resource, wrong repository root, relative path not resolved |
| Slow SQL | wrong join order, missing predicate, bad cardinality, function on indexed column |
| Angular binding error | async state not initialized, wrong property name, template evaluates too early |

---

# 4. Prefer permanent fix

A good fix should:

- Remove or reduce the actual cause
- Preserve business logic
- Avoid hiding errors
- Be easy to test
- Be easy to maintain
- Include validation/logging when useful

Temporary workaround is allowed only when:
- Clearly labeled temporary
- Risk is explained
- Permanent fix is recommended
- It does not corrupt data or hide critical errors

---

# 5. Anti-patterns

Do not:

- Catch exception and ignore it
- Add random null checks without finding why the value is null
- Remove important logic just to make error disappear
- Hardcode production values to pass one test
- Suppress logs that reveal real problems
- Change query logic without preserving business rules
- Claim “fixed” without test evidence or clear uncertainty

---

# 6. Fix explanation format

When explaining a fix, use:

```text
Cause:
- ...

Change:
- ...

Why this works:
- ...

Risk:
- ...

How to test:
- ...
```

For copy-paste code requests, provide complete replaceable code when practical.

---

# 7. PL/SQL-specific checklist

Use for Oracle SQL/PLSQL tasks.

Check:

- Are parameter modes correct? `IN`, `OUT`, `IN OUT`
- Are procedure/function calls syntactically valid?
- Are date conversions explicit and safe?
- Are bind variables used correctly?
- Are joins preserving required business rules?
- Are predicates placed where they preserve outer join logic?
- Are exception handlers hiding useful errors?
- Is `COMMIT` appropriate here, or should caller control transaction?
- Is logging useful but not too noisy?
- Are large CLOB/JSON operations handled safely?
- Is dynamic SQL necessary, and if yes, is it safe?

Avoid:

- `WHEN OTHERS THEN NULL`
- implicit date conversion
- changing outer join behavior accidentally
- adding `DISTINCT` to hide duplicate logic bugs
- using workaround predicates without explaining business impact

---

# 8. Report/Jasper-specific checklist

Use for JasperReports, PDF, SMB, file, template, or resource loading issues.

Check:

- Main `.jasper` or `.jrxml` exists
- `.jrtx` style template exists
- subreports exist
- images/fonts/resources exist
- relative paths resolve from the expected root
- repository root or workspace root is correct
- SMB path parsing is correct
- authentication/share name/domain is correct
- resources are staged locally if Jasper loader cannot fetch from SMB directly
- logs show which file was requested and where it was searched

Common rule:

If Jasper fails with resource not found, do not only patch the failing filename.  
Find how Jasper resolves relative resources and make the resource root/staging strategy consistent.
