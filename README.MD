kubectl apply -f 01-ns-and-sa.yaml   // nginx-ingress.yaml
kubectl apply -f 02-ingress.yaml
kubectl create ns cert-manager 
kubectl apply --validate=false -f https://github.com/jetstack/cert-manager/releases/download/v1.0.1/cert-manager.yaml

    #si sale algun error despues del paso anterio entonces:
        kubectl create clusterrolebinding cluster-admin-binding --clusterrole=cluster-admin --user=$(gcloud config get-value core/account)

kubectl apply -f 03-cert-manager.yaml
kubectl apply -f 04-ingress-2.yaml









------------

crear el cluster 
crear carpeta cert-manager
entrar
curl -LO https://github.com/jetstack/cert-manager/releases/download/v1.0.4/cert-manager.yaml
kubectl create ns cert-manager 
kubectl apply --validate=false -f certcert-manager.yaml

kubectl create ns cert-manager-test 
kubectl apply -f issuer.yaml
kubectl apply -f certificate.yaml

// debemos comprobar los certificados 
        kubectl describe certificate -n cert-manager-test

kubectl crate ns ingress-nginx
kubectl -n ingress-nginx apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v0.41.2/deploy/static/provider/cloud/deploy.yaml

//debemos comprobar los svc de nginx-ingress y lo puestos

kubectl -n ingress-nginx --address 0.0.0.0 port-forward svc/ingress-nginx-controller 80
kubectl -n ingress-nginx --address 0.0.0.0 port-forward svc/ingress-nginx-controller 443

kubectl apply -f cert-issuer-nginx-ingress.yaml

        //desplegamos nuestra app

kubectl apply -f certificate-2.yaml
        //podriamos verificar get secrecs
    
kubectl apply -f ingress.yaml
