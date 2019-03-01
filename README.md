# k8s-demo
Ensure Kubernetes is enabled in Docker Desktop

Ensure `kubectl` is installed
```
brew install kubernetes-cli
```

Change your context to your Docker Desktop cluster:
```
kubectl config use-context docker-for-desktop
```

Install the Kubernetes dashboard:
```
kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v1.10.1/src/deploy/recommended/kubernetes-dashboard.yaml
```

Open a proxy to the cluster:
```
kubectl proxy
```

Navigate to the dashboard:
```
http://localhost:8001/api/v1/namespaces/kube-system/services/https:kubernetes-dashboard:/proxy/#!/overview
```

If presented with a sign in screen, run:
```
kubectl describe secret kubernetes-dashboard --namespace=kube-system | grep 'token:' | awk '{print $2}' | pbcopy
```
to copy your token. Paste this into the 'Token' option on the sign in screen.
