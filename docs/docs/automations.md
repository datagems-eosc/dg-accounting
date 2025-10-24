# Automations

A number of automations are available to facilitate the development, quality assurance, security, deployment, maintenance and onboarding of the service. Here we describe some that are directly, publicly available.

## Docker image and publishing

The docker image for the service is managed and generated outside the DataGEMS organization GitHub structure. The service is based on the existing Accounting Service offered by CITE and maintained separately in a [dedicated repository](https://github.com/cite-sa/accounting-service).

Updates and new docker images are generated in that repository and are pushed through the CI system in the DataGEMS Packages to be available for delivery similarly to the other DataGEMS components.

## Documentation

A GitHub Action workflow is available to [generate documentation](https://github.com/datagems-eosc/dg-accounting/blob/main/.github/workflows/deploy-docs-on-demand.yml) available in the project in the format presented here. The action is triggered manually and can be executed against the head of the repository. The documentation generated is versioned and the documentation version is expected as input to the workflow. 

The documentation is build using the [mkdocs](https://www.mkdocs.org/) library and specifically using the [Material for mkdocs](https://squidfunk.github.io/mkdocs-material/) plugin. A number of additional tools are ustilized, such as [mike](https://github.com/jimporter/mike) to support versioning, and others.

The documentation is generated and tagged with the provided version. It is uploaded to a dedicated documentation branch that is configured to be used as the base branch over which the repository GitHub Page presents its contents.