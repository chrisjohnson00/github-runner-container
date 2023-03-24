# github-runner-container
A container that acts as a Github Action Runner

Based off the original work from https://testdriven.io/blog/github-actions-docker/

## Run locally

```
docker build --tag runner-image .

docker run \
  --detach \
  --env ORGANIZATION=<YOUR-GITHUB-ORGANIZATION> \
  --env ACCESS_TOKEN=<YOUR-GITHUB-ACCESS-TOKEN> \
  --name runner \
  runner-image
```