kubectl apply -f 1-ns-and-sa.yaml   // nginx-ingress.yaml
kubectl apply -f  ingress.yaml
kubectl create ns cert-manager 
kubectl apply --validate=false -f https://github.com/jetstack/cert-manager/releases/download/v1.0.1/cert-manager.yaml

    #si sale algun error despues del paso anterio entonces:
        kubectl create clusterrolebinding cluster-admin-binding --clusterrole=cluster-admin --user=$(gcloud config get-value core/account)

kubectl apply -f cert-manager.yaml
kubectl apply -f  ingress-2.yaml
