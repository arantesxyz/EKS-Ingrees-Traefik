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

### Deploy traefik as ingress with exposed AWS Network Load Balance
```sh
cd traefik
kubectl apply -f .
```

## TODO

- [] Make nodes completely private and only accessible via a Load Balancer