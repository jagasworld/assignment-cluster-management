We can use commands when deploying from service-a directory (feature1 namespace)
helm install service-a ./helm/service-a --namespace feature1-namespace --set image.tag=n+1
helm install service-b ./helm/service-b --namespace feature1-namespace --set image.tag=n

Similarly use below commands when deploying from service-b directory (feature2 namespace)
helm install service-a ./helm/service-a --namespace feature2-namespace --set image.tag=n
helm install service-b ./helm/service-b --namespace feature2-namespace --set image.tag=n+1
