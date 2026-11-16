# ctxray action

[ctxray](https://github.com/MairwunNx/ctxray) shows what Claude Code, Codex, Cursor, Gemini CLI, and OpenCode load into a model's context, and tests it in CI. This action installs ctxray, caches the harnesses your `ctxray.lock` pins, and runs `ctxray test`:

```yaml
- uses: actions/checkout@v7
- uses: MairwunNx/ctxray-action@v0.1.0
```

| Input | Default | What it does |
| --- | --- | --- |
| `version` | the action's version | The ctxray version, like `0.2.0` |
| `args` | `test` | What to run: `test --layer L1-L3`, `inspect`, `diff --base origin/master` |
| `working-directory` | `.` | The project's folder |
| `cache` | `true` | Cache the harnesses between runs |
| `download-base` | GitHub Releases | Where the releases live, for a mirror |

On a pull request, `ctxray diff` shows what the change adds to the agent's context:

```yaml
- uses: actions/checkout@v7
  with:
    fetch-depth: 0
- uses: MairwunNx/ctxray-action@v0.1.0
  with:
    args: diff --base origin/${{ github.base_ref }}
```

This repository holds the action only. Issues and changes go to [MairwunNx/ctxray](https://github.com/MairwunNx/ctxray), and the [CI Integration](https://github.com/MairwunNx/ctxray/wiki/CI-Integration) page of the manual covers the rest.
