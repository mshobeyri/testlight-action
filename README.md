# Testlight Action

Run Multimeter (`.mmt`) API tests, test suites, and generate documentation in GitHub Actions.

## Usage

```yaml
- uses: actions/checkout@v4
- uses: mshobeyri/testlight-action@v1
  with:
    file: tests/suite.mmt
    env-file: tests/env.mmt
    preset: ci
    report: junit
    report-file: results/junit.xml
```

The `version` input defaults to `latest`. Pass `pre` or `X.Y.Z` to pin `mmt-testlight`.

Docs: [Install Testlight](https://mmt.dev/docs/features/testlight/install) · [Run in CI](https://mmt.dev/docs/tasks/run-in-ci)

## Samples

Runnable `.mmt` files live in [`examples/`](examples/). They hit the public test server at `https://test.mmt.dev` (no secrets).

| File | What it does |
|---|---|
| [`examples/echo_test.mmt`](examples/echo_test.mmt) | POST echo and assert the body |
| [`examples/get_json.mmt`](examples/get_json.mmt) | GET a JSON API |
| [`examples/suite.mmt`](examples/suite.mmt) | Two-test suite |

The **Samples** workflow in this repo runs them with `uses: ./`.

From a checkout of this repo:

```yaml
- uses: actions/checkout@v4
- uses: ./
  with:
    file: examples/suite.mmt
    report: junit
    report-file: results/junit.xml
```
