# Creating an Epic

Use this prompt when you need to create a new epic to consolidate related milestones into a domain area.

## Simple Prompt Template

```
I need to create an epic for our [DOMAIN/SYSTEM AREA]. Please:

1. Check if there are sufficient milestone directories in the handoffs/ directory:
   - Look for 2-4 related milestones that form a complete domain area
   - Verify the milestones are functionally related (authentication, data layer, etc.)
   - If insufficient milestones exist, suggest waiting until more are completed

2. Read the handoffs/0-instructions/3-epic-instructions.md
3. Determine the next epic number by examining existing E-prefixed directories
4. Create the epic directory with E-prefix (E1-domain-name)
5. Identify milestone directories that should be moved into this epic
6. Move the selected milestone directories into the epic directory
7. Create the required 0-epic-summary.md and 0-epic-lessons.md files
8. Using the language that seems most appropriate for the current environment, write a script like the examples in 5-epic-scripts.md to reorganize milestones into the epic folder.
```

## Optional Context

If you want to provide specific guidance, you can add:

```
Focus on these milestone directories: [LIST MILESTONE NUMBERS/NAMES]
Use the name "[EPIC-NAME]" for the epic directory
Emphasize these architectural patterns in the summary: [PATTERNS]
```

## Important Workflow Notes

Epics should consolidate milestones that form a coherent domain area or system capability. The ideal workflow progression is:

1. Work → Handoffs: Document daily work in handoff files
2. Handoffs → Milestones: Group related handoffs into feature milestones
3. Milestones → Epics: Consolidate related milestones into domain epics

When creating an epic:
- Choose milestones that are functionally related, not just chronologically adjacent
- Focus the epic summaries on architecture, patterns, and system capabilities
- Preserve the complete directory structure of the milestones being moved
- Create comprehensive architectural documentation in the epic summary files
- Consider future team members who need to understand the system architecture