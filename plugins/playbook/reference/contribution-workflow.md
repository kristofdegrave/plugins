# Contribution workflow

The chain one work item runs through. `work` runs it; each step is a skill.

## The chain

| Step | Skill | Input | Output | Stop when |
|---|---|---|---|---|
| 0. File | `file-issue` | Work with no work item | A work item with its context label | The item exists |
| 1. Implement | `implement` | A work item | The work, self-checked | The work file ends |
| 2. Test | `work` | The implemented change | The suite's result | Green; red returns to step 1 |
| 3. Review | `review` | An open change request | One posted review | The pass's exit (**Review cap**) |
| 4. Fix | `fix` | Open findings | Every finding answered | Each has a reply; step 3 runs again |
| 5. Clean up | `cleanup` | The human saying it merged | Item done; worktree and branch gone | Epic's open children reported |

## Rule B: run through, then stop

- **`work` enters the chain** at the item's current step and runs on without check-ins.
- **A step skill run by hand runs alone** and stops at its own end.
- **Stops**: a clean pass, the cap, a hold, or a question parked for the human. Each stop reports.
- **Never** starts the next work item, and never reaches step 5 by running on.

## Review cap

- **One pass posts one review.** A clean pass leaves nothing Critical or Major open.
- **The cap** is the profile's `review.cap` passes. The count restarts after an escalation comment or a human comment.
- **At the cap** with Critical or Major open, the chain stops and posts one escalation comment: the open findings, and the human's choice to merge as it stands or grant a round.

| Exit label | When | Means |
|---|---|---|
| `needs-approval` | Clean pass | Mergeable as it stands |
| `needs-approval` + `needs-decision` | The cap | Human decides: merge or grant a round |
| `needs-decision` | Blocking reason found after the exit | On hold until the human decides |
