# RStudio Workbench

## NFS server provisioner

```
$ helm install nfs kvaps/nfs-server-provisioner \
   --set persistence.enabled=true \
   --set persistence.size="15G" \
   --set storageClass.name="nfs-ralf"
```


## Workbench

```
$ helm upgrade --install workbench rstudio/rstudio-workbench \
       -f values.yaml \
       --set license.key=$RSW_LICENSE
```

```
$ helm upgrade --install workbench rstudio/rstudio-workbench \
       -f values.yaml --set license.key=$RSW_LICENSE \
       --set config.userProvisioning.mysssd\\.conf.domain/LDAP.ldap_default_authtok=$LDAP_ADMIN_PASSWORD
```
