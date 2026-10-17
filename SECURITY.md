# Security Policy

This project is a hobby project maintained by Carsten Igel in their spare time.
There is no security team, no SLA, and no bug bounty. Reports are genuinely
welcome and will be handled on a best-effort basis.

## Reporting a Vulnerability

Please do not open a public issue, discussion, or pull request for a suspected
vulnerability.

**Preferred:** GitHub private vulnerability reporting —
https://github.com/carstencodes/<REPO>/security/advisories/new

_TODO_
**Fallback** (if that link is unavailable to you): email <you@example.com>
with `[SECURITY]` in the subject. PGP key: <link or fingerprint>.
_END TODO_

## What to include

- Summary of the issue and its impact — what an attacker gains
- Steps to reproduce, or a minimal proof of concept
- Affected version, commit, or container tag
- Relevant configuration, with secrets redacted
- Whether AI tooling helped you find or write this up. Not a problem —
  it just tells me how much verification to do before I act on it.
- Your name or handle, if you'd like credit

Reports without a reproducible proof of concept may be closed without
investigation. That's not hostility, it's arithmetic.

## Supported Versions

Only the latest release and the `main` branch receive security fixes.
Older tags are not maintained. If you self-host, please upgrade before
reporting — several past reports were already fixed.

| Version | Supported |
| ------- | --------- |
| Latest release | ✅ |
| `main` branch | ✅ |
| Older tags, forks, stale deployments | ❌ |

## What counts as a vulnerability

Anything that lets someone who shouldn't have access read, modify, or destroy
data, impersonate a user, execute code, or reach a service they shouldn't.
Concretely: authentication or authorization bypasses, secret exposure,
XSS, CSRF, SSRF, path traversal, injection, unsafe deserialization, and
regular expressions that can be driven into catastrophic backtracking.

## Out of scope

Unless they demonstrate concrete impact:

- Reports against versions already fixed in the latest release
- Missing security headers with no exploitable consequence
- Raw scanner or LLM output with no working proof of concept
- Denial of service that only relies on flooding with traffic
- Vulnerabilities in third-party dependencies with no demonstrated effect here
- Deliberately insecure local setups, e.g. running production over plain HTTP

## What to expect

- Acknowledgement: usually within about 7 days, best effort
- An honest answer: accepted, need more information, or out of scope with a reason
- A fix in a patch release, and a GitHub security advisory where warranted
- Credit in the advisory, unless you'd prefer to stay anonymous

I don't impose a disclosure deadline on you. If you haven't heard anything
after 30 days, please ping me again — and then do whatever you judge
responsible. A heads-up before publishing is appreciated but not demanded.

## Notes for self-hosters

- Serve over HTTPS and keep `HTTPS=true` unless the app is strictly local
- Set a strong, unique session/auth secret
- Leave public signup disabled unless you actually want public signups
- Use provider tokens with the minimum scopes that work
- Treat webhook URLs, SMTP credentials, and API tokens as secrets
- Protect `.env`, data directories, database files, and backups
- Keep the container image and dependencies updated

## Non-security bugs

Ordinary bugs and feature requests belong in the issue tracker. Please don't
route them through the channels above.
