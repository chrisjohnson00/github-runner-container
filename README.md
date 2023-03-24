# github-runner-container
A container that acts as a Github Action Runner

Based off the original work from https://testdriven.io/blog/github-actions-docker/

This has been modified to work with personal accounts, and would not work with a proper organization.  IE: This is intended
to create a repo runner, not an org runner.

## Run locally

```
docker build --tag runner-image .

docker run \
  --detach \
  --env ORGANIZATION=<YOUR-GITHUB-ORGANIZATION> \
  --env ACCESS_TOKEN=<YOUR-GITHUB-ACCESS-TOKEN> \
  --env REPO=<YOUR-GITHUB-REPO \
  --env LABELS=<OPTIONAL-EXTRA-LABELS>
  --env RUNNER_NAME=<OPTIONAL-RUNNER-NAME>
  --name runner \
  runner-image
```