# rhacm
Red Hat Advanced Cluster Management 

## Welcome! Let’s get started.
*Red Hat Advanced Cluster Management for Kubernetes provides the tools and capabilities to address various challenges with managing multiple clusters and consoles, distributed business applications, and inconsistent security controls across Kubernetes clusters that are deployed on-premises, or across public clouds.

## End-to-end visibility
*View system alerts, critical application metrics, and overall system health. Search, identify, and resolve issues that are impacting distributed workloads using an operational dashboard designed for Site Reliability Engineers (SREs).

## Application lifecycle
*Define a business application using open standards and deploy the applications using placement policies that are integrated into existing CI/CD pipelines and governance controls.

## Cluster lifecycle
*Create, update, scale, and remove clusters reliably, consistently using an open source programming model that supports and encourages Infrastructure as Code best practices and design principles.

## Governance, Risk, and Compliance
*Use policies to automatically configure and maintain consistency of security controls required by industry or other corporate standards. Prevent unintentional or malicious configuration drift that might expose unwanted and unnecessary threat vectors.

##What are the concepts?
*Learn about some basic concepts to understand the powerful features available in the product.
*In Red Hat Advanced Cluster Management for Kubernetes, the Application model consists of the following Kubernetes custom resources: channels, subscription, placement rules, and applications.

## Channels: (channel.apps.open-cluster-management.io) define the source repositories that a cluster can subscribe to with a subscription, and can be the following types: GitHub repositories, Helm release registries, object stores, and resource template (deployable) namespaces on the hub cluster. Channels require individual namespaces, except GitHub channels, which can share a namespace with another GitHub channel.

## Subscriptions (subscription.apps.open-cluster-management.io) allow clusters to subscribe to a source repository (channel) that can be the following types: GitHub repository, Helm release registry, objectstore, or resource template (deployable) namespace. Subscriptions can be applied locally to the hub or to managed-clusters.

## Placement rules (placementrule.apps.open-cluster-management.io) define the target clusters where subscriptions deploy and maintain the Kubernetes resources. You can use placement rules to help you facilitate the multi-cluster deployment. Placement rules can be shared across subscriptions.

## Applications (application.app.k8s.io) in Red Hat Advanced Cluster Management for Kubernetes are used for grouping Kubernetes resources that make up an application.

##To sum it up, we can define an "Application" in the product as a group: "Channel" + "Subscription" + "Placement Rule."

## Resources:
* https://www.redhat.com/en/technologies/management/advanced-cluster-management
* https://www.openshift.com/blog/understanding-gitops-with-red-hat-advanced-cluster-management
