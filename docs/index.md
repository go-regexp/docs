# go-regexp

Pure-Go regular expressions with lookahead, lookbehind and backreferences — the constructs RE2 forbids.

`go-regexp` is a pure-Go, `CGO_ENABLED=0` regular-expression engine of the Onigmo lineage with a standard-library-`regexp`-shaped API, adding lookahead, lookbehind, backreferences, atomic groups and subexpression calls that RE2 rejects at compile time. It matches on a backtracking VM and falls back to a linear-time lazy-NFA/DFA accelerator for the RE2-compatible subset, bounded by a step/time budget.

## Repositories

<div class="repo-grid" markdown>
<a class="repo-card" href="repos/engine.md"><code>engine</code><br><small>Pure-Go Onigmo-lineage regex engine; stdlib-`regexp`-shaped API with lookaround & backrefs. CGO=0.</small></a>
</div>
