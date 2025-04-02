# test-renovate-dev-engines

The `devEngines` is a specification a package.json field to define the runtime and package manager for developing a project
https://github.com/openjs-foundation/package-metadata-interoperability-collab-space/blob/main/devengines-field-proposal.md

This project contains a package.json which has defined yarn@4.8.0 as package manager in devEngines field as follows
```json
{
  "devEngines": {
    "packageManager": {
      "name": "yarn",
      "version": "4.8.0",
      "onFail": "download"
    }
  }
}
```

When a dependency update is requested through Renovate app, it fails with the following error
```console
...
DEBUG: Resolved stable matching version (branch="renovate/express-5.x-lockfile")
{
  "toolName": "yarn"
  "constraint": "^1.22.18"
  "resolvedVersion": "1.22.22"
}
...
DEBUG: packageFiles with updates
{
...
        "extractedConstraints": {
          "yarn": "^4.0.0"
        },
        "lockFiles": [
          "yarn.lock"
        ],
        "managerData": {
          "hasPackageManager": false,
          "yarnLock": "yarn.lock",
          "yarnZeroInstall": false
        },
        "packageFile": "package.json",
...
}
```
