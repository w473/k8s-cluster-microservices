# local minikube cluster setup

# cleanup old stuff

minikube delete
minikube start

# ISTIO installation

istioctl install

# run

kubectl apply -f https://raw.githubusercontent.com/istio/istio/release-1.9/samples/addons/kiali.yaml

kubectl apply -f https://raw.githubusercontent.com/istio/istio/release-1.9/samples/addons/grafana.yaml

kubectl apply -f https://raw.githubusercontent.com/istio/istio/release-1.9/samples/addons/prometheus.yaml

kubectl apply -f https://raw.githubusercontent.com/istio/istio/release-1.9/samples/addons/jaeger.yaml

# for Loadbalancer to work

minikube tunnel

kubectl -n users create secret generic regcred \
 --from-file=.dockerconfigjson='~/.docker/config.json' \
 --type=kubernetes.io/dockerconfigjson
