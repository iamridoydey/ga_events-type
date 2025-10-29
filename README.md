# GitHub Actions Events Example

This repository demonstrates different types of events that can trigger GitHub Actions workflows.

## Overview

This workflow showcases three main triggering events:

1. **Push Events**
  - Triggers on pushes to any branch matching the pattern `fix/*`

2. **Pull Request Events**
  - Triggers when pull requests are:
    - Opened
    - Synchronized (updated)
    - Reopened
  - Only triggers for changes in:
    - Markdown files (`*.md`)
    - Excludes text files (`*.txt`)

3. **Manual Trigger**
  - Can be triggered manually using `workflow_dispatch`

## Workflow Details

The workflow runs on Ubuntu 24.04 and dumps the full event JSON payload, which is useful for debugging and understanding the event context.

### Usage

- Make changes to markdown files in a `fix/*` branch
- Create or update pull requests
- Manually trigger from GitHub Actions tab

### Configuration

```yaml
on:
  push:
   branches: ["fix/*"]
  pull_request:
   types: [opened, synchronize, reopened]
   paths:
    - "*md"
    - "!.txt"
  workflow_dispatch:
```