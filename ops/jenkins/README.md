# Jenkins CI/CD Server

Custom Jenkins container with pre-installed Docker CLI and kubectl for automated CI/CD pipelines and Kubernetes deployments.

## Description

This Jenkins instance is part of the **Operations Management Plane** running alongside Wazuh in a shared Docker Compose stack. It provides:
- Automated builds using Docker
- Direct deployment to K3d cluster via kubectl
- Configuration as Code (JCasC) for reproducible setup
- Pre-installed plugins for Docker and Kubernetes integration

## What's in this directory

### `Dockerfile`
Custom Jenkins image built on `jenkins/jenkins:lts` with additional tools:
- **Docker CLI** - enables building and pushing container images in pipelines
- **kubectl** - allows direct deployment to K3d Kubernetes cluster
- **Docker group membership** - grants Jenkins user access to host Docker socket

### `plugins.txt`
List of pre-installed Jenkins plugins for CI/CD workflows:
- Git, Docker, and Kubernetes integrations
- Configuration as Code (JCasC) support
- Blue Ocean for modern pipeline visualization
- Job DSL for programmatic job creation

### `casc.yaml`
Jenkins Configuration as Code (JCasC) file that:
- Automatically creates admin user from environment variables
- Disables setup wizard for one-click deployment
- Configures security realm and authorization strategy
- Ensures reproducible Jenkins configuration across environments

## Why this setup?

**Docker socket mount** - Jenkins uses Docker-outside-of-Docker (DooD) approach by mounting `/var/run/docker.sock`, avoiding resource overhead of nested Docker daemons while enabling container builds.

**JCasC + environment variables** - Admin credentials are injected from `.env` file, keeping secrets out of version control while maintaining infrastructure-as-code principles.

**Management plane separation** - Jenkins runs outside K3d cluster for stability and to maintain access to CI/CD tools even when experimenting with cluster configurations.
