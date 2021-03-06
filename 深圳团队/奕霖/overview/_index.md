---
title: 产品简介
description: 为您提供Rancher容器平台的产品介绍
---

Rancher是为使用容器的公司打造的容器管理平台。Rancher简化了使用Kubernetes的流程，开发者可以随处运行Kubernetes，满足IT需求规范，赋能DevOps团队。

## 随处运行Kubernetes

Kubernetes 已经成为了容器管理的标准。大多数云服务和虚拟服务的提供商现在将Kubernetes作为标准的基础设施。用户可以使用Rancher Kubernetes Engine（简称RKE），或其他云服务提供商的容器服务，如 GKE、AKS、 EKS等，创建Kubernetes集群。用户也可以将已有集群导入Rancher，集中管理。

## 满足IT需求规范

Rancher支持集中化认证、权限控制、监控和管理所有Kubernetes集群。您可以使用Rancher完成以下操作：

- 使用活动目录（Active Directory）的认证信息访问云端Kubernetes集群，如GKE、AKS、EKS等。
- 设置用户、用户组、项目组、集群、云服务的权限控制策略和安全策略。
- 一站式监控您名下所有集群的健康状态。

## 赋能DevOps开发团队

Rancher提供了一个简单直接的用户界面给DevOps工程师管理他们的应用程序。用户不需要对Kubernetes有深入的了解，即可使用Rancher。

Rancher目录包含了一套内置的DevOps开发工具。Rancher通过了一些云原生的生态系统认证，包括安全工具、监控系统、容器镜像、存储和网络驱动等。

以下的示意图讲述了Rancher在IT管理团队和DevOps开发团队之间扮演的角色。DevOps团队把他们的应用部署在他们选择的云上面，可以是公有云，也可以是私有云。IT管理员负责管理用户、集群、多云之间的权限。

![Platform](/img/rancher/platform.png)

## Rancher API Server的功能

Rancher API Server是基于嵌入式Kubernetes API Server和ETCD数据库建立的，它提供了以下功能：

#### 授权和角色权限控制

- **用户管理：**Rancher API server 除了管理用户在公司内部的使用的认证信息之外，还管理[用户访问外部服务所需的认证信息](/docs/admin-settings/authentication/)，如登录活动目录或GitHub所需的账号密码。  
- **授权：**Rancher API server负责管理[权限控制策略](/docs/admin-settings/rbac/) 和 [安全策略](/docs/admin-settings/pod-security-policies/)。

#### 使用Kubernetes的功能

- **运行Kubernetes集群：** Rancher API server可以在已有节点上运行 [Kubernetes集群](/docs/cluster-provisioning/) ，或对Kubernetes进行[版本升级](/docs/cluster-admin/upgrading-kubernetes)。
- **目录管理：** Rancher可以使用[Helm Chart目录](/docs/catalog/)重复部署应用。
- **项目管理：**项目，是Rancher中的一个概念，Kubernetes中并没有这个概念。项目由一个集群内的多个命名空间和多个访问控制策略组成，允许用户以组为单位，一次管理多个命名空间，对其进行Kubernetes相关操作。Rancher用户界面提供了 [项目管理](/docs/project-admin/)和 [项目内应用管理](/docs/k8s-in-rancher/)两个功能。
- **流水线：**[流水线](/docs/project-admin/pipelines/) 可以帮助开发者快速高效地上线新软件。Rancher支持给每一个项目单独配置流水线。
- **Istio：** [Rancher与Istio集成](/docs/cluster-admin/tools/istio/)，管理员或集群所有者可以将Istio交给开发者，然后开发者使用Istio执行安全策略，排查问题，或为快速发布、灰度发布和A/B测试进行流量控制。

#### 配置云端基础信息

- **同步节点信息：** Rancher API server可以同步集群内所有[节点](/docs/cluster-admin/nodes/)的信息。
- **配置云端基础信息：**当Rancher与云服务提供商配置完了之后，可以在云端动态配置[新节点](/docs/cluster-provisioning/rke-clusters/node-pools/)和[永久存储](/docs/cluster-admin/volumes-and-storage/)。

#### 查看集群信息

- **日志： **Rancher可以跟多种主流日志工具集成，您可以设置 [集群日志](/docs/cluster-admin/tools/logging/) 或[项目日志](/docs/project-admin/tools/logging/)。
- **监控：**使用Rancher，你可以通过Prometheus监控集群节点、Kubernetes组件、软件部署的状态和进度。您可以设置 [集群监控](/docs/cluster-admin/tools/monitoring/) 或[项目监控](/docs/project-admin/tools/monitoring/)。
- **告警信息：**您需要随时知道集群和项目动态，才可以提高公司的运行效率。您可以设置[集群告警](/docs/cluster-admin/tools/alerts/) 或 [项目告警](/docs/project-admin/tools/alerts/)。

## 使用Rancher编辑下游集群

对于已有集群而言，启动集群的方法决定了可编辑的选项和设置。例如，只有通过RKE启动的集群才有可编辑的**集群选项**。使用Rancher创建集群后，集群管理员可以管理集群会员，开启Pod域安全策略，管理节点池，以及进行 [其他操作](/docs/cluster-admin/editing-clusters/)。下表总结了每一种类型的集群和对应的可编辑的选项和设置：

| 可编辑的选项和设置 | RKE 集群 | 云服务集群 | 导入集群 |
| -------------------- | ------------ | ------------------------- | ---------------- |
| 管理用户角色 | ✓            | ✓                         | ✓                |
| 编辑集群选项 | ✓            |                           ||
| 管理节点池 | ✓            |                           ||
