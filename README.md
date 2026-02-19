# DEPRECATED - Repository Has Moved

This repository has been migrated to GitHub and is no longer accepting changes.

## New Location

<https://github.com/DEFRA/epr-webapps-code-deploy-templates>

Please update your pipeline references to use the new GitHub repository.

## Migration Example

Before (Azure DevOps):

```yaml
resources:
  repositories:
    - repository: CommonTemplates
      name: RWD-CPR-EPR4P-ADO/epr-webapps-code-deploy-templates
      type: git
      ref: main
```

After (GitHub):

```yaml
resources:
  repositories:
    - repository: CommonTemplates
      name: DEFRA/epr-webapps-code-deploy-templates
      type: github
      endpoint: defra
      ref: main
```

e.g. <https://github.com/DEFRA/epr-regulator-service/blob/7ad19cef3cb7ddddd34a124e896847c300e69599/pipelines/ci_pipeline.yaml#L40-L46>

## More info

<https://eaflood.atlassian.net/browse/AMCR-49>
