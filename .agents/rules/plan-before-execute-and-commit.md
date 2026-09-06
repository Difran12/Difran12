# Rule: Two-Phase Workflow (Separated Plan & Commit Approvals)

## Phase 1: Implementation Plan (Planning & Execution)
1. **Research First**: Inspect code, git history, and requirements without modifying project files prematurely.
2. **Implementation Plan Artifact**: Create `implementation_plan.md` with `RequestFeedback: true` to provide a dedicated **Proceed** button for plan execution.
3. **Execute**: Once approved, perform file edits and verifications (tests, linting, preview).
4. **DO NOT COMMIT YET**: Never execute `git commit` during or immediately following Phase 1.

## Phase 2: Distinct Commit Proposal & Confirmation (Commit & Version Control)
1. **Post-Execution Review**: After changes are verified and `git status` / `git diff` are checked, create a dedicated `commit_proposal.md` artifact.
2. **Mandatory Peringatan / Alert & Interactive Modal**:
   - In `commit_proposal.md`, include a prominent GitHub alert:
     > [!WARNING]
     > **Konfirmasi Commit Git**
     > - **Branch**: `<current-branch>`
     > - **Staged Files**: List of modified/added files
     > - **Untracked / Excluded Files**: Files not included
     > - **Commit Message**: `<type>(<scope>): <clear descriptive message>`
   - Trigger the `ask_question` tool with a clear warning prompt and distinct action buttons:
     - `(Recommended) Ya, lakukan git commit sekarang`
     - `Tinjau kembali / tunda commit`
3. **Execution**: Execute `git add` and `git commit` ONLY after the user explicitly selects the commit option in the interactive modal.
