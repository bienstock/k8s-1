# Nimble Kubernetes applications
### How to expose new service
1. Edit the ingress-prod-rules.yaml
2. Add the new service as "backend"
3. Add reqrite policy "serviceName=new-service rewrite=/"

  * To add new service named "new-service" add the following:
  ```
  ...
    ingress.bluemix.net/rewrite-path: "serviceName=new-service rewrite=/"
  ...

  ...
        - backend:
          serviceName: new-service
          servicePort: 8080
        path: /new-service/
   ...
  
  ```
  
  * Your ingress should be as following:
  
```
apiVersion: extensions/v1beta1
kind: Ingress
metadata:
  annotations:
    ingress.bluemix.net/redirect-to-https: "true"
    ingress.bluemix.net/rewrite-path: "serviceName=new-service rewrite=/;serviceName=new-service-2 rewrite=/"
  name: rules-prod
spec:
  tls:
  - hosts:
    - nimble.uk-south.containers.mybluemix.net
    secretName: nimble-cert
  rules:
  - host: nimble.uk-south.containers.mybluemix.net
    http:
      paths:
        - backend:
          serviceName: new-service
          servicePort: 8080
        path: /new-service/
        - backend:
          serviceName: new-service-2
          servicePort: 8080
        path: /new-service-2/

```
