# Github Runner in a Docker Container
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

## Run in K8s

See `kubernetes/deployment.yaml` as an example.  NOTE: Add any env vars/secrets at this point, or use GH secrets.

## Notes

There is very little installed in the container by default, so if you need to install anything, you'll either want to 
build a new container, with this as its base, or run the `apt` commands in the workflow.

```commandline
- steps:
  - name: install python3
    run: |
      apt-get update && apt-get install -y python3 python3-pip
```
