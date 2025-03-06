# Epic Management System

## Purpose

Epics consolidate related milestones when:

- Major Release completed
- System capabilities span several milestones
- Core architectural patterns emerge
- Product capabilities reach maturity

## Core Principles

- **Concise**: Every token counts
- **Factual**: Concrete details, not stories
- **Relevant**: Include essential only
- **Future-Focused**: What next devs need
- **Learning**: Document issues and solutions

## Milestone to Epic

1. **Accumulate Milestones First**:
   - Complete feature implementations as milestones
   - Let 2-4 related milestones accumulate
   - Group milestones by functional domain or system area
   - Identify architectural patterns across milestones

2. **Distill to Milestones**:
   - Extract key info from handoffs
   - Identify patterns across handoffs
   - Consolidate repeated themes
   - Transform details into concise facts
   - Prioritize long-term value info

## Workflow

1. **Development Progression**:
   - Handoffs → capture daily work
   - Milestones → summarize completed features
   - Epics → consolidate system capabilities

2. **Epic Creation**
   -

   - Create epic directory with E-prefix sequential numbering
   - Use
   - Move relevant milestone folders intact
   - Create summary documents focused on architecture
   - Preserve all milestone and handoff content

   - Create milestone directoy with descriptive name
   - Use E-preixed sequential numbers (E1-feature, E2-api, etc.)
   - Distill milestone docs into epic docs
   - Move milestone folders to epic folder
   - Name reflects actual achievement

## Epic Documents

1. **0-epic-summary.md**:
   - Date completed
   - Changes implemented
   - Decisions made and why
   - Discoveries found
   - Current system state

2. **0-epic-lessons-learned.md**:
   - Problems encountered
   - Working solutions
   - Tools/libraries used
   - Edge cases identified
   - Reusable patterns

## Naming Convention

- System files: prefix with "0-" (0-epic-summary.md)
- epic directory: E-prefixed numbers (E1-authentication-system)
- Milestone directories: maintain original numbering within epics

## Writing Style

### 0-epic-summary.md

```
## Changes
- Data connector with batch processing
- Optimized query approach (30x faster)
- Cross-platform path handling

## Decisions
- Validation library update: 40% faster
- Nested env vars for configuration
- Default fallback for missing references

## Discoveries
- Duplicate entities: Item A has IDs 64, 125
- Relationship gaps: 246/252 entities connected
- Missing refs: IDs 53, 54 not in dataset
```

### 0-epic-lessons-learned.md

```
## Config Library Migration

**Problem:** `Cannot import Settings from library`

**Solution:**
- Update dependency version
- Use new config pattern
- Update initialization with correct prefix

## Null Value Handling

**Problem:** `Invalid value in transformation`

**Solution:**
- Create sanitization function
- Replace invalid values with null
- Apply to all values before serialization
```

## Example Organization

Before:

```
handoffs/
├── 1-user-auth/
│   ├── 0-milestone-summary.md
│   ├── 0-milestone-lessons-learned.md
│   ├── 1-login-setup.md
│   └── 2-auth-flow.md
├── 2-permission-system/
│   ├── 0-milestone-summary.md
│   ├── 0-milestone-lessons-learned.md
│   ├── 3-role-definition.md
│   └── 4-permission-checks.md
├── 3-audit-logging/
│   ├── 0-milestone-summary.md
│   ├── 0-milestone-lessons-learned.md
│   ├── 5-event-capture.md
│   └── 6-compliance-reports.md
```

After:

```
handoffs/
├── E1-identity-management/
│   ├── 0-epic-summary.md
│   ├── 0-epic-lessons-learned.md
│   ├── 1-user-auth/
│   │   ├── 0-milestone-summary.md
│   │   └── ...
│   ├── 2-permission-system/
│   │   ├── 0-milestone-summary.md
│   │   └── ...
│   └── 3-audit-logging/
│       ├── 0-milestone-summary.md
│       └── ...
```

handoffs/ (continues to accumulate new handoffs and milestone directories)

handoffs/
├── E1-identity-management/
│   ├── 0-epic-summary.md  # Decisions, discoveries for epic
│   ├── 0-epic-lessons-learned.md  # Patterns, fixes for epic
│   ├── 1-user-auth/
│   │   ├── 0-milestone-summary.md  # Decisions, discoveries for milestone
│   │   └── 0-milestone-milestone-lessons-learned.md  # Patterns, fixes for milestone
