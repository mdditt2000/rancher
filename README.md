## Simplifying, Securing, & Scaling your Kubernetes Deployments with F5 & Rancher

Using chart simplifies repeatable, versioned deployment of the F5 Container Ingress Services (CIS). This is the simplest way to install the CIS on Rancher cluster. Helm is a package manager for Kubernetes. Helm is Kubernetes version of yum or apt. Helm deploys something called charts, which you can think of as a packaged application. It is a collection of all your versioned, pre-configured application resources which can be deployed as one unit. This chart creates a Deployment for one Pod containing the k8s-bigip-ctlr, it's supporting RBAC, Service Account and Custom Resources Definition installations. The purpose of this user-guide is demonstrate the simplicity of CIS with Rancher using Helm Charts

### Installing the Chart for the F5 CIS

* Add BIG-IP credentials as K8S secrets

    kubectl create secret generic f5-bigip-ctlr-login -n kube-system --from-literal=username=admin --from-literal=password=f5PME123

* Add the CIS chart repository in Helm using following command:

    helm repo add f5-stable https://f5networks.github.io/charts/stable

* Install the Helm chart using the following command:

    helm install -f cis-k8s-custom-resource-values.yaml f5-bigip-ctlr f5-stable/f5-bigip-ctlr

* cis-k8s-custom-resource-values [repo](https://github.com/mdditt2000/kubernetes-1-19/tree/master/cis%202.6/multi-site/east/cis-deployment)