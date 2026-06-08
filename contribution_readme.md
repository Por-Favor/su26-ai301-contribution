# Contribution #1: Fix silent truncation of INTERVAL second values with >3 decimal digits

**Contribution Number:** 1 \
**Student:** Nyan Lin Thura \
**Issue:** [trinodb/trino#6754 — INTERVAL `x` SECOND values with `x<0.001` are silently truncated to zero](https://github.com/trinodb/trino/issues/6754) \
**Project:** [Trino](https://github.com/trinodb/trino) \
**My Fork:** [In Progress] \
**Status:** 🟡 Phase I — In Progress \
**Last Updated:** June 7, 2026

---

## 📍 Progress (for reviewers)

| Phase | Status | Key artifact |
|---|---|---|
| Phase I — Issue Selection | 🟡 In progress | Issue link above; comment on issue: [after] |
| Phase II — Reproduce & Plan | ⬜ Not started | Reproduction commit: — |
| Phase III — Build & Test | ⬜ Not started | Branch: — |
| Phase IV — Pull Request | ⬜ Not started | PR: — |

### Phase I checklist
- [x] Issue selected from curated list and verified live on GitHub (open, no open PR solving it)
- [x] Prior work researched (prior PR #13426 closed as stale, unmerged)
- [x] Confirmed no one working on the issue
- [x] Comment posted on issue expressing interest
- [ ] Marked issue on course Google Sheet
- [x] Project forked
- [x] Check-in form submitted ("Phase I Complete")

### Progress log
| Date | Update |
|---|---|
| 2026-06-07 | Selected issue #6754. Verified status: issue open; |

---

## Why I Chose This Issue

I'm an applied math major with a data science background. The bug is a **numeric-precision problem**: `INTERVAL '.0001' SECOND` silently becomes zero because Trino's interval type only carries millisecond precision, so sub-millisecond literals are truncated without warning which would produce wrong query results in a SQL engine used heavily for financial and analytical workloads that would otherwise unnoticed. Reasoning about decimal precision, truncation, and correct failure behavior is something I could work with from numerical computing; the new skill I'm building is contributing to a large production Java codebase.

**Problem summary (2–4 sentences):** Trino's `INTERVAL ... SECOND` literals accept more than 3 fractional-second digits but silently truncate them to millisecond precision, so `SELECT val + INTERVAL '.0001' SECOND` returns `val` unchanged. Maintainers agreed the engine should instead raise an error when a literal exceeds the supported precision. My contribution is to implement that validation (in `io.trino.util.DateTimeUtils`'s period-formatter construction).

---

## Understanding the Issue

### Problem Description

[In your own words, what's broken or missing?]

### Expected Behavior

[What should happen?]

### Current Behavior

[What actually happens?]

### Affected Components

[Which parts of the codebase are involved?]

---

## Reproduction Process

### Environment Setup

[Notes on setting up your local development environment - challenges you faced, how you solved them]

### Steps to Reproduce

1. [Step 1]
2. [Step 2]
3. [Observed result]

### Reproduction Evidence

- **Commit showing reproduction:** [Link to commit in your fork]
- **Screenshots/logs:** [If applicable]
- **My findings:** [What you discovered during reproduction]

---

## Solution Approach

### Analysis

[Your analysis of the root cause - what's causing the issue?]

### Proposed Solution

[High-level description of your fix approach]

### Implementation Plan

Using UMPIRE framework (adapted):

**Understand:** [Restate the problem]

**Match:** [What similar patterns/solutions exist in the codebase?]

**Plan:** [Step-by-step implementation plan]
1. [Modify file X to do Y]
2. [Add function Z]
3. [Update tests]

**Implement:** [Link to your branch/commits as you work]

**Review:** [Self-review checklist - does it follow the project's contribution guidelines?]

**Evaluate:** [How will you verify it works?]

---

## Testing Strategy

### Unit Tests

- [ ] Test case 1: [Description]
- [ ] Test case 2: [Description]
- [ ] Test case 3: [Description]

### Integration Tests

- [ ] Integration scenario 1
- [ ] Integration scenario 2

### Manual Testing

[What you tested manually and results]

---

## Implementation Notes

### Week [X] Progress

[What you built this week, challenges faced, decisions made]

### Week [Y] Progress

[Continue documenting as you work]

### Code Changes

- **Files modified:** [List]
- **Key commits:** [Links to important commits]
- **Approach decisions:** [Why you chose certain approaches]

---

## Pull Request

**PR Link:** [GitHub PR URL when submitted]

**PR Description:** [Draft or final PR description - much of the content above can be adapted]

**Maintainer Feedback:**
- [Date]: [Summary of feedback received]
- [Date]: [How you addressed it]

**Status:** [Awaiting review / Iterating / Approved / Merged]

---

## Learnings & Reflections

### Technical Skills Gained

[What you learned technically]

### Challenges Overcome

[What was hard and how you solved it]

### What I'd Do Differently Next Time

[Reflection on your process]

---

## Resources Used

- [Link to helpful documentation]
- [Tutorial or Stack Overflow post that helped]
- [GitHub issues or discussions that helped]
