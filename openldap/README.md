# OpenLDAP server

```
helm repo add helm-openldap https://jp-gouin.github.io/helm-openldap/
helm install openldap helm-openldap/openldap-stack-ha  \
     -f values.yaml \
     --set adminPassword=<password> --set configPassword=<password>
```


Interestingly, the passwords get added automatically to Kubernetes
secrets, making them available in other pods:

```
NAME: openldap
LAST DEPLOYED: Thu Oct 28 18:19:29 2021
NAMESPACE: ralf
STATUS: deployed
REVISION: 1
TEST SUITE: None
NOTES:
** Please be patient while the chart is being deployed **

OpenLDAP-Stack-HA has been installed. You can access the server from within the k8s cluster using:

  openldap.ralf.svc.cluster.local:389

  Or

  openldap.ralf.svc.cluster.local:636


You can access the LDAP adminPassword and configPassword using:

  kubectl get secret --namespace ralf openldap -o jsonpath="{.data.LDAP_ADMIN_PASSWORD}" | base64 --decode; echo
  kubectl get secret --namespace ralf openldap -o jsonpath="{.data.LDAP_CONFIG_PASSWORD}" | base64 --decode; echo


You can access the LDAP service, from within the cluster (or with kubectl port-forward) with a command like (replace password and domain):
  ldapsearch -x -H ldap://openldap.ralf.svc.cluster.local:389 -b dc=example,dc=org -D "cn=admin,dc=example,dc=org" -w $LDAP_ADMIN_PASSWORD

You can access PHPLdapAdmin, using

Test server health using Helm test:
  helm test openldap

Enjoy :)
```
