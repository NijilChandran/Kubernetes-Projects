
kubectl get nodes
kubectl create namespace airflow
kubectl config set-context --current --namespace -namespace=airflow

helm repo add apache-airflow https://airflow.apache.org
helm search repo apache-airflow --versions
helm install airflow apache-airflow/airflow --version 1.7.0 -n airflow --debug
helm list --all-namespaces

kubectl port-forward svc/airflow-webserver 8080:8080 -n airflow

helm show values apache-airflow/airflow > values.yaml

helm uninstall airflow --namespace airflow

helm install airflow apache-airflow/airflow --version 1.7.0 -n airflow \
-f values.yaml \
--debug \
--timeout 10m0s


## updatng current helm release without upgrading to the latest Helm chart version

+ update the values.yaml
helm status <release-name>
helm upgrade --reuse-values <release-name> <chart-name>

# The --reuse-values flag tells Helm to reuse the existing values that are already set in the release and only update the values that have changed in the updated values.yaml file.
