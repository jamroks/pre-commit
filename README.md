
# Pre-commit hooks

This repo defines Git pre-commit hooks intended for use with [pre-commit](http://pre-commit.com/). The currently
supported hooks are:

* **terraform-fmt**: Automatically run `terraform fmt` on all Terraform code (`*.tf` files).

## General Usage

In each of your repos, add a file called `.pre-commit-config.yaml` with the following contents:

```yaml
repos:
  - repo: https://github.com/jamroks/pre-commit
    rev: <VERSION> # Get the latest from: https://github.com/jamroks/pre-commit/releases
    hooks:
      - id: terraform-fmt
```

Next, have every developer:

1. Install [pre-commit](http://pre-commit.com/). E.g. `brew install pre-commit`.
1. Run `pre-commit install` in the repo.

That’s it! Now every time you commit a code change (`.tf` file), the hooks in the `hooks:` config will execute.

## Running Against All Files At Once

### Example: Formatting all files

If you'd like to format all of your code at once (rather than one file at a time), you can run:

```bash
pre-commit run terraform-fmt --all-files
```

### Example: Enforcing in CI

If you'd like to enforce all your hooks, you can configure your CI build to fail if the code doesn't pass checks by
adding the following to your build scripts:

```bash
pip install pre-commit
pre-commit install
pre-commit run --all-files
```

## License

This code is released under the Apache 2.0 License. Please see [LICENSE](LICENSE) and [NOTICE](NOTICE) for more details.
