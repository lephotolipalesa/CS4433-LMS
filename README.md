# Moderated LMS 

C++17 + SQLite + OpenSSL offline console LMS. See `docs/BUILD_AND_INSTALL.md` first.

Build (MSYS2 UCRT64):
```bash
cmake -S . -B build -G Ninja
cmake --build build
ctest --test-dir build --output-on-failure
./build/lms.exe
```

The first run creates the initial administrator. Database file: `lms.db`.

**Important:** run and verify on your own MSYS2 machine. The included automated tests cover core business rules and authentication/database integration, but the test report intentionally leaves actual coverage and static-analysis results for measured evidence. Review `docs/TEST_PLAN.md`, `docs/CONFIGURATION_QA.md`, and `docs/DEPLOYMENT.md` before submission.

## HCI and usability update
The console remains C++17 + SQLite + OpenSSL. It now has role-specific information dashboards, record lists before ID selection, context-specific department prompts, field validation, review-before-save confirmations, and post-task choices to repeat, return to dashboard or log out. Navigation commands are `:back`, `:cancel`, `:restart`, `:undo`, `:help` and `:exit`. Their exact safety boundaries and limitations are documented in `docs/HCI_DESIGN_JUSTIFICATION.md`.

The student dashboard displays assignments, deadlines, effective deadlines, submission status and released marks/feedback. Late submissions are accepted; the penalty is 10 percentage points of maximum mark per started late day for days 1–3 and zero after day 3. Resubmission after the effective deadline is rejected. Mark/audit, submission/version, moderation and release updates use SQLite transactions.

See `docs/PHASE_REVIEW_AND_REMAINING_WORK.md` for the remaining gaps against Phases 1–8. Do not treat the review as evidence that uncompleted tasks have passed; the target-machine, hosted CI, static-analysis, coverage and formal usability evidence still need to be produced.
