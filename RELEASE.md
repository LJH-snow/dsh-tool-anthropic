# npm release

This repository publishes @libai168/dsh-tool-anthropic through GitHub Actions and npm Trusted Publishing.

## One-time npm setup

In the npm package settings, add a GitHub Actions trusted publisher with:

- owner: LJH-snow
- repository: dsh-tool-anthropic
- workflow file: .github/workflows/publish-npm.yml
- environment: leave blank

Do not add an NPM_TOKEN secret. The workflow uses the GitHub OIDC token with id-token: write.

## Release a version

Run these commands from this repository after updating the source:

```sh
npm version patch
git push origin main --follow-tags
```

Use npm version minor or npm version major when appropriate. The generated vX.Y.Z tag starts the workflow. It checks the tag against package.json, runs typecheck, tests, build, and npm pack --dry-run, then publishes with provenance.

To rerun an existing tag, use the workflow dispatch form and enter the exact tag, for example v0.1.1.
