# CMSC 124 Lab 0 reference template: C#

A finished Lab 0 project in C#, kept as a reference. It's here for two reasons: to give you a known-good file layout when your own setup is stuck, and to give me a small project to check the commands printed in the Lab 0 manual against.

The program is deliberately boring. `run` takes one UTF-8 source-file path and copies that file to standard output. A missing or unreadable path prints a diagnostic on standard error and exits 65. That's enough to exercise argument passing, file reading, stdout, exit codes, the build artifact, the test manifest, and the toolchain, without pretending to be an interpreter.

## Try it

```bash
./build.sh
./run tests/lab0/hello.src
curl -sSL https://raw.githubusercontent.com/WhiteLicorice/cmsc-124-harness/v1.0/run_tests.py -o run_tests.py
python run_tests.py tests/lab0
```

Run those from Git Bash on Windows, not PowerShell. Both scripts are bash.

## What this is not

This isn't a head start on your interpreter, and copying it wholesale won't earn you anything. It's plumbing. Read it when your own `build.sh` or `run` is misbehaving and you want to see a working one.

## Validation record

**Windows, 30 July 2026.** Windows 11 Home, build 26200. Shell: Git Bash. Cloned into a path containing spaces with Git's normal Windows line-ending handling (`core.autocrlf=true`), then run through the full sequence: `./build.sh` twice, `./run tests/lab0/hello.src` compared byte-for-byte against `tests/lab0/hello.expected`, the pinned harness (`python run_tests.py tests/lab0`), generated output deleted and rebuilt from clean, and three failure cases (no argument, missing file, unreadable file) each checked for exit code 65, empty stdout, and a non-empty stderr diagnostic.

Toolchain observed:

```
.NET SDK 10.0.302 (GitHub Actions)
.NET SDK 9.0.301 (Windows host, see the limitation below)
```

**Ubuntu, 30 July 2026.** The committed `.github/workflows/test.yml` runs green on `ubuntu-latest` against `cmsc-124-harness/v1.0`, reporting `1/1 tests passed`. That run resolved SDK 10.0.302 from `global.json` and produced a `net10.0` assembly.

**Installation routes.** The Windows, Linux, and macOS install commands in the manual's C# section were audited against official documentation and live package-manager metadata on 30 July 2026 (`Microsoft.DotNet.SDK.10` resolves to .NET SDK 10.0.302 through WinGet. Ubuntu 24.04 offers `dotnet-sdk-10.0`. `https://dotnet.microsoft.com/download/dotnet/10.0` answers). They were **not** exercised on a freshly imaged machine, so treat them as verified-on-paper rather than verified-end-to-end.

**Known limitation.** The Windows sequence above was run while this project still pinned .NET 8. The project has since moved to the .NET 10 LTS SDK, because .NET 8 leaves support on 10 November 2026, partway through the course. The Windows machine used for validation carries SDKs 8.0.401 and 9.0.301 and cannot satisfy the current `global.json`, so **the .NET 10 pin is currently proven by the Ubuntu workflow only.**

## Relationship to the manual

The `.csproj` filename replaces `YOUR_PROJECT_NAME` in the manual's `run` script. `global.json` matches section 5.4.

## License

MIT. See [LICENSE](LICENSE).
