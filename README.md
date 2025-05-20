# GitHub repo template

![build status]

## Structure

- [.github/](.github/) - contains GitHub workflows and repository settings

## Development

See [Contributing Guide](CONTRIBUTING.md) for information about installing development environment
and development workflow.

## Credentials

In order to be able to build the project and resolve all dependencies you need to setup
env variables with credentials:

```bash
export ARTIFACTORY_USER="... your user id"
export ARTIFACTORY_TOKEN="... your access token"
```

To generate an access token:

1. Go to artifactory: <https://artifactory.example.com/ui/repos/tree/General/maven-packages>
2. Press on "Set Me Up" bottom in top right corner
3. Press on "Generate Token & Create Instruction" button
4. Copy generated token

## Build applications

Description of application build process.


<!-- Build status badges -->

[build status]: https://github.com/turboBasic/github-workflow-template/actions/workflows/on-push.yml/badge.svg?branch=main "main branch build status"
