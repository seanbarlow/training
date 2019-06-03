# Overview

## Naming Conventions

[Microsoft Naming Conventions](https://docs.microsoft.com/en-us/azure/architecture/best-practices/naming-conventions)

### Recommendations

1. Only use lower case
   
| Name            | Format                         |
| --------------- | ------------------------------ |
| Resource Groups | [Application]-[Environment]-rg |
|Web App|[Name]-[Environment]

## Tagging

Recommended Tags

| Tag         | Description                                                                                                                 |
| ----------- | --------------------------------------------------------------------------------------------------------------------------- |
| Environment | Tag used to indicate what environment the resource is for                                                                   |
| Owner       | Owner of the resource. We could use a person or group. Typically this is who should be contacted if someone has a question. |

## Resources and Resource Groups

Everything in Azure is a resource and can be represented in JSON. Resources are organized into Resource Groups.

Resource Groups are just containers for you resources. You can use RBAC to control access to your resource groups.

## Getting around the portal

## Dashboards

