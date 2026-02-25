---
sidebar_position: 0
---

import useBaseUrl from '@docusaurus/useBaseUrl';

# Dev Pipeline

<div style={{
  backgroundColor: 'white',
  borderRadius: '12px',
  overflow: 'hidden',
  marginBottom: '1rem',
}}>
  <img
    src={useBaseUrl('/img/devPipeline.png')}
    alt="Dev pipeline diagram"
    style={{
      maxWidth: '100%',
      height: 'auto',
      display: 'block',
    }}
  />
</div>

This section covers the development pipeline: how code moves from your machine to production, CI/CD, and related workflows.

Developement usually is done by the `LAN-HTTPS` setup, which means the front end server is taken off docker to allow LIVE updates when coding.

Only repo owners are allowed to make changes to main and test-prod. Developers must make a feature branch to complete their work and must make a pull request.

When pull requests are made, gitlab will automatically start the pipeline which has 4 phases:
- [Linting](../format-linter)
- [Building](../docker)
- [JUnit Testing](../junit) and [E2E Testing](../e2e)
- [Deploying](../blue-green-deployment)

If at any point one of these stages fail, the pipeline will stop, throw errors in the console and send out a notification to the Owner of the PR.
