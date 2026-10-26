# epr-webapps-code-deploy-templates

This repository hosts the common templates used in other repositories for EPR - RPD.

## History

This GitHub repository was refreshed from the original https://dev.azure.com/defragovuk/RWD-CPR-EPR4P-ADO/_git/epr-app-config-settings repository after a migration wasn't completely cleanly. See https://github.com/DEFRA/epr-webapps-code-deploy-templates/pull/39.

## Usage

The templates hosted here are not intended to be used on their own, but to be extended by or included in other Azure pipelines. See [Azure documentation](https://learn.microsoft.com/en-us/azure/devops/pipelines/process/templates?view=azure-devops&pivots=templates-includes) for the how-to.

## NuGet package ID check

`epr-build-pipeline.yaml` runs a `CheckNuGetPackageIds` job (see `templates/nuget-package-id-check.yaml`) that fails the build when a NuGet package ID in the repository contains non-ASCII characters. A package such as `AutоFiхture.MSTеst` (with Cyrillic `о`, `х`, `е`) looks identical to the real `AutoFixture.MSTest` in code review and in text search, so it can hide a look-alike package.

Only package IDs are checked (not comments or descriptions) in `*.csproj`, `*.fsproj`, `*.vbproj`, `*.props`, `*.targets`, `packages.config`, `NuGet.Config` package source mappings, `packages.lock.json` and `dotnet-tools.json`. The `Docker` build job depends on it, like the Gitleaks scan.

To report the problem without failing the build (for example while a repository is being cleaned up), set the `failOnNonAsciiPackageId` parameter to `false`. To find offenders locally:

```bash
grep -rn --include='*.csproj' --include='*.props' --include='*.targets' -P '[^\x00-\x7F]' .
```

## Contributing to this project

Please read the [contribution guidelines](/CONTRIBUTING.md) before submitting a pull request.

## Licence

THIS INFORMATION IS LICENSED UNDER THE CONDITIONS OF THE OPEN GOVERNMENT LICENCE found at:

<http://www.nationalarchives.gov.uk/doc/open-government-licence/version/3>

The following attribution statement MUST be cited in your products and applications when using this information.

>Contains public sector information licensed under the Open Government licence v3

### About the licence

The Open Government Licence (OGL) was developed by the Controller of Her Majesty's Stationery Office (HMSO) to enable information providers in the public sector to license the use and re-use of their information under a common open licence.

It is designed to encourage use and re-use of information freely and flexibly, with only a few conditions.
