# golang-bundle

[![Build Status](https://img.shields.io/github/workflow/status/batect/golang-bundle/Pipeline/main)](https://github.com/batect/golang-bundle/actions?query=workflow%3APipeline+branch%3Amain)
[![License](https://img.shields.io/github/license/batect/golang-bundle.svg)](https://opensource.org/licenses/Apache-2.0)

A bundle for [Batect](https://batect.dev) that provides a development container for Golang, with sensible default configuration.

## Usage

### Setup

Add the following to your `batect.yml`:

```yaml
include:
  - type: git
    repo: https://github.com/batect/golang-bundle.git
    ref: XXX # Replace with latest version from https://github.com/batect/golang-bundle/releases
```

### Containers

#### `golang-build-env`

A container (based on the official [Golang images](https://hub.docker.com/_/golang)) with sensible defaults for use with Golang.

It mounts the project directory into the container, enables run as current user mode and configures a cache for dependencies downloaded by Go.

### Example

```
tasks:
  build:
    description: Build the project.
    group: Build tasks
    run:
      container: golang-build-env
      command: go build .

include:
  - type: git
    repo: https://github.com/batect/golang-bundle.git
    ref: XXX # Replace with latest version from https://github.com/batect/golang-bundle/releases
```

The [Golang sample project](https://github.com/batect/batect-sample-golang) also demonstrates how to use this bundle.

## Development

Run `./batect --list-tasks` to see a list of available tasks for this project.
