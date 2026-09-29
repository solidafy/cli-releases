# Solidafy CLI — releases

Published builds of the `solidafy` command-line tool.

This repository holds **no source code**. It exists so the binaries and their
checksums can be downloaded without a GitHub account. The CLI itself is developed
in a private repository.

## Install

**macOS and Linux**

```sh
curl -fsSL https://github.com/solidafy/cli-releases/releases/latest/download/install.sh | sh
```

**Windows (PowerShell)**

```powershell
irm https://github.com/solidafy/cli-releases/releases/latest/download/install.ps1 | iex
```

Then confirm it worked:

```sh
solidafy --version
```

The installer picks the right build for your machine, verifies it against the
published `SHA256SUMS`, and installs nothing if that check fails. It installs under
your home directory and does not need administrator rights or modify your shell
profile — it prints the one line to add yourself.

You need no Node, Bun, npm or Docker. Each build is a single self-contained
executable.

## What is in a release

Every [release](https://github.com/solidafy/cli-releases/releases) contains:

| File                       | Platform             |
| -------------------------- | -------------------- |
| `solidafy-darwin-arm64`    | macOS, Apple Silicon |
| `solidafy-darwin-x64`      | macOS, Intel         |
| `solidafy-linux-x64`       | Linux, x86_64        |
| `solidafy-linux-arm64`     | Linux, arm64         |
| `solidafy-windows-x64.exe` | Windows, x64         |
| `SHA256SUMS`               | checksums for all of the above |
| `install.sh`, `install.ps1` | the installers, matching that release |

## Verifying a download by hand

The installer does this for you, but if you would rather check yourself:

```sh
curl -fsSLO https://github.com/solidafy/cli-releases/releases/latest/download/solidafy-darwin-arm64
curl -fsSLO https://github.com/solidafy/cli-releases/releases/latest/download/SHA256SUMS
shasum -a 256 -c SHA256SUMS --ignore-missing
```

## Installing a specific version

```sh
SOLIDAFY_VERSION=cli-v0.2.0 \
  curl -fsSL https://github.com/solidafy/cli-releases/releases/download/cli-v0.2.0/install.sh | sh
```

`SOLIDAFY_INSTALL_DIR` changes where the binary lands.

## A note for macOS users

Install with the `curl` command above rather than downloading through a browser.
macOS quarantines browser downloads and will refuse to run the binary, often with
no useful message. The install command is not affected. If you already have a
blocked copy:

```sh
xattr -d com.apple.quarantine /path/to/solidafy
```

The binaries are not yet code-signed, which is why the checksum above is worth
checking.

## Updating

Re-run the install command to get the latest CLI. Inside a Solidafy project,
`solidafy update` is a different thing — it refreshes that project's docs, examples
and skills to match the CLI you have installed, and does not upgrade the CLI itself.

## Getting help

Run `solidafy --help`, or `solidafy docs` for the reference guides bundled into the
binary. For anything else, contact your Solidafy representative — issues opened here
are not monitored.
