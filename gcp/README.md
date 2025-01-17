## cloud-dns

- Create Kubernetes Secret with GCP ServiceAccount

```bash
kubectl create secret generic clouddns-credentials-secret \
--from-file=key.json=/path/to/SERVICE_ACCOUNT_KEY.json \
--namespace=[CERT-MANAGER-NAMESPACE] > clouddns-credentials-secret.yaml
```

- And sequentially, the clusterissuer, certificate, and ingress are created.
- The clouddns credentials secret is created in cert-manager namespace, and the Clusterissuer does not belong to namespace.

```bash
k apply -f clouddns-credentials-secret.yaml -n cert-manager
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
- [Google CloudDNS](https://cert-manager.io/docs/configuration/acme/dns01/google/)

### [Contact ]
* [Name: nho Luong]
* [Skype](luongutnho_skype)
* [Github](https://github.com/nholuongut/)
* [Linkedin](https://www.linkedin.com/in/nholuong/)
* [Email Address](luongutnho@hotmail.com) 

[![ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/nholuong)

# License
* Nho Luong (c). All Rights Reserved.