# Example Helm Deployment

## Create cluster
kind create cluster --name simple-go-app

## Deploy app with helm
helm install go-app helm_charts/go-app

## Output
```
➜  simple_k8s_golang_deployment git:(main) ✗ kubectl get all -n simple-go-app 
NAME                                     READY   STATUS    RESTARTS   AGE
pod/go-app-deployment-57f9dc9d88-8ttvf   1/1     Running   0          20m
pod/go-app-deployment-57f9dc9d88-g2xnn   1/1     Running   0          20m
pod/go-app-deployment-57f9dc9d88-p57t6   1/1     Running   0          20m

NAME                                READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/go-app-deployment   3/3     3            3           20m

NAME                                           DESIRED   CURRENT   READY   AGE
replicaset.apps/go-app-deployment-57f9dc9d88   3         3         3       20m
➜  simple_k8s_golang_deployment git:(main) ✗ kubectl exec -i -t go-app-deployment-57f9dc9d88-8ttvf  --container simple-go-app -n simple-go-app  -- /bin/sh
/app # ../go_app
done!
/app # 
```