# first play

## installation Kyma

Follow [kyma instllation](https://kyma-project.io/docs/#installation-installation) to install the kyma. For this article, just use [kyma installation on cluster](https://kyma-project.io/docs/#installation-install-kyma-on-a-cluster) to install kyma in kubernetes cluster.

<!-->
finally follow the [install kyma in gardener](https://jam4.sapjam.com/blogs/show/YZm1zvh0pdnZua6fyT8LOT) and [another link](https://cxwiki.sap.com/pages/viewpage.action?spaceKey=ps&title=Kyma+on+Gardener) to start the installation. 
-->

### prerequisites

- kubernetes cluster preparation: choose version : <=1.19 >=1.16 ===> 1.18.17
- minimun node number: 2
- kyma version decision: latest(1.21)

If the version is not the same as expected, below error shall showes itself:

```txt
Unable to create the release: template: kyma/templates/_helpers.tpl:53:4: executing "kyma.checkRequirements" at <fail (printf "Unsupported Kubernetes version used on the cluster. Found '%s' but expected a version within range '%s'." $shootInfo.data.kubernetesVersion .Values.initializer.requires.k8s.version)>: error calling fail: Unsupported Kubernetes version used on the cluster. Found '1.20.5' but expected a version within range '<=1.19 >=1.16'.
```

### install the kyma-cli

```sh
## install the kyma-cli
# https://github.com/kyma-project/cli
brew install kyma-cli # this will install the latest kyma version
```

### install the kyma-release

```sh
# kyma version: 1.20.0
# https://github.com/kyma-project/kyma/releases/tag/1.20.0
# https://kyma-project.io/docs/1.20/root/kyma#installation-install-kyma-on-a-cluster

# follow the link: https://kyma-project.io/docs/1.20/root/kyma/#installation-install-kyma-on-a-cluster-choose-the-release-to-install

export KYMA_VERSION=1.20.0

kyma install -s $KYMA_VERSION

# kyma will install many components in the cluster
```

### install the kyma-release on aws - 1.20

- k8s cluster based on gardener, version 1.20.5
- secret: trial-secretbingding-aws
- kyma version: 

[full scripts](https://github.com/kyma-project/cli/blob/main/docs/gen-docs/kyma_provision_gardener_aws.md)

```sh
kyma install

# follow the link https://kyma-project.io/docs/1.21/root/kyma#installation-overview to see all the components

```

```error

Events:
  Type     Reason            Age   From               Message
  ----     ------            ----  ----               -------
  Warning  FailedScheduling  23m   default-scheduler  0/2 nodes are available: 2 Insufficient cpu.
  Warning  FailedScheduling  23m   default-scheduler  0/2 nodes are available: 2 Insufficient cpu.
```


## started

follow the [kyma tutorial](https://kyma-project.io/docs/root/getting-started/) to do the first play.

目的：

- 创建一个微型服务，对外暴露http endpoints同时，接收外部应用产生的events(外部应用产生)
- 该微服务既可以使用本地存储，也可以使用外部存储类似redis
- 通过service catalog对该微服务使用的redis扩容
- 连接一个外部应用到kyma作为addon，同时使用该外部应用来向微服务发送事件
- 在外部应用中，创建一个函数，处理逻辑与该微服务相似



## tutorial

https://kyma-project.io/docs/components/serverless

[kyma project in github](https://github.com/kyma-project)

[kyma example in github](https://github.com/kyma-project/examples)

[kyma handson](https://blogs.sap.com/2020/06/22/kyma-hands-on-part-1/)

[all components of kyma](https://kyma-project.io/docs/1.21/root/kyma#installation-overview )
