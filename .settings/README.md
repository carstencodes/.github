# Repository settings as code

The settings workflows manage every public `carstencodes` repository that is
not a fork or archived. They discover that set at run time. Keep one file at
`.settings/repository/<repository-name>.yaml` for each eligible repository.
The workflows fail with a clear message if a discovered repository does not
have a corresponding file.

`.settings/general.yaml` is the shared baseline. Each run renders it together
with the target repository's file, in that order, so the repository file can
override values from the baseline. A repository file may be empty until it
needs an override.

The baseline currently enables automatic deletion of head branches after
pull-request merges. Review check-mode reports before relying on sync to apply
this or any future settings.

## Workflows and token

Add a fine-grained personal access token as the `ADMIN_TOKEN` Actions secret
in this repository. Grant it Administration: write for every target
repository. The workflows use it to discover the public repository list and
read or apply repository settings; the default `GITHUB_TOKEN` cannot perform
these operations.

- **Synchronize settings** applies the rendered settings when configuration
  or workflow files change on `main`, or when manually dispatched.
- **Check settings** runs weekly and can also be manually dispatched. It
  fails when a target is missing a configuration file, settings drift, or an
  API request fails.

Both workflows render each target's shared and repository-specific files
before applying or checking them. Changes made directly in GitHub can be
reviewed in the weekly check report and corrected by the sync workflow.
