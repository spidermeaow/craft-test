# craft-test

A small Craft source library for testing package distribution through GitHub.
Version: 1.0.0. Intended runtime: Craft 0.1.10 or later. Runtime tests have not yet been executed for this release.

## Public API

- `greet(name: String): String`: trims surrounding whitespace and returns `Hello, <name>!`; blank names return `Hello, stranger!`.
- `isBlank(value: String): Bool`: true for empty or whitespace-only text.

## Check and test

At the repository root:

```powershell
craft check
craft test
```

Expected: 4 passed, 0 failed. The root is a library and has no main function.

## Local usage (available now)

```powershell
cd examples/hello
craft package check
craft run
```

Expected output: `Hello, Craft!`.

An application can refer to a local checkout in craft.toml:

```toml
[dependencies]
greeting = { path = "../craft-test", version = "1.0.0" }
```

```craft
import greeting "greeting"

func main() {
    print(greeting.greet("Craft"))
}
```

## Planned GitHub usage (Rev.11, not implemented yet)

```powershell
craft install github.com/spidermeaow/craft-test@v1.0.0
```

Git tag v1.0.0 matches the root manifest. This distributes source, not a binary. License terms are in LICENSE. No installation hooks, network access, credentials or external dependencies are needed by the library.
