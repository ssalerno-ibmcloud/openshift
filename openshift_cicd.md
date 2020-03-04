---

copyright:
  years: 2014, 2020
lastupdated: "2020-02-17"

keywords: openshift, roks, rhoks, rhos

subcollection: openshift

---

{:codeblock: .codeblock}
{:deprecated: .deprecated}
{:download: .download}
{:external: target="_blank" .external}
{:faq: data-hd-content-type='faq'}
{:gif: data-image-type='gif'}
{:help: data-hd-content-type='help'}
{:important: .important}
{:new_window: target="_blank"}
{:note: .note}
{:pre: .pre}
{:preview: .preview}
{:screen: .screen}
{:shortdesc: .shortdesc}
{:support: data-reuse='support'}
{:table: .aria-labeledby="caption"}
{:tip: .tip}
{:troubleshoot: data-hd-content-type='troubleshoot'}
{:tsCauses: .tsCauses}
{:tsResolve: .tsResolve}
{:tsSymptoms: .tsSymptoms}


# Setting up continuous integration and delivery
{: #cicd}

With {{site.data.keyword.cloud_notm}} and other open source tools, you can set up continuous integration and delivery (CI/CD), version control, tool chains, and more to help automate app development and deployment.
{: shortdesc}

Continuous integration (CI) can help you detect errors early, ensure early system integration, and improve collaboration in your development process. Continuous delivery (CD) is a practice by which you build and deploy your software so that it can be released into production at any time. By automating your continuous integration and delivery processes through setting up CI/CD pipelines, you can achieve repeatability in code releases and greater predictability in delivery schedules.

For a deep dive into the benefits and specifics of automating continuous integration and delivery, check out [Automate continuous integration](https://www.ibm.com/garage/method/practices/code/practice_continuous_integration){: external} and [Build and deploy by using continuous delivery](https://www.ibm.com/garage/method/practices/deliver/practice_continuous_delivery){: external} in the IBM Garage Methodology documentation.

## Supported automation tools
{: #cicd_strategy}

To automate your CI/CD pipeline, check out the following supported integrations and tools.
{: shortdesc}

<dl>
<dt>Codeship</dt>
<dd>You can use [Codeship ![External link icon](../icons/launch-glyph.svg "External link icon")](https://codeship.com) for the continuous integration and delivery of containers. For more information, see [Using Codeship Pro To Deploy Workloads to {{site.data.keyword.containerlong_notm}} ![External link icon](../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/cloud/blog/using-codeship-pro-deploy-workloads-ibm-container-service).</dd>
<dt>Grafeas</dt>
<dd>[Grafeas ![External link icon](../icons/launch-glyph.svg "External link icon")](https://grafeas.io) is an open source CI/CD service that provides a common way for how to retrieve, store, and exchange metadata during the software supply chain process. For example, if you integrate Grafeas into your app build process, Grafeas can store information about the initiator of the build request, vulnerability scan results, and quality assurance sign-off so that you can make an informed decision if an app can be deployed to production. You can use this metadata in audits or to prove compliance for your software supply chain.</dd>
<dt>{{site.data.keyword.deliverypipelinelong}}</dt>
<dd>With your app configuration files organized in a source control management system such as Git, you can build your pipeline to test and deploy code to different environments, such as `test` and `prod`. {{site.data.keyword.contdelivery_full}} allows you to automate your app builds and container deployments to Kubernetes clusters by using a toolchain. To get started, see [Setting up a continuous delivery pipeline for a cluster](#continuous-delivery-pipeline). You can also check out [this tutorial on Continuous Deployment to Kubernetes](/docs/tutorials?topic=solution-tutorials-continuous-deployment-to-kubernetes#continuous-deployment-to-kubernetes).</dd>
<dt>Helm</dt>
<dd>[Helm ![External link icon](../icons/launch-glyph.svg "External link icon")](https://helm.sh) is a Kubernetes package manager. You can create new Helm charts or use preexisting Helm charts to define, install, and upgrade complex Kubernetes applications that run in {{site.data.keyword.containerlong_notm}} clusters. For example, you can specify all Kubernetes resources that your app requires in a Helm chart. Then, you can use Helm to create the YAML configuration files and deploy these files in your cluster.For more information, see [Packaging apps in OpenShift 3.11 clusters by using Helm charts](/docs/openshift?topic=openshift-openshift_apps#roks_helm).<p class="tip">In {{site.data.keyword.openshiftshort}} clusters that run version 4.3 or later, use [Operators](/docs/openshift?topic=openshift-operators) instead of Helm charts. If you have custom Helm charts, you can create a [Helm-based Operator ![External link icon](../icons/launch-glyph.svg "External link icon")](https://docs.openshift.com/container-platform/4.2/operators/operator_sdk/osdk-helm.html) instead.</p></dd>
<dt>Kustomize</dt>
<dd>Use the Kubernetes project [Kustomize ![External link icon](../icons/launch-glyph.svg "External link icon")](https://github.com/kubernetes-sigs/kustomize) to package your apps by both standardizing and customizing your deployments across multiple environments. Kustomize helps you write, customize, and reuse your Kubernetes resource YAML configurations. To get started, see [Packaging apps for reuse in multiple environments with Kustomize](/docs/openshift?topic=openshift-openshift_apps#kustomize).<p class="note">Kustomize is not supported for {{site.data.keyword.openshiftshort}} clusters that run version 3.11.</p></dd>
<dt>Operators</dt>
<dd>With operators, you can manage the lifecycle of the apps in your cluster, including third-party software and services that you integrate into your cluster from the [OperatorHub ![External link icon](../icons/launch-glyph.svg "External link icon")](https://operatorhub.io/). You can consistently install, update, and monitor system components by using operators or by making operators available to developers that work in specific projects or across projects. To set up operators, see [Using Operators in 4.3 clusters](/docs/openshift?topic=openshift-operators#operators_4) or [Using Operators in 3.11 clusters](/docs/openshift?topic=openshift-operators#operators_311).</dd>
<dt>Razee</dt>
<dd>[Razee ![External link icon](../icons/launch-glyph.svg "External link icon")](https://razee.io/) is an open-source project that automates and manages the deployment of Kubernetes resources across clusters, environments, and cloud providers, and helps you to visualize deployment information for your resources so that you can monitor the rollout process and find deployment issues more quickly. For more information about Razee and how to set up Razee in your cluster to automate your deployment process, see the [Razee documentation ![External link icon](../icons/launch-glyph.svg "External link icon")](https://github.com/razee-io/Razee).</dd>
</dl>

<br />


## Setting up a continuous delivery pipeline for a cluster
{: #continuous-delivery-pipeline}

Adopt a DevOps approach by using {{site.data.keyword.deliverypipelinelong}}, which includes open toolchains that automate the building and deployment of containerized apps.
{: shortdesc}

Want a more detailed walkthrough? Check out the [Set up a DevOps delivery pipeline for your app](/docs/containers?topic=containers-tutorial-byoc-kube) tutorial. This tutorial shows you how to create a DevOps toolchain in IBM Cloud, integrate it with your GitHub repository and configure delivery pipeline stages that automatically build a container image from your Dockerfile, push it to IBM Cloud Container Registry, and deploy your app to a cluster.
{: tip}

1. From the [cluster dashboard](https://cloud.ibm.com/kubernetes/clusters?platformType=openshift), select the cluster for which you want to set up a continuous delivery pipeline.
2. Select the **DevOps** tab.
3. Click **Create a toolchain**.
4. Review the available toolchains. IBM provides pre-defined toolchains that you can use to deploy, test, and monitor Kubernetes-native apps or Helm charts. You can expand each toolchain to find an overview of the tools that are set up for you and to find the scripts in GitHub that are used to configure the toolchain in your cluster. For more information about each toolchain, see [Toolchain templates](/docs/ContinuousDelivery?topic=ContinuousDelivery-cd_about#templates). If you know what tools you want to use, you can create your own toolchain.
5. Select the toolchain that you want to use and click **Create**.
6. Follow the directions in the console to configure your toolchain. Make sure to include the name of your cluster in your toolchain name so that you can easily find the toolchain that is associated with your cluster later. For more information, see [Creating toolchains](/docs/ContinuousDelivery?topic=ContinuousDelivery-toolchains_getting_started).
7. Select **Delivery Pipeline** to review the stages of your continuous integration and continuous delivery pipeline. After you create your toolchain, your pipeline is automatically kicked off and runs through the stages that you configured. Make sure that your stages run successfully and correct any errors.
8. Modify your toolchain. You can add more tools to your toolchain or change the stages of your delivery pipeline.
   1. From the [cluster dashboard](https://cloud.ibm.com/kubernetes/clusters?platformType=openshift), select the cluster for which you want to set up a continuous delivery pipeline.
   2. Select the **DevOps** tab.
   3. Select the toolchain that you want to modify.

   Having trouble finding the toolchain that you configured for your cluster? If one of the stages in your continuous delivery pipeline fails, the toolchain does not show in the **DevOps** tab of your cluster. Make sure to review errors in your pipeline by selecting your toolchain from the [{{site.data.keyword.contdelivery_short}} dashboard](https://cloud.ibm.com/devops/toolchains) directly.
   {: tip}


