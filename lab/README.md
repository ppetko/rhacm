## RHACM GitOPS LAB

## Configure OpenShift client context for cluster admin access

```
$ oc login -u admin -p XXXX  https://api.YOURCLUSTER1.DOMAIN:6443
$ oc config rename-context $(oc config current-context) hubcluster

$ oc login -u admin -p XXXX https://api.YOURCLUSTER2.DOMAIN:6443
$ oc config rename-context $(oc config current-context) cluster1

```

## Switch to hub

```
$ oc config use-context hubcluster
$ oc config current-context && oc whoami
```

## Deploying and Managing a Project with GitOps

```
$ oc config use-context hubcluster
Switched to context "hubcluster".
```

## Check deployments on cluster1
```
$ oc --context cluster1 -n simple-app get deployment
No resources found.
```

## Deploy the app 
```
$ oc create -f all.yaml 
namespace/simple-app created
channel.apps.open-cluster-management.io/federation created
application.app.k8s.io/httpd created
placementrule.apps.open-cluster-management.io/cluster1only created
subscription.apps.open-cluster-management.io/httpd created
```

### Check the deployment on cluster1
```
$ oc --context cluster1 -n simple-app get deployments,services,pods
 NAME                    READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/httpd   1/1     1            1           3m36s

NAME            TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)    AGE
service/httpd   ClusterIP   172.30.70.216   <none>        8080/TCP   3m36s

NAME                         READY   STATUS    RESTARTS   AGE
pod/httpd-54b9dfb679-ttkl7   1/1     Running   0          3m36s
```

### Create route

```
oc --context=cluster1 -n simple-app expose service httpd

```

```
# Expose the route for the httpd service
oc --context=cluster1 -n simple-app expose service httpd
# Get the Route hostname
url="http://$(oc --context=cluster1 -n simple-app get route httpd -o jsonpath='{.spec.host}')"
# We will wait 5 seconds to allow for proper propagation
sleep 5
# Access the route
curl -s $url | grep "This page"
```

### State Recovery
```
# Use the `oc` command to delete the httpd deployment object
oc --context cluster1 -n simple-app delete deployment httpd
```

### MongoDB on 3 clusters that are used within RHACM
* https://github.com/ansonmez/rhacmgitopslab/blob/master/6.md

### Credit 
* https://github.com/ansonmez/rhacmgitopslab
