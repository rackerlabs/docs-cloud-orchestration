# Rackspace Cloud Orchestration API documentation

[![Netlify Status](https://api.netlify.com/api/v1/badges/a92f6061-c2a3-493d-b86d-667981bc7c3d/deploy-status)](https://app.netlify.com/sites/docs-cloud-orchestration/deploys)

This GitHub repository contains the source files that generate the following Rackspace Cloud Orchestration API documentation:

* [Getting Started Guide](https://developer.rackspace.com/docs/cloud-queues/v1/developer-guide/#getting-started/)
* [Developer Guide](https://developer.rackspace.com/docs/cloud-orchestration/v1/developer-guide/)
* [API Reference](https://developer.rackspace.com/docs/cloud-orchestration/v1/developer-guide/#api-reference)

When you commit changes to the master branch of this repository, the
[Strider CI/CD build job](https://build.developer.rackspace.com/rackerlabs/docs-cloud-identity/)
builds the documentation. Successful builds are deployed to production.

## Local Setup

`npm i -g netlify-cli`
`netlify init`
`netlify build`
`netlify dev`
`netlify deploy`

### Support and feedback

We welcome feedback, comments, and bug reports. Follow the
[contributor guidelines](CONTRIBUTING.md)
to propose a source file change, or [submit a GitHub issue](https://github.com/rackerlabs/docs-cloud-identity/issues/new)
to request an update or to provide feedback.

You can also contact the [Rackspace documentation team](mailto:devdoc@rackspace.com) directly for general issues
or questions about the content.
