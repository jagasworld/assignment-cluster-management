We can use commands when deploying from service-a directory (feature1 namespace)

helm install service-a ./helm/service-a --namespace feature1-namespace --set image.tag=n+1
helm install service-b ./helm/service-b --namespace feature1-namespace --set image.tag=n
############################################################################################
Similarly use below commands when deploying from service-b directory (feature2 namespace)

helm install service-a ./helm/service-a --namespace feature2-namespace --set image.tag=n
helm install service-b ./helm/service-b --namespace feature2-namespace --set image.tag=n+1

############################################################################################


1) We can create separate namespaces each of the feature so that it can be isolated environments

2) We can deploy service A (n+1) and service B (n) in feature1-namespace. These two services i.e. service A (n+1) and service B (n) can communicate with each other being in same namespace. A curl command followed by service url should work.

3) We can deploy service A (n) and service B (n+1) in feature2-namespace These two services i.e. service A (n) and service B (n+1) can communicate with each other being in same namespace. A curl command followed by service url should work.

4) Now, to avoid communication between these two namespaces we can apply a network policy using plugin like calico (open source) denying all ingress traffic from other namespace.

5) If we are using helm chart, we can deploy all the resources together. 

6) For deployment, we can install GitOps tool ArgoCD (Open source) so that we can enable continuous deployment in Kubernetes.

