gcloud compute start-iap-tunnel mgmt-pe-bld-01-cin-euwe1b-openvpn-iap 1194 --local-host-port=localhost:1194 --zone=europe-west1-b --project mgmt-vpn-bld-1733

# test_commands

helm template .\helm-charts\esh-rbac -f helm-overrides\esh-rbac-bld-01-config.yaml
helm template .\helm-charts\esh-event-api -f helm-overrides\esh-event-api-bld-01-config.yaml
helm template .\helm-charts\sbs-esh-event-enricher -f helm-overrides\sbs-esh-event-enricher-bld-01-config.yaml
 
helm -n ns-kcl-sbs-kaf-kafka-operator get all esh-rbac-topics
 
helm upgrade --install --namespace ns-kcl-sbs-kaf-kafka-operator esh-rbac-topics .\helm-charts\esh-rbac -f helm-overrides\esh-rbac-bld-01-config.yaml
 
kubectl  -n ns-kcl-sbs-kaf-kafka-operator describe cfrb dml-esh-al22279-kafka-client-producer-app-0
kubectl  -n ns-kcl-sbs-kaf-kafka-operator describe connector esh-event-sbs-eshmfa-bq-connector
kubectl  -n ns-kcl-sbs-kaf-kafka-operator list connector
 
helm upgrade --install --namespace ns-kcl-sbs-eshmfa-esh-apps kafka-image .\helm-charts\esh-event-enrichment-app -f helm-overrides\esh-event-enrichment-app-bld-01-config.yaml
 
helm template .\helm-charts\esh-con\ -f .\helm-overrides\esh-con-bld-01-config.yaml
helm upgrade --install --namespace ns-kcl-sbs-kaf-kafka-operator esh-con-topics .\helm-charts\esh-con\ -f .\helm-overrides\esh-con-bld-01-config.yaml
gcloud container clusters get-credentials sbs-kaf-bld-01-kcl-01-euwe2 --region europe-west2 --project sbs-kaf-bld-01-6362
 
-n ns-kcl-sbs-kaf-kafka-operator confluent-operator
 
kubectl -n ns-kcl-sbs-kaf-kafka-operator exec -it confluent-operator-7b9c6b9dbf-6hsx7 -- /bin/bash
kubectl -n ns-kcl-sbs-eshmfa-esh-apps exec -it kafka-pod -- /bin/bash
 
gcloud container clusters get-credentials  sbs-kaf-bld-01-kcl-01-euwe2  --region europe-west2 --project sbs-kaf-bld-01-6362
gcloud container clusters get-credentials sbs-eshmfa-bld-01-kcl-01-euwe2 --region europe-west2 --project sbs-eshmfa-bld-01-519b
 
helm upgrade --install --namespace ns-kcl-sbs-kaf-kafka-operator esh-rbac-topics .\helm-charts\esh-rbac -f helm-overrides\esh-rbac-bld-01-config.yaml
 
helm template .\helm-charts\esh-rbac\ -f .\helm-overrides\esh-rbac-bld-01-config.yaml
helm template .\helm-charts\esh-rbac\ -f .\helm-overrides\esh-rbac-int-01-config.yaml
 
helm template .\helm-charts\esh-temp\ -f .\helm-overrides\esh-temp-bld-01-config.yaml
 
