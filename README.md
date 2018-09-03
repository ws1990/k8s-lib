# k8s依赖的docker镜像
## 概述
 每次安装k8s集群时，镜像都是一个问题，为了避免每次都要去各种找镜像，干脆不如自己打包生成镜像。

## 操作步骤
1. 修改Dockerfile的版本
2. 打标签
3. 登录docker hub并生成镜像

## 直接从Docker Hub获取镜像
```shell
images=(etcd-amd64:3.2.18 kube-apiserver-amd64:v1.11.2 kube-controller-manager-amd64:v1.11.2 kube-scheduler-amd64:v1.11.2 kube-proxy-amd64:v1.11.2 pause:3.1 coredns:1.1.3)
for imageName in ${images[@]} ; do
  if [ "`docker images | grep ${imageName%:*}`" == "" ];then
    docker pull ws1990/$imageName
    docker tag ws1990/$imageName k8s.gcr.io/$imageName
    docker rmi ws1990/$imageName
  fi
done
```

## 直接从阿里云获取镜像
```shell
images=(etcd-amd64:3.2.18 kube-apiserver-amd64:v1.11.2 kube-controller-manager-amd64:v1.11.2 kube-scheduler-amd64:v1.11.2 kube-proxy-amd64:v1.11.2 pause:3.1 coredns:1.1.3)
for imageName in ${images[@]} ; do
  if [ "`docker images | grep ${imageName%:*}`" == "" ];then
    docker pull registry.cn-hangzhou.aliyuncs.com/ws_k8s/$imageName
    docker tag registry.cn-hangzhou.aliyuncs.com/ws_k8s/$imageName k8s.gcr.io/$imageName
    docker rmi registry.cn-hangzhou.aliyuncs.com/ws_k8s/$imageName
  fi
done
```

## 参考
[国内获取k8s镜像](https://blog.csdn.net/sjyu_ustc/article/details/79990858)
