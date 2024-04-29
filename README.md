# setup-node-pnpm

A composite Action for setting up Node and PNPM.

## Usage
```yml
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout your repository using git
        uses: actions/checkout@v3

      - name: setup node and pnpm
        uses: dafnik/setup-node-pnpm@v1
        # with:
          # pnpm: 9
          # node: 20
          # node-file: ''
          # cwd: '.'
          # install: false
          # install-ignore-scripts: false
```

| Inputs                   | Default value | Description                                                                                                                                                                                                         |
|--------------------------|---------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `pnpm`                   | `9`           | PNPM version to install                                                                                                                                                                                             |
| `node`                   | `20`          | Version Spec of the version to use in SemVer notation.<br /> It also emits such aliases as lts, latest, nightly and canary builds.<br /> Examples: 12.x, 10.15.1, >=10.15.0, lts/Hydrogen, 16-nightly, latest, node |
| `node-file`              | `''`          | File containing the version Spec of the version to use.<br /> Examples: .nvmrc, .node-version, .tool-versions.<br /> If `node` and `node-file` are both provided the action will use version from `node-file`.      |
| `cwd`                    | `.`           | Changes pnpm-lock.yaml lookup location and the work directory of "pnpm install" if enabled                                                                                                                          |
| `install`                | `false`       | Runs "pnpm install" in working directory                                                                                                                                                                            |
| `install-ignore-scripts` | `false`       | Runs "pnpm install --ignore-scripts" in working directory. Enable "install" or "install-ignore-scripts" only once                                                                                                   |



Furthermore, see [action.yml](action.yml)

## Testing

Local testing is done with [act][act]

Run the test workflow:

```bash
act -j test
```

## Release instructions

In order to release a new version of this action:

1. Locate the semantic version of the [upcoming release][release-list] (a draft is maintained by the [`draft-release` workflow][draft-release]).

2. Publish the draft release from the `main` branch with semantic version as the tag name, _with_ the checkbox to publish to the GitHub Marketplace checked. :ballot_box_with_check:

3. After publishing the release, the [`release` workflow][release] will automatically run to create/update the corresponding the major version tag such as `v0`.

   ⚠️ Environment approval is required. Check the [Release workflow run list][release-workflow-runs].

## License

The scripts and documentation in this project are released under the [MIT License](LICENSE).

<!-- references -->
[act]: https://github.com/nektos/act
[release-list]: https://github.com/dafnik/setup-node-pnpm/releases
[draft-release]: .github/workflows/draft-release.yml
[release]: .github/workflows/release.yml
[release-workflow-runs]: https://github.com/dafnik/setup-node-pnpm/actions/workflows/release.yml
