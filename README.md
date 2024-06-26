# C4builder GitHub Action

Run [C4Builder](https://adrianvlupu.github.io/C4-Builder/) in GitHub Actions to generate a documentation website from Markdown and PlantUML files.

## Fix

This action is using a [version of C4-Build](https://github.com/yciabaud/C4-Builder#7b1444c4a307e63d1f9dc1ee5453bdde5ebc5378) without Zlib.

## Usage

Put the following step in your workflow:

```yml
      - name: C4Builder
        uses: spy7/c4builder-action@v1
```

Workflow example:

```yml
name: Build

on:
  pull_request:
    types: [open, synchronize]
  push:
    branches:
      - master

jobs:
  build:
    name: Build
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v1

      - name: C4Builder
        uses: spy7/c4builder-action@v1
```

## Configuration

The only available configuration is the path where the `.c4builder` file is located.
Defaults to the root of your repository.

You can change it via the `path` input like this:

```yml
jobs:
  build:
    name: Build
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v1

      - name: C4Builder
        uses: spy7/c4builder-action@v1
        with:
          path: 'doc/architecture'
```

All the remaining configuration like source and destination folder is read from your C4Builder configuration file found in the `path`.

## License

Licensed under the MIT license. See [LICENSE](LICENSE).
