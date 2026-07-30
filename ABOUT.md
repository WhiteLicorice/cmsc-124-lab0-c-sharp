# About this template

This is the C# reference project for CMSC 124 Lab 0. It gives you a known-good file layout when your own setup is stuck, and it gives the instructor a small project for checking the commands printed in the Lab 0 manual.

The program is deliberately simple: `run` accepts one UTF-8 source-file path and copies that file to standard output. A missing or unreadable path produces a diagnostic on standard error and exit code 65.

## Validation record

- Windows version: clean Windows 11 validation pending
- Shell: Git Bash
- Installation route: .NET 8 SDK through WinGet
- Toolchain versions: pending clean-machine validation
- Build: `./build.sh`
- Direct run: `./run tests/lab0/hello.src`
- Harness: `python run_tests.py tests/lab0`
- Ubuntu Actions: pending publication
- Test date: pending
- Known limitations: this is plumbing for Lab 0, not an interpreter implementation
- Manual relationship: the project name replaces the placeholder in the C# section; its SDK resolution, launchers, tests, and workflow follow that section
