# iam
***********************************************
apiVersion: v1
data:
  log.level: debug
  registries.conf: |
    registries:
    - name: docker Registry
      api_url: https://index.docker.io
      prefix: index.docker.io
      ping: no
      credentials: pullsecret:argocd/reg-aka-cred
      
***************************      
kind: ConfigMap
metadata:
  labels:
    app.kubernetes.io/name: argocd-image-updater-config
    app.kubernetes.io/part-of: argocd-image-updater
  name: argocd-image-updater-config
  namespace: argocd
  
  cat reg-aka-cred.yaml
apiVersion: v1
data:
  .dockerconfigjson: ewoJImF1dGhzIjogewoJCSJodHRwczovL2luZGV4LmRvY2tlci5pby92MS8iOiB7CgkJCSJhdXRoIjogIllXNXBiR0Z3WVhSdk9sQmhjM04zYjNKa1FERXlNdz09IgoJCX0KCX0KfQ==
kind: Secret
metadata:
  name: reg-aka-cred
  namespace: argocd
type: kubernetes.io/dockerconfigjson
