# Session Restoration Prompt Template

When returning to a project after breaks or context resets, use this prompt to efficiently restore context from epics, milestones, and handoffs.

**For best results, you need to customize this prompt!**

## Template

```
Before we begin, please:

1. Examine the handoffs/ directory structure
2. Check for epic directories (E-prefixed), milestone directories (numbered), and handoff documents

If epic directories (E-prefixed) exist:
   
   A. First review all epic directories in numerical order
      - Read ONLY the 0-prefixed documents in each epic directory (0-epic-summary.md, 0-epic-lessons.md)
      - Skip milestone directories within epics for now
   
   B. Then check if standalone milestone directories exist in the root directory:
      - If yes, read ONLY the 0-prefixed documents in these milestone directories
   
   C. Finally, check if handoff documents exist in the root directory:
      - If yes, read ALL handoff documents in numerical order
      - Pay special attention to the most recent handoff for current state

If NO epic directories exist but milestone directories exist:
   
   A. Review all milestone directories in numerical order
      - Read ONLY the 0-prefixed documents in each milestone directory
      - Skip any numbered documents within milestone directories
   
   B. Then check if handoff documents exist in the root directory:
      - If yes, read ALL handoff documents in numerical order
      - Pay special attention to the most recent handoff for current state

If NO epic directories AND NO milestone directories exist:
   
   - Read ALL handoff documents in the root directory in numerical order
   - Pay special attention to the most recent handoff for current state

After reading, please verify your understanding by:
1. Listing all epic directories in numerical order (if any)
2. Listing all milestone directories in numerical order (if any)
3. Listing all handoff documents you've read (if any)
4. Summarizing the current project state and next steps

This will ensure you have the right context while optimizing token usage.
```

## Project-Specific Customization

Add additional project-specific files to read:

```
Additionally, please read these key project files:
- README.md for project overview
- [specific file paths relevant to your current work]
- [configuration files needed for context]
```

## Advanced Verification

For more comprehensive verification:

```
Please verify your understanding more deeply by:
1. Listing major capabilities across all epics (if any)
2. Listing major features completed across all milestones
3. Identifying recurring patterns or lessons from epic and milestone documents
4. Summarizing the most important open issues from handoff documents
5. Explaining the overall project architecture as you understand it
```

## Session Focus

To guide the session toward specific goals:

```
After restoring context, please focus on:
- [specific feature or component to work on]
- [particular problem that needs solving]
- [next steps in the project roadmap]
```