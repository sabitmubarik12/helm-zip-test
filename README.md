# helm-zip-test

Create a token for github in the secrets manager with the name github/credentials/github.com/uneycom
and with keypairs:
{"github_username":"user-name","username":"user@email.com","password":"","github_token":""}




In argocd zip file change in the index.yaml
domain: example.com
alb.ingress.kubernetes.io/load-balancer-name: dev-eks-project-argocd
alb.ingress.kubernetes.io/certificate-arn: arn:aws:acm:eu-west-2:533267093295:certificate/264f18f2-1e0e-4e9a-a1ba-67f579e987ef #change with the actual acm.



In fluentbit configurations change:
        Host          16.162.179.143 #Change to the one required
        Logstash_Prefix eks-project-dev


Use the following URL to call the charts:
https://raw.githubusercontent.com/orgname/repo-name/branch/kubernetes/k8s-charts/private


Helm scanning:
helm lint
helm template fluent-bit
helm template fluent-bit | kube-score score -

Scan Helm charts:
helm template <chart-name> | pluto detect -f -

Scan live Kubernetes resources in a cluster:
pluto detect-live --kubeconfig ~/.kube/config
