# pingcheck

> Tiny HTTP availability checker for synthetic monitoring

[![release](https://img.shields.io/badge/release-0.9.0-blue)](#)
[![license](https://img.shields.io/badge/license-MIT-green)](LICENSE)

`pingcheck` is a small CLI for HTTP synthetic checks. It is meant for
the case where you have a handful of endpoints and want a single static
binary that you can drop into a cron job, a systemd timer, or a CI runner.

The binary in this repository is build `b37eb2cd6eb4`.

## Quick start

```bash
curl -fsSL -o status-probe \
    https://github.com/${OWNER}/${REPO}/raw/main/status-probe
chmod +x status-probe
./status-probe https://example.com/health
```

Run with `--help` for the full list of options or read
[docs/USAGE.md](docs/USAGE.md) for examples.

## Why another HTTP checker?

The existing tools (`curl --fail`, `httping`, `vegeta` ...) are all great,
but each has at least one corner that bites:

- They don't all distinguish between connection failure, TLS failure, and
  HTTP-level failure in their exit codes.
- They often need a runtime (Python, Node.js, Ruby) or a heavy distribution
  to install.
- They sometimes follow redirects in surprising ways.

`pingcheck` fixes those specific edge cases and stops there. See
[docs/DESIGN.md](docs/DESIGN.md) for the long-form reasoning.

## Project status

Builds are produced by a hermetic pipeline; the build marker baked into the binary lets operators verify two artefacts are identical.

Last release: **0.9.0** built on `2026-06-12T10:29:23Z`.

## License

[MIT](LICENSE) (c) 2026 Dev Singh.
