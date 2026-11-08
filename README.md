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
