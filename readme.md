# 1. docker
```bash
docker build -t sabana-architecture-microservice .
docker run -dp 800:8080 --name sabana-architecture-microservice sabana-architecture-microservice
```

# 2. reposiotorios
* https://github.com/lara44/sabana.architecture.microservice
* https://github.com/lara44/sabana.architecture.argocd.git

# 3. k8s
```bash
k get endpoints -n microservice-api # Ver los endpoints del service
k describe endpoints -n microservice-api # Ver detalles del servicio:
k get services -n microservice-api
k delete namespace api # Eliminar namespace api (el que no estás usando)
```

# 4. argocd
```bash
# instalar
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml

# consultar password
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo

# abrir tunel
kubectl port-forward svc/argocd-server -n argocd 8080:443 &
https://localhost:8080/
```
# 5. Helm chart
```bash
brew install helm #instalar paquete
helm create microservice-chart #crear plantilla k8s
helm install microservice-service microservice-chart #ejecutar paquete
helm uninstall microservice-service # desinstala el chart actual
```
# saber que imagen está usando
```bash
k describe deployment microservice-service-microservice-chart
```