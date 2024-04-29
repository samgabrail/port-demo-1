

```bash
helm repo add port-labs https://port-labs.github.io/helm-charts
helm upgrade --install my-pagerduty-integration port-labs/port-ocean \
    --set port.clientId="Xisbot4wfbQEjQEUgCn5UZfB5ih9j3Jc" \
    --set port.clientSecret="lJKLJ08CWOPeD1SaFvSIOABzcaxfCDKvdmnw2f0EaksRrcjqVTQzI4Du9km61TTw"  \
    --set initializePortResources=true  \
    --set integration.identifier="my-pagerduty-integration"  \
    --set integration.type="pagerduty"  \
    --set integration.eventListener.type="POLLING"  \
    --set integration.secrets.token="u+ECZ_2nz_Q3SwC1j_1A"  \
    --set integration.config.apiUrl="https://api.pagerduty.com"
```