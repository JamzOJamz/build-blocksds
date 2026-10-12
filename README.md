# Build with BlocksDS

A GitHub Action that builds a Nintendo DS `.nds` ROM using [BlocksDS](https://blocksds.skylyrac.net/) and optionally uploads it as a workflow artifact.

## Usage

```yaml
name: Build

on: [push, pull_request, workflow_dispatch]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v5
      - uses: JamzOJamz/build-blocksds@v1
```

## Inputs

| Input | Description | Default |
| --- | --- | --- |
| `image` | BlocksDS Docker image to build with | `skylyrac/blocksds:slim-latest` |
| `working-directory` | Directory containing the Makefile, relative to the repo root | `.` |
| `make-args` | Extra arguments passed to `make` | `""` |
| `rom-path` | Path or glob of the ROM to upload, relative to `working-directory` | `*.nds` |
| `upload-artifact` | Upload the ROM as a workflow artifact | `true` |
| `artifact-name` | Name of the uploaded artifact | `DS ROM` |

Requires a Linux runner with Docker.

## License

[MIT](LICENSE)
