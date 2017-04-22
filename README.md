# statefulset-crunchy-postgresql

This repo contains two Openshift 3.5+ templates for Crunchy PostgreSQL master-replica cluster apps based on this demo: http://info.crunchydata.com/blog/deploying-postgresql-clusters-kubernetes-statefulsets

Setup:

* 1. Install templates

oc project openshift

oc create -f postgresql-statefulset-template.json 

oc create -f postgresql-statefulset-template-dynamic.json 

* 2. Create project

oadm new-project postgresql-cluster --display-name='PostgreSQL Cluster' --description='PostgreSQL Cluster using StatefulSets' --node-selector='region=dev'

oc project postgresql-cluster

oadm policy add-role-to-user edit -z default

* 3. Deploy application

* 3.1 With dynamic persistent storage provisioning (https://docs.openshift.com/container-platform/3.5/install_config/persistent_storage/dynamically_provisioning_pvs.html)

oc new-app postgresql-statefulset-dynamic

* 3.2 Without dynamic persistent storage provisioning

oc new-app postgresql-statefulset

P.S. You might want to change default templates parameters values. 
