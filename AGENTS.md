## Incremental commits, never stacked changes

- Commit every change as soon as it is verified. Nothing sits uncommitted.
- Never layer new edits on top of uncommitted edits. If a change cannot be
  committed yet, stop and tell the user why — do not keep working.
- One topic per commit. If two topics touch the same file, split the hunks
  into separate commits rather than mixing them.

## One topic at a time

Do not stack unrelated tasks in a single turn. Finish (and commit) the
current task before starting a new one, even when the new request is small.

## Never elide values

Never truncate, shorten, or ellipsis identifiers (CIDs, hashes, addresses,
URLs, peer IDs, commit SHAs) for display. Show the full value and let the UI
wrap it. The user will say explicitly if they ever want a shortened form.

## Never push without an explicit order

`git push` (and any other remote or destructive action) runs only when the
user explicitly says so. Never infer permission from an earlier task or a
standing goal — work stays local until told otherwise.

## Commands in docs always get their own line

Every runnable command shown in UI text, help docs, or README gets its own
line (its own code block). Never append comments or prose to a command
line, and never bury a command inside a sentence.

## Always run tests in the background

This is interactive — never block the session on a test suite. Every test
run (unit, CDP, builds, anything long) goes to a background task; report
results when they arrive. Foreground test chains that hang eat the user's
time and are not acceptable.

## Green means commit

A test run that passes is the commit signal: commit immediately, in the
smallest reviewable units (see "Incremental commits"). The fast gate runs
in the edit loop; the full/slow gate confirms phase completion, less
often. Never let verified work sit uncommitted while starting new work.

## Narrate, and stop means stop

Say what you are doing and why, before and after non-trivial steps — no
silent long-running waits while the user watches. When the user says
STOP, stop acting and explain first; never act through a stop.

## Deadlines are time-boxed

When the user gives a time window, the priority is a working, verified,
committed result by the deadline. Polish, extra hardening, and nice-to-
haves come after the deadline is met — not instead of it.

## The user's terminal drives launches

When the user runs something themselves, do not launch competing
instances of it (ports, shared state, and their attention all collide).
Clear the blockers instead: kill strays, free ports, verify the slate.
Exceptions the user grants (e.g. an away-window with a broken stack) are
recorded where they live, per repo.

## Notes: general vs repo-specific directives

The sections above are GENERAL — they apply to every repo this user
works in. Repo-specific directives (wire formats, ports, toolchains,
per-repo rituals like commit-message trailers, watchkeeping cadences)
live in that repo's own AGENTS.md. When both files speak, the repo file
wins for repo-specific matters; these general orders fill the gaps. If
a directive is invented in a session and the user approves it, write it
into the right file immediately — session memory is not tracking.
