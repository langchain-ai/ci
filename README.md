# LangChain Shared CI/CD \[WIP\]

This repository contains Github Actions workflows for the LangChain ecosystem.

These workflows are used to automate the testing and deployment of the LangChain ecosystem.

The main components of this repository are:

1. Main Workflows
2. Supporting Workflows
3. Meta Workflows
4. Actions

## Main Workflows

This repository implements 4 "main" workflows that are triggered by `workflow_call` events
from the repositories in the LangChain ecosystem.

1. pull_request.yml
2. push.yml
3. release.yml
4. scheduled.yml

### pull_request.yml: Not Started

This workflow is triggered when a pull request is opened or updated. Its primary purpose
is to run the tests on the code changes in the pull request and notify the developers
of the results.

The jobs in this workflow must pass for a pull request to be merged.

The main steps in this workflow are:

1. Get the changed libraries.
2. Call the `_public_ci.yml` workflow on each changed library (as a matrix)
3. Get the CI summary across all libraries.

### push.yml: Not Started

This workflow is triggered when the main/master branch is updated.

The main steps in this workflow are:

1. Get all the libraries.
2. Call the `_public_ci.yml` workflow on each library (as a matrix)
3. Get the CI summary across all libraries.

### release.yml: Not Started

This workflow is triggered when a new release is requested.

### scheduled.yml: Not Started

This workflow is triggered on a schedule, typically every morning (Pacific Time) at 13:00 UTC.

## Supporting Workflows

This repository implements 2 "supporting" workflows that are used by the main workflows.

1. _public_ci.yml
2. _integration_tests.yml

### _public_ci.yml: Not Started

This workflow is used to run the tests on the code changes in the pull request,
without relying on any secrets.

The main jobs in this workflow are:

1. Get the jobs configs to run for the library.
2. Lint (if applicable)
3. Test (if applicable)
4. Get the CI summary for the library.

Note that the Test step has a matrix that in addition to testing different
versions of Python, also tests different versions of

- `pydantic`
- minimum versions of dependencies (e.g. `langchain-core`, `SQLAlchemy`) if applicable


### _integration_tests.yml: Not Started

This workflow runs integration tests.

## Meta Workflows

This repository implements one "meta" workflow that is used to test the workflows
in this repository against the LangChain ecosystem repositories.

1. _meta_ci.yml: Not Started

## Actions

This repository contains custom actions that are used by the workflows in this repository.

1. poetry_setup: Done
2. get_changed_libs: Not Started
3. get_all_libs: Not Started
4. get_ci_summary: Not Started
