# Overview

This is a repo to explore Port and how to integrate it with GitHub, PagerDuty, and ArgoCD

## Pager Duty Integration

You can find detailed instructions in [the documentation here.](https://docs.getport.io/guides-and-tutorials/ensure-production-readiness/)

We need to run these helm commands in a K8s cluster. Replace `CLIENT_ID` and `CLIENT_SECRET` with your Port credentials and you can get [them here](https://docs.getport.io/build-your-software-catalog/custom-integration/api/#find-your-port-credentials).

Replace token with your Pagerduty token. To obtain it:

- Hover over your avatar in the top right corner of your Pagerduty app, then click My profile.
- Click the User settings tab and scroll to the bottom.
- Click on Create API User Token and provide a name.
- Copy the new token value.

```bash
helm repo add port-labs https://port-labs.github.io/helm-charts
helm upgrade --install my-pagerduty-integration port-labs/port-ocean \
    --set port.clientId="CLIENT_ID" \   # REPLACE VALUE
    --set port.clientSecret="CLIENT_SECRET"  \   # REPLACE VALUE
    --set initializePortResources=true  \
    --set integration.identifier="my-pagerduty-integration"  \
    --set integration.type="pagerduty"  \
    --set integration.eventListener.type="POLLING"  \
    --set integration.secrets.token="token"  \   # REPLACE VALUE
    --set integration.config.apiUrl="https://api.pagerduty.com"
```