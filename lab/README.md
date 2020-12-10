## RHACM GitOPS LAB

## Configure OpenShift client context for cluster admin access

```
oc login -u admin -p XXXX  https://api.YOURCLUSTER1.DOMAIN:6443
oc config rename-context $(oc config current-context) hubcluster

oc login -u admin -p XXXX https://api.YOURCLUSTER2.DOMAIN:6443
oc config rename-context $(oc config current-context) cluster1

```

## Switch to hub

```
oc config use-context hubcluster
oc config current-context && oc whoami
```

## Deploying and Managing a Project with GitOps

```
oc --context cluster1 -n simple-app get deployment

```

### MongoDB on 3 clusters that are used within RHACM
* https://github.com/ansonmez/rhacmgitopslab/blob/master/6.md

### Credit 
* https://github.com/ansonmez/rhacmgitopslab
