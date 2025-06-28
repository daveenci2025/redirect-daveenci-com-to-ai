# Redirect: daveenci.com to daveenci.ai

This repository contains the configuration for a simple Render Static Site whose sole purpose is to permanently redirect all traffic from `daveenci.com` to `https://daveenci.ai`.

## Purpose

The primary domain for my web presence has been moved to `daveenci.ai`. To ensure a seamless user experience and maintain SEO value, all requests to the old `daveenci.com` domain must be permanently redirected (301) to the new domain.

This repository serves as a dedicated, code-free "redirector" service to handle this task.

## How It Works

This is achieved using a single `render.yaml` configuration file within a Render Static Site. There is no website code (HTML, CSS, JS) in this repository.

The `render.yaml` file instructs Render to:
1. Create a static site service.
2. Apply a global redirect rule to all incoming traffic.

### `render.yaml` Configuration

```yaml
# This file tells Render to act as a permanent redirector
# for any traffic it receives.

services:
  - type: static
    name: redirect-service
    # This section adds the redirect rule
    redirects:
      - source: "/*"
        destination: "https://daveenci.ai/:splat"
        statusCode: 301
