# Kubernetes-Projects

## Deploy airflow with helm

+ Using helm to deploy airflow on a kubernetes cluster
+ Tested on GCP cluster

### Known issues

+ helm upgrade has issues on helm chart version 1.8.0. Use a separate postgresql to avoid this issue
+ Workarounds
   + Continue on the Helm chart version 1.7.0 . 
   + Will need additional modifications to the values.yaml to re-install after making any changes
