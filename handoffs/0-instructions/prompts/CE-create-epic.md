# Creating an Epic

Use this prompt when you need to create a new epic to consolidate related milestones into a domain area.

## Simple Prompt Template

```
I need to create an epic for our [FEATURE/RELEASE]. Please:
(The handoff directory may not be at the project root)
1. Check if there are milestone directories or/and handoff documents in the handoffs/ directory:
   - If handoff documents exist without being in a milestone directory, suggest creating a milestone first before proceeding
   - If no milestone directories exist and no handoff documents exist, suggest creating a handoff first and then a milestone before proceeding
   - If insufficient milestones exist, suggest waiting until more are completed

2. Read the handoffs/0-instructions/3-epic-instructions.md
3. Determine the next sequential epic number by examining existing E-prefixed epic directories
4. Create the epic directory with E-prefix and that number (E1-domain-name)

5. Move all numbered milestone directories from the handoffs/ root into the epic directory
6. Create the required 0-epic-summary.md and 0-epic-lessons-learned.md files
7. Using the language that seems most appropriate for the current environment, write a script like the examples in 5-epic-scripts.md to reorganize milestones into an epic folder.
```

## Optional Context

If you want to provide specific guidance, you can add:

```
Use the following name for the epic directory: [EPIC-NAME]
```

## Important Workflow Notes

An epic should always consolidate recent milestones.
This is the workflow we try to enable:

1. Work on feature/component → Create handoffs during development
2. Complete feature/component → Create final handoff with completion status
3. Consolidate work → Create milestone that includes this final handoff
4. Consolidate features for a realease → Create epic that includes all necessary information from all milestone summaries and milestone lessons learned that are not in an epic yet
