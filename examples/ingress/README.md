## Setup NGINX Ingress

To understand how the ingress component ([kubernetes/ingress-nginx](https://github.com/kubernetes/ingress-nginx/)) in Kubernetes works, please finish the following tasks:

**1. Inspect and deploy the mandatory ingress components:**

    ingress-deployment/mandatory.yaml
    ingress-deployment/ingress-svc-lb.yaml


***HINT:*** At katacoda environment we need to use port-forwarding, to test. Open a **second terminal**:
```
kubectl port-forward -n NAMESPACE svc/INGRESS-SERVICE-NAME 80:80
```

Test the access to the default nginx reverse proxy, in the first terminal: `curl localhost:80`

**2. Setup a example web application**

     web-1-deployment-svc.yaml
     web-1-ingress-rule.yaml
     
**3. Test external ingress routing**

Test the deployed web-site with `curl` and the matching host header: `Host: my.test.com`

**4. Change the routing to subpath and verify**

e.g. change to path `my.test.com/web-1` and test the results of the paths `/` and `/web-1`

**5. Deploy a second web application**

     web-2-deployment-svc.yaml
     web-2-ingress-rule.yaml
     
**6. Test routing of second web app** 

Test the deployed web-site with `curl` and the matching host header `Host: my.web-2.com` (see ingress file).

**7. Change routing of web-2**
Change the routing of the second web app to `my.test.com/` and test the new routing:

    my.test.com/web-1 -> echoserver
    my.test.com/ -> demo-www      # hello world!
