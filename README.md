# Custom Catalog to Deploy CAPI Clusters from DKP Dashboard

```
export NAMESPACE=kommander

kubectl apply -f - <<EOF
apiVersion: source.toolkit.fluxcd.io/v1beta1
kind: GitRepository
metadata:
  name: dkp-capi
  namespace: ${NAMESPACE}
  labels:
    kommander.d2iq.io/gitapps-gitrepository-type: catalog
    kommander.d2iq.io/gitrepository-type: catalog
spec:
  interval: 1m0s
  ref:
    branch: main
  secretRef:
    name: tls-root-ca    
  timeout: 20s
  url: https://github.com/arbhoj/capvcd-custom-catalog-demo
EOF

``` 
