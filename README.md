# EGILExampleOrganisation
LDIF files for populating an LDAP server with example data for EGIL

Meant to be used with the Docker image osixia/openldap.

See https://github.com/osixia/docker-openldap for details, but here's an
example of running with Docker:

```
docker run --env LDAP_ORGANISATION="Kommunen" \
       --env LDAP_DOMAIN="kommunen.se" \
       --env LDAP_ADMIN_PASSWORD="verysecret" \
       --env LDAP_TLS=false \
       --env LDAP_READONLY_USER=true \
       --env LDAP_READONLY_USER_USERNAME=readonly \
       --env LDAP_READONLY_PASSWORD=readonly \
       -p 389:389 \
       --name kommunens-ldap \
       --volume /path/to/repo/ldif:/container/service/slapd/assets/config/bootstrap/ldif/custom \
       --detach \
       osixia/openldap:1.2.4 \
       --copy-service
```

Replace '/path/to/repo' above with wherever you downloaded this repository.
