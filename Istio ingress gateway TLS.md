# Istio ingress gateway TLS
k -n istio-ingress create secret tls bitbucket-credential --key=server.key --cert=server.crt

```
apiVersion: networking.istio.io/v1alpha3
kind: Gateway
metadata:
  name: bitbucket-gateway
spec:
  # The selector matches the ingress gateway pod labels.
  # If you installed Istio using Helm following the standard documentation, this would be "istio=ingress"
  selector:
    istio: ingress # use istio default controller
  servers:
  - port:
      number: 443
      name: https
      protocol: HTTPS
    tls:
      mode: SIMPLE
      credentialName: bitbucket-credential
    hosts:
    - "bitbucket.xin.test.com"
  - port:
      number: 80
      name: http
      protocol: HTTP
    hosts:
    - "bitbucket.xin.test.com"
```