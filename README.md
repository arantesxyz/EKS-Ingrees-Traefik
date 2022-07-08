# EKS-ingress-traefik

## Setup
### Deploy k8s cluster
```sh
cd eks-new-vpc
terraform apply
```

### Get the kubeconfig file using AWS CLI.
```sh
aws eks --profile {profile_name} --region {region} update-kubeconfig --name {cluster name}
```

### Deploy traefik as ingress with a AWS Network Load Balance
```sh
cd traefik
kubectl apply -f .
```

### Deploy cert manager with Helm to create SSL certificates
```bash
helm repo add jetstack https://charts.jetstack.io
helm repo update
helm install cert-manager jetstack/cert-manager --namespace cert-manager --create-namespace --set installCRDs=true
```

## TODO

- [] Make nodes completely private and only accessible via a Load Balancer