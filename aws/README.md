## Route53

- Create Kubernetes Secret with AWS Secret Access Key.

```bash
kubectl create secret generic route53-credentials-secret \
--from-literal=secret-access-key=AWS_SECRET_ACCESS_KEY \
--namespace=[CERT-MANAGER-NAMESPACE] > route53-credentials-secret.yaml
```

- And sequentially, the clusterissuer, certificate, and ingress are created.
- The route53 credentials secret is created in cert-manager namespace, and the Clusterissuer does not belong to namespace.

```bash
k apply -f route53-credentials-secret.yaml -n cert-manager
k apply -f clusterissuer.yaml  # No namespace
```

- Finally, create the remaining resources.
- Note that you should create the namespace of the application to be applied.

```bash
k apply -f certificate.yaml -n <application namespace>
k apply -f ingress.yaml -n <application namespace>
```

<br/>

## Reference
- [AWS Route53](https://cert-manager.io/docs/configuration/acme/dns01/route53/)

### [Contact ]
* [Name: nho Luong]
* [Skype](luongutnho_skype)
* [Github](https://github.com/nholuongut/)
* [Linkedin](https://www.linkedin.com/in/nholuong/)
* [Email Address](luongutnho@hotmail.com) 

[![ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/nholuong)

# License
* Nho Luong (c). All Rights Reserved.