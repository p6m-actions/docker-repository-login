# Docker Registry Login

![Latest Release](https://img.shields.io/github/v/release/p6m-actions/docker-repository-login?style=flat-square&label=Latest%20Release&color=blue)

## Description

A GitHub Action that simplifies login to Docker container registries. This action wraps the official Docker login action to provide a standardized way to authenticate with container registries in your workflows.

## Usage

```yaml
- name: Login to Docker Registry
  uses: p6m-actions/docker-repository-login@v1
  with:
    registry: your-registry-url # Required
    username: ${{ secrets.REGISTRY_USERNAME }}
    password: ${{ secrets.REGISTRY_TOKEN }}
```

## Inputs

| Input    | Description                          | Required | Default    |
| -------- | ------------------------------------ | -------- | ---------- |
| registry | Container registry URL               | Yes      | N/A        |
| username | Username for registry authentication | Yes      | N/A        |
| password | Password or token for authentication | Yes      | N/A        |

## Examples

### Login to Artifactory Container Registry

```yaml
- name: Login to Artifactory Container Registry
  uses: p6m-actions/docker-repository-login@v1
  with:
    registry: ${{ vars.ARTIFACTORY_HOSTNAME }}
    username: ${{ secrets.ARTIFACTORY_USERNAME }}
    password: ${{ secrets.ARTIFACTORY_IDENTITY_TOKEN }}
```

### Login to Docker Hub

```yaml
- name: Login to Docker Hub
  uses: p6m-actions/docker-repository-login@v1
  with:
    registry: docker.io
    username: ${{ secrets.DOCKERHUB_USERNAME }}
    password: ${{ secrets.DOCKERHUB_TOKEN }}
```

### Login to AWS ECR

```yaml
- name: Login to Amazon ECR
  uses: p6m-actions/docker-repository-login@v1
  with:
    registry: ${{ env.AWS_ACCOUNT_ID }}.dkr.ecr.${{ env.AWS_REGION }}.amazonaws.com
    username: ${{ secrets.AWS_ACCESS_KEY_ID }}
    password: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
```
