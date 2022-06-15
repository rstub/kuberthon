# RStudio Connect

```
$ helm upgrade --install connect rstudio/rstudio-connect \
       -f values.yaml --set license.key=$RSC_LICENSE \
       --set config.LDAP\ \"My\ LDAP\ Server\".BindPassword=$LDAP_ADMIN_PASSWORD
```
