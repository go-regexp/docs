# engine

Pure-Go Onigmo-lineage regex engine; stdlib-`regexp`-shaped API with lookaround & backrefs. CGO=0.

A regular-expression engine with a public API shaped like the standard library's `regexp` — `Compile`/`MustCompile`, the `Find*`/`FindAll*` family, `ReplaceAll*`, `MatchString`, `SubexpNames` — that additionally supports lookahead, lookbehind, backreferences, atomic groups and `\g<>` subexpression calls. Package `onigmo`.

## Highlights

- **CGO_ENABLED=0**, zero third-party dependencies.
- Lookahead `(?=…)`/`(?!…)`, lookbehind `(?<=…)`/`(?<!…)`, backreferences — none expressible in RE2.
- Standard-library-shaped API: `Compile`/`MustCompile`, `Find*`/`FindAll*`, `ReplaceAll*` (with `$1`/`${name}` expansion), `MatchBounds`, `WithTimeout`.
- Backtracking VM for the full feature set; linear-time lazy-NFA/DFA accelerator for the RE2-compatible subset; step/time budget bounds pathological patterns.
- 100% statement coverage; CI across amd64/arm64 + ppc64le/s390x/riscv64/loong64 (qemu) + wasm.

## Example

```go
re := onigmo.MustCompile(`v\d+\.\d+\.\d+(?=["<])`)
got := re.FindAllString(`a v1.2.3" b v4.5.6< c v9.9.9 d`, -1)
// got == []string{"v1.2.3", "v4.5.6"}   // v9.9.9 excluded by the lookahead
```

## Install

```sh
go get github.com/go-regexp/engine
```

Requires Go 1.26.4 or newer.

## Links

- Source — <https://github.com/go-regexp/engine>
- API reference — <https://pkg.go.dev/github.com/go-regexp/engine>
