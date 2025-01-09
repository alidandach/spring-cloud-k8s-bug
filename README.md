# spring-cloud-k8s-bug

## To locally build the docker image, go to pom.xml and set  `false` in `publish` xml tag

```ssh
mvn -Pnative spring-boot:build-image -Dmaven.test.skip=true 
```

## To push to docker registry 

```ssh
mvn -Pnative spring-boot:build-image -Dmaven.test.skip=true -Ddocker.publishRegistry.token=xx
```
***

## use microk8s or k3s to run that docker image where the deployement file of k8s is located in k8s.yaml

### create namespace
```ssh
microk8s kubectl create namespace example
```

### apply the deployment 
```
 microk8s kubectl apply -f k8s.yaml -n example
```

### check the application status
```ssh
kubectl logs <POD> -n example
```

